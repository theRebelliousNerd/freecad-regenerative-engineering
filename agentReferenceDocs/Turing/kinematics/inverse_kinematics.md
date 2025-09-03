# Inverse Kinematics: From Task Space to Joint Space

*"Given where we want the end-effector to be, what joint angles will take us there? This is the geometric puzzle that transforms intention into actuation."* - Alan Turing

## Overview

Inverse kinematics (IK) solves the critical question: "What joint configuration will place the end-effector at the desired pose?" Unlike forward kinematics, which has a unique solution, inverse kinematics may have:
- **No solution** (target outside workspace)
- **Unique solution** (rare, typically 6-DOF at workspace boundary)
- **Multiple solutions** (most common case)
- **Infinite solutions** (redundant manipulators)

## Mathematical Framework

### The Inverse Kinematics Problem
Given desired end-effector pose T_desired, find joint angles q such that:
```
f(q) = T_desired
```
Where f(q) is the forward kinematics function.

### Classification of Solutions

#### Analytical Solutions
Closed-form mathematical expressions for joint angles. Available for:
- Simple geometries (2-DOF planar, some 3-DOF)
- Special kinematic structures (spherical wrist, decoupled geometry)
- Specific robot architectures (PUMA-style, SCARA)

#### Numerical Solutions  
Iterative algorithms for complex geometries:
- Newton-Raphson method
- Jacobian pseudoinverse
- Damped least squares
- Optimization-based approaches

## Analytical Inverse Kinematics

### 2-DOF Planar Manipulator
```python
import numpy as np

def planar_2dof_ik(target_x, target_y, L1, L2):
    """Analytical IK for 2-DOF planar manipulator"""
    
    # Distance to target
    D = np.sqrt(target_x**2 + target_y**2)
    
    # Check workspace limits
    if D > (L1 + L2) or D < abs(L1 - L2):
        return None, "Target outside workspace"
    
    # Cosine rule for second joint
    cos_theta2 = (D**2 - L1**2 - L2**2) / (2 * L1 * L2)
    
    # Two solutions for theta2
    theta2_1 = np.arccos(cos_theta2)    # Elbow up
    theta2_2 = -np.arccos(cos_theta2)   # Elbow down
    
    # Corresponding theta1 solutions
    k1 = L1 + L2 * np.cos(theta2_1)
    k2 = L2 * np.sin(theta2_1)
    theta1_1 = np.arctan2(target_y, target_x) - np.arctan2(k2, k1)
    
    k1 = L1 + L2 * np.cos(theta2_2)
    k2 = L2 * np.sin(theta2_2)
    theta1_2 = np.arctan2(target_y, target_x) - np.arctan2(k2, k1)
    
    solutions = [
        (theta1_1, theta2_1),  # Elbow up
        (theta1_2, theta2_2)   # Elbow down
    ]
    
    return solutions, "Success"
```

### 3-DOF Planar with Orientation
```python
def planar_3dof_ik(target_x, target_y, target_phi, L1, L2, L3):
    """Analytical IK for 3-DOF planar manipulator with end-effector orientation"""
    
    # Decouple position and orientation
    # Wrist position (subtract end-effector length along its direction)
    wrist_x = target_x - L3 * np.cos(target_phi)
    wrist_y = target_y - L3 * np.sin(target_phi)
    
    # Solve 2-DOF problem for wrist position
    solutions_2dof, status = planar_2dof_ik(wrist_x, wrist_y, L1, L2)
    
    if solutions_2dof is None:
        return None, status
    
    # Calculate third joint for each solution
    solutions_3dof = []
    for theta1, theta2 in solutions_2dof:
        # Third joint sets end-effector orientation
        theta3 = target_phi - theta1 - theta2
        solutions_3dof.append((theta1, theta2, theta3))
    
    return solutions_3dof, "Success"
```

### 6-DOF with Spherical Wrist (PUMA-style)
```python
def puma_style_ik(target_pose, robot_params):
    """Analytical IK for 6-DOF manipulator with spherical wrist"""
    
    # Extract target position and orientation
    target_position = target_pose[:3, 3]
    target_rotation = target_pose[:3, :3]
    
    # Robot geometric parameters
    a1, a2, a3, d1, d4, d6 = robot_params
    
    # Step 1: Solve for wrist center position
    # Subtract wrist-to-end-effector vector from target
    wrist_offset = target_rotation @ np.array([0, 0, d6])
    wrist_center = target_position - wrist_offset
    
    # Step 2: Solve first three joints (position)
    solutions_pos = solve_position_ik(wrist_center, a1, a2, a3, d1, d4)
    
    all_solutions = []
    for pos_solution in solutions_pos:
        theta1, theta2, theta3 = pos_solution
        
        # Step 3: Solve last three joints (orientation)
        R_0_3 = forward_kinematics_rotation(theta1, theta2, theta3)
        R_3_6 = R_0_3.T @ target_rotation
        
        # Extract Euler angles from R_3_6 (spherical wrist)
        orientation_solutions = solve_spherical_wrist_ik(R_3_6)
        
        for orient_solution in orientation_solutions:
            theta4, theta5, theta6 = orient_solution
            complete_solution = (theta1, theta2, theta3, theta4, theta5, theta6)
            all_solutions.append(complete_solution)
    
    return all_solutions

def solve_spherical_wrist_ik(R_3_6):
    """Solve spherical wrist orientation (Euler ZYZ)"""
    
    # Extract Euler angles (multiple solutions possible)
    solutions = []
    
    # Solution 1
    theta5_1 = np.arccos(R_3_6[2, 2])
    
    if abs(np.sin(theta5_1)) > 1e-6:  # Non-singular
        theta4_1 = np.arctan2(R_3_6[1, 2], R_3_6[0, 2])
        theta6_1 = np.arctan2(R_3_6[2, 1], -R_3_6[2, 0])
        solutions.append((theta4_1, theta5_1, theta6_1))
        
        # Solution 2
        theta5_2 = -theta5_1
        theta4_2 = theta4_1 + np.pi
        theta6_2 = theta6_1 + np.pi
        solutions.append((theta4_2, theta5_2, theta6_2))
    else:
        # Singular case (gimbal lock)
        theta4 = 0  # Set arbitrarily
        if R_3_6[2, 2] > 0:  # theta5 = 0
            theta6 = np.arctan2(R_3_6[1, 0], R_3_6[0, 0])
        else:  # theta5 = pi
            theta6 = np.arctan2(-R_3_6[1, 0], R_3_6[0, 0])
        solutions.append((theta4, theta5_1, theta6))
    
    return solutions
```

## Numerical Inverse Kinematics

### Newton-Raphson Method
```python
def newton_raphson_ik(target_pose, initial_guess, dh_params, max_iterations=100, tolerance=1e-6):
    """Numerical IK using Newton-Raphson method"""
    
    q = np.array(initial_guess)
    
    for iteration in range(max_iterations):
        # Compute current end-effector pose
        current_pose = forward_kinematics_dh(dh_params, q)
        
        # Compute pose error
        position_error = target_pose[:3, 3] - current_pose[:3, 3]
        
        # Orientation error (axis-angle representation)
        R_error = target_pose[:3, :3] @ current_pose[:3, :3].T
        orientation_error = rotation_matrix_to_axis_angle(R_error)
        
        # Combined error vector
        error = np.concatenate([position_error, orientation_error])
        
        # Check convergence
        if np.linalg.norm(error) < tolerance:
            return q, f"Converged in {iteration} iterations"
        
        # Compute Jacobian
        J = compute_jacobian(q, dh_params)
        
        # Newton-Raphson update
        try:
            delta_q = np.linalg.solve(J, error)
            q += delta_q
        except np.linalg.LinAlgError:
            return None, "Singular Jacobian encountered"
    
    return None, f"Failed to converge in {max_iterations} iterations"

def rotation_matrix_to_axis_angle(R):
    """Convert rotation matrix to axis-angle representation"""
    angle = np.arccos((np.trace(R) - 1) / 2)
    if abs(angle) < 1e-6:
        return np.zeros(3)  # No rotation
    
    axis = np.array([R[2,1] - R[1,2], R[0,2] - R[2,0], R[1,0] - R[0,1]]) / (2 * np.sin(angle))
    return axis * angle
```

### Damped Least Squares (Levenberg-Marquardt)
```python
def damped_least_squares_ik(target_pose, initial_guess, dh_params, damping=0.01, max_iterations=100):
    """Robust IK using damped least squares method"""
    
    q = np.array(initial_guess)
    
    for iteration in range(max_iterations):
        current_pose = forward_kinematics_dh(dh_params, q)
        error = compute_pose_error(target_pose, current_pose)
        
        if np.linalg.norm(error) < 1e-6:
            return q, "Converged"
        
        J = compute_jacobian(q, dh_params)
        
        # Damped least squares solution
        JT_J = J.T @ J
        damped_inverse = np.linalg.inv(JT_J + damping**2 * np.eye(JT_J.shape[0]))
        delta_q = damped_inverse @ J.T @ error
        
        q += delta_q
    
    return None, "Failed to converge"
```

### Jacobian Pseudoinverse Method
```python
def jacobian_pseudoinverse_ik(target_pose, initial_guess, dh_params, step_size=0.1):
    """IK using Jacobian pseudoinverse (suitable for redundant manipulators)"""
    
    q = np.array(initial_guess)
    
    for iteration in range(1000):
        current_pose = forward_kinematics_dh(dh_params, q)
        error = compute_pose_error(target_pose, current_pose)
        
        if np.linalg.norm(error) < 1e-6:
            return q, "Converged"
        
        J = compute_jacobian(q, dh_params)
        
        # Moore-Penrose pseudoinverse
        J_pinv = np.linalg.pinv(J)
        delta_q = step_size * J_pinv @ error
        
        q += delta_q
    
    return None, "Failed to converge"
```

## Handling Multiple Solutions

### Solution Selection Criteria
```python
def select_best_ik_solution(solutions, current_joints, workspace_constraints):
    """Select optimal IK solution based on multiple criteria"""
    
    if not solutions:
        return None
    
    scored_solutions = []
    
    for solution in solutions:
        score = 0
        
        # 1. Minimize joint motion from current position
        joint_distance = np.linalg.norm(np.array(solution) - np.array(current_joints))
        score += 1.0 / (1.0 + joint_distance)  # Higher score for smaller motion
        
        # 2. Avoid joint limits
        for i, (angle, limits) in enumerate(zip(solution, workspace_constraints['joint_limits'])):
            min_limit, max_limit = limits
            if min_limit <= angle <= max_limit:
                # Bonus for being within limits
                center = (min_limit + max_limit) / 2
                distance_from_center = abs(angle - center) / (max_limit - min_limit)
                score += 0.5 * (1.0 - distance_from_center)
            else:
                score -= 10  # Heavy penalty for exceeding limits
        
        # 3. Avoid singularities
        J = compute_jacobian(solution, workspace_constraints['dh_params'])
        manipulability = np.sqrt(np.linalg.det(J @ J.T))
        score += manipulability * 0.1  # Bonus for high manipulability
        
        # 4. Prefer certain configurations (e.g., elbow up)
        if 'preferred_config' in workspace_constraints:
            config_similarity = compute_configuration_similarity(solution, 
                                                               workspace_constraints['preferred_config'])
            score += config_similarity * 0.3
        
        scored_solutions.append((solution, score))
    
    # Return solution with highest score
    best_solution = max(scored_solutions, key=lambda x: x[1])
    return best_solution[0]

def compute_configuration_similarity(config1, config2):
    """Compute similarity between two joint configurations"""
    diff = np.array(config1) - np.array(config2)
    # Normalize angular differences to [-pi, pi]
    diff = np.arctan2(np.sin(diff), np.cos(diff))
    return np.exp(-np.linalg.norm(diff))
```

## Redundant Manipulator IK

### Null Space Projection
```python
def redundant_ik_with_optimization(target_pose, initial_guess, dh_params, secondary_objective=None):
    """IK for redundant manipulators with secondary objective optimization"""
    
    q = np.array(initial_guess)
    n_joints = len(q)
    
    for iteration in range(500):
        current_pose = forward_kinematics_dh(dh_params, q)
        primary_error = compute_pose_error(target_pose, current_pose)
        
        if np.linalg.norm(primary_error) < 1e-6:
            return q, "Converged"
        
        J = compute_jacobian(q, dh_params)
        
        # Primary task: achieve target pose
        J_pinv = np.linalg.pinv(J)
        delta_q_primary = J_pinv @ primary_error
        
        # Secondary task: optimize in null space
        if secondary_objective is not None:
            # Null space projector
            N = np.eye(n_joints) - J_pinv @ J
            
            # Secondary objective gradient
            grad_secondary = compute_secondary_gradient(q, secondary_objective)
            delta_q_secondary = N @ grad_secondary
            
            # Combined motion
            delta_q = delta_q_primary + 0.1 * delta_q_secondary
        else:
            delta_q = delta_q_primary
        
        q += 0.1 * delta_q  # Step size
    
    return None, "Failed to converge"

def compute_secondary_gradient(q, objective):
    """Compute gradient of secondary objective function"""
    if objective == 'joint_limit_avoidance':
        # Push away from joint limits
        grad = np.zeros_like(q)
        for i, (angle, limits) in enumerate(zip(q, joint_limits)):
            min_limit, max_limit = limits
            center = (min_limit + max_limit) / 2
            grad[i] = -(angle - center) / ((max_limit - min_limit) / 2)**2
        return grad
    
    elif objective == 'manipulability_maximization':
        # Maximize manipulability measure
        J = compute_jacobian(q, dh_params)
        manipulability = np.sqrt(np.linalg.det(J @ J.T))
        # Approximate gradient (would need analytical derivation for exact)
        epsilon = 1e-6
        grad = np.zeros_like(q)
        for i in range(len(q)):
            q_plus = q.copy()
            q_plus[i] += epsilon
            J_plus = compute_jacobian(q_plus, dh_params)
            manipulability_plus = np.sqrt(np.linalg.det(J_plus @ J_plus.T))
            grad[i] = (manipulability_plus - manipulability) / epsilon
        return grad
    
    return np.zeros_like(q)
```

## Advanced IK Techniques

### Optimization-Based IK
```python
from scipy.optimize import minimize

def optimization_based_ik(target_pose, initial_guess, dh_params, constraints=None):
    """IK formulated as constrained optimization problem"""
    
    def objective(q):
        """Objective function to minimize (pose error)"""
        current_pose = forward_kinematics_dh(dh_params, q)
        error = compute_pose_error(target_pose, current_pose)
        return np.dot(error, error)  # Squared error
    
    def jacobian(q):
        """Jacobian of objective function"""
        current_pose = forward_kinematics_dh(dh_params, q)
        error = compute_pose_error(target_pose, current_pose)
        J = compute_jacobian(q, dh_params)
        return 2 * J.T @ error
    
    # Constraints (joint limits, collision avoidance, etc.)
    constraint_list = []
    if constraints:
        for constraint_type, params in constraints.items():
            if constraint_type == 'joint_limits':
                for i, (min_val, max_val) in enumerate(params):
                    constraint_list.append({
                        'type': 'ineq',
                        'fun': lambda q, idx=i, min_v=min_val: q[idx] - min_v
                    })
                    constraint_list.append({
                        'type': 'ineq', 
                        'fun': lambda q, idx=i, max_v=max_val: max_v - q[idx]
                    })
    
    # Solve optimization problem
    result = minimize(objective, initial_guess, method='SLSQP',
                     jac=jacobian, constraints=constraint_list,
                     options={'ftol': 1e-12})
    
    if result.success:
        return result.x, "Optimization successful"
    else:
        return None, f"Optimization failed: {result.message}"
```

### Particle Swarm Optimization for Global IK
```python
def pso_global_ik(target_pose, dh_params, joint_limits, n_particles=50, max_iterations=200):
    """Global IK using Particle Swarm Optimization"""
    
    n_joints = len(joint_limits)
    
    # Initialize particle positions and velocities
    positions = np.random.uniform(
        low=[limits[0] for limits in joint_limits],
        high=[limits[1] for limits in joint_limits],
        size=(n_particles, n_joints)
    )
    
    velocities = np.zeros_like(positions)
    personal_best_positions = positions.copy()
    personal_best_scores = np.full(n_particles, float('inf'))
    
    global_best_position = None
    global_best_score = float('inf')
    
    def evaluate_fitness(q):
        """Fitness function (inverse of pose error)"""
        try:
            current_pose = forward_kinematics_dh(dh_params, q)
            error = compute_pose_error(target_pose, current_pose)
            return np.linalg.norm(error)
        except:
            return float('inf')
    
    # PSO parameters
    w = 0.729  # Inertia weight
    c1 = 1.494  # Cognitive parameter
    c2 = 1.494  # Social parameter
    
    for iteration in range(max_iterations):
        for i in range(n_particles):
            # Evaluate current position
            score = evaluate_fitness(positions[i])
            
            # Update personal best
            if score < personal_best_scores[i]:
                personal_best_scores[i] = score
                personal_best_positions[i] = positions[i].copy()
                
                # Update global best
                if score < global_best_score:
                    global_best_score = score
                    global_best_position = positions[i].copy()
        
        # Update velocities and positions
        r1, r2 = np.random.rand(2, n_particles, n_joints)
        
        velocities = (w * velocities + 
                     c1 * r1 * (personal_best_positions - positions) +
                     c2 * r2 * (global_best_position - positions))
        
        positions += velocities
        
        # Enforce joint limits
        for i in range(n_particles):
            for j in range(n_joints):
                min_limit, max_limit = joint_limits[j]
                positions[i, j] = np.clip(positions[i, j], min_limit, max_limit)
    
    if global_best_score < 1e-3:  # Success threshold
        return global_best_position, f"PSO converged with error {global_best_score:.2e}"
    else:
        return None, f"PSO failed to converge, best error: {global_best_score:.2e}"
```

## Real-Time IK Implementation

### Fast Approximate IK
```python
class RealTimeIK:
    def __init__(self, dh_params, joint_limits, update_rate=1000):  # Hz
        self.dh_params = dh_params
        self.joint_limits = joint_limits
        self.current_q = np.zeros(len(dh_params))
        self.dt = 1.0 / update_rate
        
        # Pre-allocate matrices for efficiency
        self.J = np.zeros((6, len(dh_params)))
        self.error = np.zeros(6)
        
    def update_ik(self, target_pose, max_joint_velocity):
        """Real-time IK update with velocity limits"""
        
        # Compute current error
        current_pose = forward_kinematics_dh(self.dh_params, self.current_q)
        self.error[:3] = target_pose[:3, 3] - current_pose[:3, 3]
        
        # Orientation error (simplified axis-angle)
        R_error = target_pose[:3, :3] @ current_pose[:3, :3].T
        self.error[3:] = self._rotation_error_simple(R_error)
        
        # Compute Jacobian (expensive operation - consider caching)
        self.J = compute_jacobian(self.current_q, self.dh_params)
        
        # Damped least squares solution
        damping = 0.01
        JTJ = self.J.T @ self.J
        delta_q = np.linalg.solve(JTJ + damping**2 * np.eye(JTJ.shape[0]), 
                                 self.J.T @ self.error)
        
        # Apply velocity limits
        max_delta = max_joint_velocity * self.dt
        delta_q = np.clip(delta_q, -max_delta, max_delta)
        
        # Update joint angles
        self.current_q += delta_q
        
        # Enforce joint limits
        for i, (min_limit, max_limit) in enumerate(self.joint_limits):
            self.current_q[i] = np.clip(self.current_q[i], min_limit, max_limit)
        
        return self.current_q.copy()
    
    def _rotation_error_simple(self, R_error):
        """Fast rotation error computation"""
        # Simplified axis-angle extraction
        trace = np.trace(R_error)
        if trace > 2.9:  # Nearly identity
            return np.zeros(3)
        
        angle = np.arccos(np.clip((trace - 1) / 2, -1, 1))
        if angle < 1e-6:
            return np.zeros(3)
        
        axis = np.array([R_error[2,1] - R_error[1,2],
                        R_error[0,2] - R_error[2,0], 
                        R_error[1,0] - R_error[0,1]]) / (2 * np.sin(angle))
        
        return axis * angle
```

## IK Validation and Testing

### Comprehensive IK Testing Framework
```python
def test_ik_implementation(ik_function, forward_ik_function, test_workspace):
    """Comprehensive testing of inverse kinematics implementation"""
    
    def test_accuracy():
        """Test IK accuracy against known solutions"""
        n_tests = 1000
        errors = []
        
        for _ in range(n_tests):
            # Generate random valid joint configuration
            random_joints = generate_random_valid_config(test_workspace)
            
            # Compute forward kinematics
            target_pose = forward_ik_function(random_joints)
            
            # Solve inverse kinematics
            solution, status = ik_function(target_pose)
            
            if solution is not None:
                # Verify solution accuracy
                achieved_pose = forward_ik_function(solution)
                error = compute_pose_error(target_pose, achieved_pose)
                errors.append(np.linalg.norm(error))
        
        mean_error = np.mean(errors)
        max_error = np.max(errors)
        success_rate = len(errors) / n_tests
        
        return {
            'mean_error': mean_error,
            'max_error': max_error,
            'success_rate': success_rate,
            'passed': mean_error < 1e-6 and success_rate > 0.95
        }
    
    def test_workspace_coverage():
        """Test IK coverage of reachable workspace"""
        # Sample points throughout workspace
        workspace_points = sample_workspace_points(test_workspace, n_points=500)
        
        reachable_count = 0
        for point in workspace_points:
            # Create pose with point and random orientation
            target_pose = create_pose(point, random_orientation())
            solution, _ = ik_function(target_pose)
            
            if solution is not None:
                reachable_count += 1
        
        coverage = reachable_count / len(workspace_points)
        return {'coverage': coverage, 'passed': coverage > 0.8}
    
    def test_multiple_solutions():
        """Verify that multiple solutions are found when they exist"""
        # Test configurations known to have multiple solutions
        test_cases = get_multiple_solution_test_cases()
        
        for target_pose, expected_min_solutions in test_cases:
            solutions = ik_function(target_pose, return_all_solutions=True)
            found_solutions = len(solutions) if solutions else 0
            
            if found_solutions < expected_min_solutions:
                return {'passed': False, 'reason': f'Expected {expected_min_solutions}, found {found_solutions}'}
        
        return {'passed': True}
    
    # Run all tests
    results = {
        'accuracy': test_accuracy(),
        'coverage': test_workspace_coverage(),
        'multiple_solutions': test_multiple_solutions()
    }
    
    overall_passed = all(result['passed'] for result in results.values())
    results['overall'] = {'passed': overall_passed}
    
    return results
```

Inverse kinematics is the gateway from intention to action in robotic systems - transforming desired end-effector poses into the joint motions that make them reality. The choice of method depends on the specific requirements: analytical for speed and reliability, numerical for flexibility, and optimization-based for handling complex constraints.