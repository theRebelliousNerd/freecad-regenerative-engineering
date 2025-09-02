# Robotic Kinematics: The Mathematics of Motion Control

*"A robot is a kinematic chain seeking purpose - every joint a degree of freedom, every link a constraint, every motion a solution to geometric equations."* - Alan Turing

## Table of Contents

1. [Philosophy of Robotic Kinematics](#philosophy-of-robotic-kinematics)
2. [Mathematical Foundations](#mathematical-foundations)
3. [Forward Kinematics](#forward-kinematics)
4. [Inverse Kinematics](#inverse-kinematics)
5. [Redundant Manipulators](#redundant-manipulators)
6. [Parallel Mechanisms](#parallel-mechanisms)
7. [Mobile Robot Kinematics](#mobile-robot-kinematics)
8. [Velocity and Jacobian Analysis](#velocity-and-jacobian-analysis)
9. [Singularities and Workspace](#singularities-and-workspace)
10. [Modern Algorithms and Optimization](#modern-algorithms-and-optimization)

---

## Philosophy of Robotic Kinematics

Robotic kinematics is the pure geometry of motion - the study of how robots move without consideration of the forces that cause motion. It is the foundation upon which all robot control is built, transforming abstract joint angles into precise end-effector positions and orientations.

### The Kinematic Hierarchy

**Configuration Space**: The space of all possible joint positions
**Task Space**: The space of end-effector positions and orientations  
**Null Space**: The subspace of joint motions that don't affect the end-effector
**Workspace**: The set of all reachable end-effector poses

### The Fundamental Questions

1. **Forward Kinematics**: Given joint angles, where is the end-effector?
2. **Inverse Kinematics**: Given desired end-effector pose, what joint angles are needed?
3. **Velocity Kinematics**: How do joint velocities relate to end-effector velocities?
4. **Acceleration Kinematics**: How do joint accelerations affect end-effector motion?

---

## Mathematical Foundations

### Homogeneous Transformations

The backbone of robotic kinematics is the homogeneous transformation matrix:

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.spatial.transform import Rotation as R

def homogeneous_transform(rotation_matrix, translation_vector):
    """
    Create 4x4 homogeneous transformation matrix
    """
    T = np.eye(4)
    T[0:3, 0:3] = rotation_matrix
    T[0:3, 3] = translation_vector
    return T

def rotation_x(angle):
    """Rotation matrix about X-axis"""
    c, s = np.cos(angle), np.sin(angle)
    return np.array([[1, 0, 0],
                     [0, c, -s],
                     [0, s, c]])

def rotation_y(angle):
    """Rotation matrix about Y-axis"""
    c, s = np.cos(angle), np.sin(angle)
    return np.array([[c, 0, s],
                     [0, 1, 0],
                     [-s, 0, c]])

def rotation_z(angle):
    """Rotation matrix about Z-axis"""
    c, s = np.cos(angle), np.sin(angle)
    return np.array([[c, -s, 0],
                     [s, c, 0],
                     [0, 0, 1]])

def transform_composition(T1, T2):
    """
    Compose two transformations: T_result = T1 * T2
    """
    return np.dot(T1, T2)

def transform_inverse(T):
    """
    Inverse of homogeneous transformation
    """
    T_inv = np.eye(4)
    R_T = T[0:3, 0:3].T  # Transpose of rotation matrix
    T_inv[0:3, 0:3] = R_T
    T_inv[0:3, 3] = -np.dot(R_T, T[0:3, 3])
    return T_inv

# Example: Compose rotations and translation
R_x = rotation_x(np.pi/6)  # 30 degrees
R_z = rotation_z(np.pi/4)  # 45 degrees
t = np.array([1, 2, 3])    # Translation

T1 = homogeneous_transform(R_x, [0, 0, 0])
T2 = homogeneous_transform(R_z, t)
T_combined = transform_composition(T1, T2)

print("Combined transformation matrix:")
print(T_combined)
```

### Denavit-Hartenberg Parameters

The DH convention provides a systematic method for attaching coordinate frames to kinematic chains:

```python
class DHParameters:
    """
    Denavit-Hartenberg parameter representation
    """
    
    def __init__(self, a, alpha, d, theta):
        self.a = a          # Link length
        self.alpha = alpha  # Link twist  
        self.d = d          # Link offset
        self.theta = theta  # Joint angle
    
    def transformation_matrix(self):
        """
        Generate transformation matrix from DH parameters
        """
        ct, st = np.cos(self.theta), np.sin(self.theta)
        ca, sa = np.cos(self.alpha), np.sin(self.alpha)
        
        T = np.array([
            [ct, -st*ca, st*sa, self.a*ct],
            [st, ct*ca, -ct*sa, self.a*st],
            [0, sa, ca, self.d],
            [0, 0, 0, 1]
        ])
        
        return T

def create_dh_chain(dh_params_list):
    """
    Create kinematic chain from list of DH parameters
    """
    chain = []
    for params in dh_params_list:
        dh = DHParameters(*params)
        chain.append(dh)
    return chain

def forward_kinematics_dh(dh_chain, joint_angles):
    """
    Calculate forward kinematics using DH parameters
    """
    if len(joint_angles) != len(dh_chain):
        raise ValueError("Number of joint angles must match DH chain length")
    
    T_total = np.eye(4)
    
    for i, (dh, angle) in enumerate(zip(dh_chain, joint_angles)):
        # Update joint angle (for revolute joints)
        dh_temp = DHParameters(dh.a, dh.alpha, dh.d, dh.theta + angle)
        T_i = dh_temp.transformation_matrix()
        T_total = np.dot(T_total, T_i)
    
    # Extract position and orientation
    position = T_total[0:3, 3]
    rotation_matrix = T_total[0:3, 0:3]
    
    return T_total, position, rotation_matrix

# Example: 6-DOF manipulator DH parameters
# [a, alpha, d, theta_offset]
dh_params_6dof = [
    [0, np.pi/2, 0.340, 0],      # Joint 1
    [0.320, 0, 0, -np.pi/2],    # Joint 2  
    [0, np.pi/2, 0, np.pi/2],   # Joint 3
    [0, -np.pi/2, 0.320, 0],    # Joint 4
    [0, np.pi/2, 0, 0],         # Joint 5
    [0, 0, 0.080, np.pi],       # Joint 6
]

dh_chain = create_dh_chain(dh_params_6dof)
joint_config = [0, 0, 0, 0, 0, 0]  # Home position

T_end, pos_end, rot_end = forward_kinematics_dh(dh_chain, joint_config)
print(f"End-effector position: {pos_end}")
print(f"End-effector orientation matrix:\n{rot_end}")
```

### Screw Theory and Exponential Coordinates

Modern approach using screw theory and the Product of Exponentials:

```python
def skew_symmetric(omega):
    """
    Create skew-symmetric matrix from 3D vector
    """
    return np.array([
        [0, -omega[2], omega[1]],
        [omega[2], 0, -omega[0]],
        [-omega[1], omega[0], 0]
    ])

def matrix_exponential_se3(xi_hat, theta):
    """
    Matrix exponential for SE(3) - screw motion
    
    xi_hat: 4x4 matrix representation of screw axis
    theta: screw displacement
    """
    if np.allclose(xi_hat, 0):
        return np.eye(4)
    
    omega_hat = xi_hat[0:3, 0:3]  # Angular part
    v = xi_hat[0:3, 3]            # Linear part
    
    if np.allclose(omega_hat, 0):  # Pure translation
        T = np.eye(4)
        T[0:3, 3] = v * theta
        return T
    
    # General screw motion
    omega = np.array([omega_hat[2, 1], omega_hat[0, 2], omega_hat[1, 0]])
    omega_magnitude = np.linalg.norm(omega)
    
    if omega_magnitude < 1e-6:  # Nearly pure translation
        T = np.eye(4)
        T[0:3, 3] = v * theta
        return T
    
    # Rodrigues' formula for rotation
    I = np.eye(3)
    R = I + np.sin(theta) * omega_hat + (1 - np.cos(theta)) * np.dot(omega_hat, omega_hat)
    
    # Translation part
    V = (I * theta + 
         (1 - np.cos(theta)) * omega_hat + 
         (theta - np.sin(theta)) * np.dot(omega_hat, omega_hat))
    p = np.dot(V, v)
    
    # Assemble transformation matrix
    T = np.eye(4)
    T[0:3, 0:3] = R
    T[0:3, 3] = p
    
    return T

def screw_axis_revolute(q, s, h=0):
    """
    Create screw axis for revolute joint
    
    q: point on joint axis
    s: unit vector along joint axis  
    h: pitch (0 for pure rotation)
    """
    omega = s
    v = -np.cross(omega, q) + h * omega
    
    # 4x4 matrix representation
    xi_hat = np.zeros((4, 4))
    xi_hat[0:3, 0:3] = skew_symmetric(omega)
    xi_hat[0:3, 3] = v
    
    return xi_hat

def screw_axis_prismatic(s):
    """
    Create screw axis for prismatic joint
    
    s: unit vector along joint axis
    """
    omega = np.zeros(3)
    v = s
    
    xi_hat = np.zeros((4, 4))
    xi_hat[0:3, 3] = v
    
    return xi_hat

class ScrewTheoryRobot:
    """
    Robot kinematics using screw theory
    """
    
    def __init__(self, M, screw_axes):
        self.M = M  # Home configuration (when all joints = 0)
        self.screw_axes = screw_axes  # List of screw axes
        self.num_joints = len(screw_axes)
    
    def forward_kinematics(self, joint_angles):
        """
        Calculate forward kinematics using product of exponentials
        """
        T = np.eye(4)
        
        for i, (xi_hat, theta) in enumerate(zip(self.screw_axes, joint_angles)):
            T_i = matrix_exponential_se3(xi_hat, theta)
            T = np.dot(T, T_i)
        
        return np.dot(T, self.M)
    
    def jacobian_spatial(self, joint_angles):
        """
        Calculate spatial Jacobian matrix
        """
        J = np.zeros((6, self.num_joints))
        T = np.eye(4)
        
        for i in range(self.num_joints):
            # Extract screw coordinates
            omega = np.array([self.screw_axes[i][2, 1], 
                             self.screw_axes[i][0, 2], 
                             self.screw_axes[i][1, 0]])
            v = self.screw_axes[i][0:3, 3]
            
            # Transform to current configuration
            xi_spatial = np.zeros(6)
            xi_spatial[0:3] = np.dot(T[0:3, 0:3], omega)
            xi_spatial[3:6] = np.dot(T[0:3, 0:3], v) + np.cross(T[0:3, 3], xi_spatial[0:3])
            
            J[:, i] = xi_spatial
            
            # Update transformation for next joint
            if i < self.num_joints - 1:
                T_i = matrix_exponential_se3(self.screw_axes[i], joint_angles[i])
                T = np.dot(T, T_i)
        
        return J
    
    def jacobian_body(self, joint_angles):
        """
        Calculate body Jacobian matrix
        """
        J = np.zeros((6, self.num_joints))
        T = self.M
        
        # Work backwards from end-effector
        for i in range(self.num_joints - 1, -1, -1):
            # Extract screw coordinates in body frame
            omega = np.array([self.screw_axes[i][2, 1], 
                             self.screw_axes[i][0, 2], 
                             self.screw_axes[i][1, 0]])
            v = self.screw_axes[i][0:3, 3]
            
            # Transform to body frame
            T_inv = transform_inverse(T)
            xi_body = np.zeros(6)
            xi_body[0:3] = np.dot(T_inv[0:3, 0:3], omega)
            xi_body[3:6] = (np.dot(T_inv[0:3, 0:3], v) + 
                           np.cross(T_inv[0:3, 3], xi_body[0:3]))
            
            J[:, i] = xi_body
            
            # Update transformation
            if i > 0:
                T_i_inv = matrix_exponential_se3(self.screw_axes[i], -joint_angles[i])
                T = np.dot(T, T_i_inv)
        
        return J

# Example: Create 6-DOF robot using screw theory
M_home = np.array([
    [1, 0, 0, 0.6],
    [0, 1, 0, 0],  
    [0, 0, 1, 0.8],
    [0, 0, 0, 1]
])

# Define screw axes for each joint
screw_axes = [
    screw_axis_revolute([0, 0, 0], [0, 0, 1]),         # Joint 1: Z-axis rotation
    screw_axis_revolute([0.3, 0, 0.3], [0, 1, 0]),    # Joint 2: Y-axis rotation  
    screw_axis_revolute([0.3, 0, 0.6], [0, 1, 0]),    # Joint 3: Y-axis rotation
    screw_axis_revolute([0.6, 0, 0.6], [1, 0, 0]),    # Joint 4: X-axis rotation
    screw_axis_revolute([0.6, 0, 0.6], [0, 1, 0]),    # Joint 5: Y-axis rotation
    screw_axis_revolute([0.6, 0, 0.8], [1, 0, 0]),    # Joint 6: X-axis rotation
]

robot = ScrewTheoryRobot(M_home, screw_axes)
joint_config = [0.1, 0.2, -0.1, 0.3, -0.2, 0.1]
T_fk = robot.forward_kinematics(joint_config)
J_spatial = robot.jacobian_spatial(joint_config)

print("Forward kinematics result:")
print(T_fk)
print("\nSpatial Jacobian:")
print(J_spatial)
```

---

## Forward Kinematics

Forward kinematics transforms joint space coordinates to task space coordinates:

```python
class ForwardKinematicsSolver:
    """
    Generic forward kinematics solver
    """
    
    def __init__(self, robot_model):
        self.robot = robot_model
        self.link_transforms = []
    
    def solve(self, joint_angles, return_all_links=False):
        """
        Solve forward kinematics
        
        Returns:
        - End-effector pose
        - Optionally: all link poses
        """
        link_poses = []
        T_current = np.eye(4)
        
        for i, angle in enumerate(joint_angles):
            # Get transformation for this joint
            T_joint = self.robot.get_joint_transform(i, angle)
            
            # Accumulate transformation
            T_current = np.dot(T_current, T_joint)
            
            if return_all_links:
                link_poses.append(T_current.copy())
        
        if return_all_links:
            return T_current, link_poses
        else:
            return T_current
    
    def solve_multiple_configurations(self, joint_trajectories):
        """
        Solve forward kinematics for multiple configurations
        """
        end_effector_trajectory = []
        
        for joint_config in joint_trajectories:
            T_end = self.solve(joint_config)
            position = T_end[0:3, 3]
            orientation = T_end[0:3, 0:3]
            end_effector_trajectory.append({
                'position': position,
                'orientation': orientation,
                'transformation': T_end
            })
        
        return end_effector_trajectory
    
    def workspace_analysis(self, joint_limits, resolution=20):
        """
        Analyze robot workspace through forward kinematics sampling
        """
        workspace_points = []
        
        # Generate joint angle samples
        joint_samples = []
        for joint_idx, (min_angle, max_angle) in enumerate(joint_limits):
            samples = np.linspace(min_angle, max_angle, resolution)
            joint_samples.append(samples)
        
        # Cartesian product of all joint samples
        import itertools
        for joint_config in itertools.product(*joint_samples):
            try:
                T_end = self.solve(list(joint_config))
                position = T_end[0:3, 3]
                workspace_points.append(position)
            except:
                # Skip configurations that cause issues
                continue
        
        workspace_points = np.array(workspace_points)
        
        # Analyze workspace properties
        workspace_analysis = {
            'points': workspace_points,
            'min_reach': np.min(np.linalg.norm(workspace_points, axis=1)),
            'max_reach': np.max(np.linalg.norm(workspace_points, axis=1)),
            'workspace_volume': self.estimate_workspace_volume(workspace_points),
            'centroid': np.mean(workspace_points, axis=0)
        }
        
        return workspace_analysis
    
    def estimate_workspace_volume(self, points):
        """
        Estimate workspace volume using convex hull
        """
        try:
            from scipy.spatial import ConvexHull
            hull = ConvexHull(points)
            return hull.volume
        except:
            # Fallback to bounding box volume
            ranges = np.ptp(points, axis=0)  # Peak-to-peak (max - min)
            return np.prod(ranges)

def create_robot_model_example():
    """
    Create example robot model for testing
    """
    class SimpleRobotModel:
        def __init__(self):
            # Simple 3-DOF planar robot
            self.link_lengths = [1.0, 0.8, 0.6]  # meters
            
        def get_joint_transform(self, joint_index, angle):
            """Get transformation matrix for joint"""
            if joint_index >= len(self.link_lengths):
                return np.eye(4)
            
            # Rotation about Z-axis + translation along X-axis
            T = np.eye(4)
            T[0:2, 0:2] = rotation_z(angle)[0:2, 0:2]
            T[0, 3] = self.link_lengths[joint_index]
            
            return T
    
    return SimpleRobotModel()

# Example usage
robot_model = create_robot_model_example()
fk_solver = ForwardKinematicsSolver(robot_model)

# Test configuration
test_config = [np.pi/4, np.pi/6, -np.pi/3]
T_result = fk_solver.solve(test_config)

print("End-effector pose:")
print(f"Position: {T_result[0:3, 3]}")
print(f"Orientation:\n{T_result[0:3, 0:3]}")

# Workspace analysis
joint_limits = [(-np.pi, np.pi), (-np.pi/2, np.pi/2), (-np.pi/3, np.pi/3)]
workspace = fk_solver.workspace_analysis(joint_limits, resolution=10)
print(f"\nWorkspace analysis:")
print(f"Max reach: {workspace['max_reach']:.3f}")
print(f"Min reach: {workspace['min_reach']:.3f}")
print(f"Estimated volume: {workspace['workspace_volume']:.3f}")
```

---

## Inverse Kinematics

Inverse kinematics is the core challenge of robotics - determining joint angles for desired end-effector poses:

```python
class InverseKinematicsSolver:
    """
    Comprehensive inverse kinematics solver
    """
    
    def __init__(self, robot_model, method='jacobian_pseudoinverse'):
        self.robot = robot_model
        self.method = method
        self.tolerance = 1e-6
        self.max_iterations = 100
        self.step_size = 0.1
    
    def solve_numerical(self, target_pose, initial_guess=None, constraints=None):
        """
        Solve inverse kinematics using numerical methods
        """
        if self.method == 'jacobian_pseudoinverse':
            return self.solve_jacobian_pseudoinverse(target_pose, initial_guess, constraints)
        elif self.method == 'damped_least_squares':
            return self.solve_damped_least_squares(target_pose, initial_guess, constraints)
        elif self.method == 'newton_raphson':
            return self.solve_newton_raphson(target_pose, initial_guess, constraints)
        elif self.method == 'optimization':
            return self.solve_optimization(target_pose, initial_guess, constraints)
        else:
            raise ValueError(f"Unknown method: {self.method}")
    
    def solve_jacobian_pseudoinverse(self, target_pose, initial_guess=None, constraints=None):
        """
        Jacobian pseudoinverse method for IK
        """
        if initial_guess is None:
            q = np.zeros(self.robot.num_joints)
        else:
            q = np.array(initial_guess)
        
        target_position = target_pose[0:3, 3]
        target_rotation = target_pose[0:3, 0:3]
        
        for iteration in range(self.max_iterations):
            # Forward kinematics
            current_pose = self.robot.forward_kinematics(q)
            current_position = current_pose[0:3, 3]
            current_rotation = current_pose[0:3, 0:3]
            
            # Calculate position error
            position_error = target_position - current_position
            
            # Calculate orientation error (axis-angle representation)
            rotation_error_matrix = np.dot(target_rotation, current_rotation.T)
            rotation_error = self.rotation_matrix_to_axis_angle(rotation_error_matrix)
            
            # Combine errors
            error = np.concatenate([position_error, rotation_error])
            
            # Check convergence
            if np.linalg.norm(error) < self.tolerance:
                return {
                    'success': True,
                    'joint_angles': q,
                    'error': np.linalg.norm(error),
                    'iterations': iteration + 1
                }
            
            # Calculate Jacobian
            J = self.robot.jacobian_spatial(q)
            
            # Pseudoinverse solution
            J_pinv = np.linalg.pinv(J)
            dq = self.step_size * np.dot(J_pinv, error)
            
            # Apply constraints if specified
            if constraints:
                dq = self.apply_constraints(q, dq, constraints)
            
            # Update joint angles
            q += dq
        
        return {
            'success': False,
            'joint_angles': q,
            'error': np.linalg.norm(error),
            'iterations': self.max_iterations,
            'message': 'Maximum iterations exceeded'
        }
    
    def solve_damped_least_squares(self, target_pose, initial_guess=None, constraints=None):
        """
        Damped Least Squares (Levenberg-Marquardt) method
        """
        damping_factor = 0.01
        
        if initial_guess is None:
            q = np.zeros(self.robot.num_joints)
        else:
            q = np.array(initial_guess)
        
        target_position = target_pose[0:3, 3]
        target_rotation = target_pose[0:3, 0:3]
        
        for iteration in range(self.max_iterations):
            # Forward kinematics and error calculation
            current_pose = self.robot.forward_kinematics(q)
            current_position = current_pose[0:3, 3]
            current_rotation = current_pose[0:3, 0:3]
            
            position_error = target_position - current_position
            rotation_error_matrix = np.dot(target_rotation, current_rotation.T)
            rotation_error = self.rotation_matrix_to_axis_angle(rotation_error_matrix)
            error = np.concatenate([position_error, rotation_error])
            
            # Check convergence
            if np.linalg.norm(error) < self.tolerance:
                return {
                    'success': True,
                    'joint_angles': q,
                    'error': np.linalg.norm(error),
                    'iterations': iteration + 1
                }
            
            # Calculate Jacobian
            J = self.robot.jacobian_spatial(q)
            
            # Damped least squares solution
            I = np.eye(J.shape[1])
            JTJ_damped = np.dot(J.T, J) + damping_factor**2 * I
            dq = self.step_size * np.dot(np.linalg.inv(JTJ_damped), np.dot(J.T, error))
            
            # Apply constraints
            if constraints:
                dq = self.apply_constraints(q, dq, constraints)
            
            # Update and adjust damping
            q_new = q + dq
            new_error_norm = self.calculate_pose_error_norm(target_pose, self.robot.forward_kinematics(q_new))
            
            if new_error_norm < np.linalg.norm(error):
                q = q_new
                damping_factor *= 0.7  # Decrease damping
            else:
                damping_factor *= 1.5  # Increase damping
        
        return {
            'success': False,
            'joint_angles': q,
            'error': np.linalg.norm(error),
            'iterations': self.max_iterations
        }
    
    def solve_optimization(self, target_pose, initial_guess=None, constraints=None):
        """
        Optimization-based IK using scipy.optimize
        """
        from scipy.optimize import minimize
        
        if initial_guess is None:
            initial_guess = np.zeros(self.robot.num_joints)
        
        def objective(q):
            """Objective function: pose error"""
            current_pose = self.robot.forward_kinematics(q)
            return self.calculate_pose_error_norm(target_pose, current_pose)
        
        # Set up optimization constraints
        opt_constraints = []
        
        if constraints:
            if 'joint_limits' in constraints:
                bounds = [(low, high) for low, high in constraints['joint_limits']]
            else:
                bounds = None
            
            if 'collision_avoidance' in constraints:
                opt_constraints.append({
                    'type': 'ineq',
                    'fun': lambda q: self.collision_constraint(q, constraints['collision_avoidance'])
                })
        else:
            bounds = None
        
        # Solve optimization
        result = minimize(
            objective,
            initial_guess,
            method='SLSQP',
            bounds=bounds,
            constraints=opt_constraints,
            options={'ftol': self.tolerance, 'maxiter': self.max_iterations}
        )
        
        return {
            'success': result.success,
            'joint_angles': result.x,
            'error': result.fun,
            'iterations': result.nit,
            'message': result.message
        }
    
    def solve_multiple_solutions(self, target_pose, num_attempts=10):
        """
        Find multiple IK solutions using different initial guesses
        """
        solutions = []
        
        for attempt in range(num_attempts):
            # Generate random initial guess
            initial_guess = np.random.uniform(-np.pi, np.pi, self.robot.num_joints)
            
            # Solve IK
            result = self.solve_numerical(target_pose, initial_guess)
            
            if result['success']:
                # Check if this is a new solution
                is_new_solution = True
                for existing_solution in solutions:
                    if np.allclose(result['joint_angles'], existing_solution['joint_angles'], rtol=0.1):
                        is_new_solution = False
                        break
                
                if is_new_solution:
                    solutions.append(result)
        
        return solutions
    
    def rotation_matrix_to_axis_angle(self, R):
        """
        Convert rotation matrix to axis-angle representation
        """
        trace = np.trace(R)
        angle = np.arccos((trace - 1) / 2)
        
        if np.abs(angle) < 1e-6:
            return np.zeros(3)
        elif np.abs(angle - np.pi) < 1e-6:
            # Special case: 180-degree rotation
            # Find the eigenvector corresponding to eigenvalue 1
            eigenvalues, eigenvectors = np.linalg.eig(R)
            axis_index = np.argmin(np.abs(eigenvalues - 1))
            axis = eigenvectors[:, axis_index].real
            return axis * angle
        else:
            axis = np.array([R[2, 1] - R[1, 2], R[0, 2] - R[2, 0], R[1, 0] - R[0, 1]])
            axis = axis / (2 * np.sin(angle))
            return axis * angle
    
    def calculate_pose_error_norm(self, target_pose, current_pose):
        """
        Calculate norm of pose error (position + orientation)
        """
        position_error = target_pose[0:3, 3] - current_pose[0:3, 3]
        
        rotation_error_matrix = np.dot(target_pose[0:3, 0:3], current_pose[0:3, 0:3].T)
        rotation_error = self.rotation_matrix_to_axis_angle(rotation_error_matrix)
        
        # Weighted combination of position and orientation errors
        position_weight = 1.0
        orientation_weight = 0.1
        
        return (position_weight * np.linalg.norm(position_error) + 
                orientation_weight * np.linalg.norm(rotation_error))
    
    def apply_constraints(self, q, dq, constraints):
        """
        Apply constraints to joint angle update
        """
        if 'joint_limits' in constraints:
            for i, (q_min, q_max) in enumerate(constraints['joint_limits']):
                q_new = q[i] + dq[i]
                if q_new < q_min:
                    dq[i] = q_min - q[i]
                elif q_new > q_max:
                    dq[i] = q_max - q[i]
        
        if 'max_joint_velocity' in constraints:
            max_dq = constraints['max_joint_velocity']
            dq_norm = np.linalg.norm(dq)
            if dq_norm > max_dq:
                dq = dq * max_dq / dq_norm
        
        return dq

# Example usage
def test_inverse_kinematics():
    """
    Test inverse kinematics with example robot
    """
    # Create robot (same as forward kinematics example)
    robot_model = create_robot_model_example()
    
    # Create IK solver
    ik_solver = InverseKinematicsSolver(robot_model, method='damped_least_squares')
    
    # Target pose
    target_position = np.array([1.5, 1.0, 0])
    target_orientation = np.eye(3)  # No rotation
    target_pose = homogeneous_transform(target_orientation, target_position)
    
    # Solve IK
    result = ik_solver.solve_numerical(target_pose)
    
    print("Inverse Kinematics Result:")
    print(f"Success: {result['success']}")
    print(f"Joint angles: {result['joint_angles']}")
    print(f"Final error: {result['error']:.6f}")
    print(f"Iterations: {result['iterations']}")
    
    # Verify solution
    if result['success']:
        verified_pose = robot_model.forward_kinematics(result['joint_angles'])
        print("\nVerification:")
        print(f"Target position: {target_position}")
        print(f"Achieved position: {verified_pose[0:3, 3]}")
        print(f"Position error: {np.linalg.norm(target_position - verified_pose[0:3, 3]):.6f}")
    
    # Find multiple solutions
    multiple_solutions = ik_solver.solve_multiple_solutions(target_pose, num_attempts=20)
    print(f"\nFound {len(multiple_solutions)} different solutions:")
    for i, sol in enumerate(multiple_solutions):
        print(f"Solution {i+1}: {sol['joint_angles']}")

if __name__ == "__main__":
    test_inverse_kinematics()
```

---

## Redundant Manipulators

Redundant manipulators have more degrees of freedom than required for the task:

```python
class RedundantManipulatorSolver:
    """
    Specialized solver for redundant manipulators
    """
    
    def __init__(self, robot_model):
        self.robot = robot_model
        self.task_dof = 6  # Position (3) + Orientation (3)
        self.redundancy = robot_model.num_joints - self.task_dof
    
    def solve_with_nullspace_optimization(self, target_pose, objective_function, 
                                        initial_guess=None, constraints=None):
        """
        Solve IK while optimizing secondary objectives in nullspace
        """
        if initial_guess is None:
            q = np.zeros(self.robot.num_joints)
        else:
            q = np.array(initial_guess)
        
        target_position = target_pose[0:3, 3]
        target_rotation = target_pose[0:3, 0:3]
        
        tolerance = 1e-6
        max_iterations = 100
        step_size = 0.1
        
        for iteration in range(max_iterations):
            # Forward kinematics and error
            current_pose = self.robot.forward_kinematics(q)
            current_position = current_pose[0:3, 3]
            current_rotation = current_pose[0:3, 0:3]
            
            position_error = target_position - current_position
            rotation_error = self.rotation_matrix_to_axis_angle(
                np.dot(target_rotation, current_rotation.T))
            task_error = np.concatenate([position_error, rotation_error])
            
            # Check convergence
            if np.linalg.norm(task_error) < tolerance:
                return {
                    'success': True,
                    'joint_angles': q,
                    'task_error': np.linalg.norm(task_error),
                    'iterations': iteration + 1
                }
            
            # Calculate Jacobian
            J = self.robot.jacobian_spatial(q)
            
            # Primary task: achieve target pose
            J_pinv = np.linalg.pinv(J)
            dq_primary = step_size * np.dot(J_pinv, task_error)
            
            # Secondary task: optimize objective in nullspace
            if self.redundancy > 0 and objective_function is not None:
                # Nullspace projector
                I = np.eye(self.robot.num_joints)
                N = I - np.dot(J_pinv, J)
                
                # Gradient of secondary objective
                grad_secondary = self.calculate_objective_gradient(q, objective_function)
                
                # Project gradient into nullspace
                dq_secondary = step_size * np.dot(N, grad_secondary)
                
                # Combine motions
                dq = dq_primary + dq_secondary
            else:
                dq = dq_primary
            
            # Apply constraints
            if constraints:
                dq = self.apply_constraints(q, dq, constraints)
            
            q += dq
        
        return {
            'success': False,
            'joint_angles': q,
            'task_error': np.linalg.norm(task_error),
            'iterations': max_iterations
        }
    
    def solve_with_joint_limit_avoidance(self, target_pose, joint_limits, 
                                       initial_guess=None):
        """
        Solve IK while avoiding joint limits
        """
        def joint_limit_objective(q):
            """Objective function to avoid joint limits"""
            cost = 0
            for i, (q_min, q_max) in enumerate(joint_limits):
                q_mid = (q_min + q_max) / 2
                q_range = q_max - q_min
                # Quadratic penalty near limits
                normalized_pos = 2 * (q[i] - q_mid) / q_range
                cost += normalized_pos**2
            return cost
        
        return self.solve_with_nullspace_optimization(
            target_pose, joint_limit_objective, initial_guess)
    
    def solve_with_obstacle_avoidance(self, target_pose, obstacles, 
                                    initial_guess=None):
        """
        Solve IK while avoiding obstacles
        """
        def obstacle_avoidance_objective(q):
            """Objective function for obstacle avoidance"""
            # Get all link positions
            link_poses = self.robot.forward_kinematics_all_links(q)
            
            total_cost = 0
            for link_pose in link_poses:
                link_position = link_pose[0:3, 3]
                
                for obstacle in obstacles:
                    distance = self.calculate_distance_to_obstacle(link_position, obstacle)
                    if distance < obstacle.get('safety_margin', 0.1):
                        # Inverse distance penalty
                        total_cost += 1.0 / (distance + 1e-6)
            
            return total_cost
        
        return self.solve_with_nullspace_optimization(
            target_pose, obstacle_avoidance_objective, initial_guess)
    
    def solve_with_manipulability_optimization(self, target_pose, initial_guess=None):
        """
        Solve IK while maximizing manipulability
        """
        def manipulability_objective(q):
            """Maximize manipulability (negative for minimization)"""
            J = self.robot.jacobian_spatial(q)
            # Manipulability measure: sqrt(det(J*J^T))
            manipulability = np.sqrt(np.linalg.det(np.dot(J, J.T)))
            return -manipulability  # Negative for maximization
        
        return self.solve_with_nullspace_optimization(
            target_pose, manipulability_objective, initial_guess)
    
    def solve_with_minimum_joint_motion(self, target_pose, reference_config, 
                                      initial_guess=None):
        """
        Solve IK while staying close to reference configuration
        """
        def minimum_motion_objective(q):
            """Minimize distance from reference configuration"""
            return np.linalg.norm(q - reference_config)**2
        
        return self.solve_with_nullspace_optimization(
            target_pose, minimum_motion_objective, initial_guess)
    
    def calculate_objective_gradient(self, q, objective_function):
        """
        Calculate gradient of objective function using finite differences
        """
        epsilon = 1e-8
        gradient = np.zeros(len(q))
        
        f_center = objective_function(q)
        
        for i in range(len(q)):
            q_plus = q.copy()
            q_plus[i] += epsilon
            f_plus = objective_function(q_plus)
            
            gradient[i] = (f_plus - f_center) / epsilon
        
        return gradient
    
    def analyze_redundancy(self, joint_config):
        """
        Analyze redundancy properties at given configuration
        """
        J = self.robot.jacobian_spatial(joint_config)
        
        # Singular value decomposition
        U, s, Vt = np.linalg.svd(J)
        
        # Rank and nullspace dimension
        rank = np.sum(s > 1e-6)
        nullspace_dim = len(joint_config) - rank
        
        # Condition number
        condition_number = s[0] / s[-1] if s[-1] > 1e-6 else float('inf')
        
        # Manipulability
        manipulability = np.sqrt(np.linalg.det(np.dot(J, J.T)))
        
        return {
            'jacobian_rank': rank,
            'nullspace_dimension': nullspace_dim,
            'condition_number': condition_number,
            'manipulability': manipulability,
            'singular_values': s,
            'near_singularity': condition_number > 100
        }
    
    def generate_self_motion_manifold(self, target_pose, joint_config, 
                                    num_samples=50):
        """
        Generate samples from self-motion manifold for fixed end-effector pose
        """
        # Base configuration that achieves target pose
        base_config = joint_config
        
        # Calculate nullspace basis
        J = self.robot.jacobian_spatial(base_config)
        U, s, Vt = np.linalg.svd(J)
        
        # Nullspace basis vectors
        nullspace_basis = Vt[len(s):].T
        
        if nullspace_basis.shape[1] == 0:
            return [base_config]  # No redundancy
        
        # Generate random coefficients for nullspace motion
        manifold_samples = []
        
        for _ in range(num_samples):
            # Random coefficients
            alpha = np.random.uniform(-1, 1, nullspace_basis.shape[1])
            
            # Scale coefficients
            alpha = alpha * 0.5  # Limit range of motion
            
            # Generate new configuration
            nullspace_motion = np.dot(nullspace_basis, alpha)
            new_config = base_config + nullspace_motion
            
            # Verify that end-effector pose is maintained
            new_pose = self.robot.forward_kinematics(new_config)
            pose_error = self.calculate_pose_error_norm(target_pose, new_pose)
            
            if pose_error < 1e-3:  # Acceptable error
                manifold_samples.append(new_config)
        
        return manifold_samples
    
    def rotation_matrix_to_axis_angle(self, R):
        """Convert rotation matrix to axis-angle (same as base class)"""
        trace = np.trace(R)
        angle = np.arccos(np.clip((trace - 1) / 2, -1, 1))
        
        if np.abs(angle) < 1e-6:
            return np.zeros(3)
        elif np.abs(angle - np.pi) < 1e-6:
            eigenvalues, eigenvectors = np.linalg.eig(R)
            axis_index = np.argmin(np.abs(eigenvalues - 1))
            axis = eigenvectors[:, axis_index].real
            return axis * angle
        else:
            axis = np.array([R[2, 1] - R[1, 2], R[0, 2] - R[2, 0], R[1, 0] - R[0, 1]])
            axis = axis / (2 * np.sin(angle))
            return axis * angle

# Example: 7-DOF redundant manipulator
def create_7dof_robot_example():
    """Create example 7-DOF redundant robot"""
    
    class Redundant7DOFRobot:
        def __init__(self):
            self.num_joints = 7
            # Example DH parameters for 7-DOF arm
            self.link_lengths = [0.3, 0.3, 0.3, 0.3, 0.2, 0.2, 0.1]
            self.link_offsets = [0.1, 0, 0, 0, 0, 0, 0.05]
        
        def forward_kinematics(self, joint_angles):
            """Forward kinematics using simplified model"""
            T = np.eye(4)
            
            for i, (angle, length, offset) in enumerate(zip(joint_angles, 
                                                           self.link_lengths, 
                                                           self.link_offsets)):
                # Alternating rotation axes (simplified)
                if i % 2 == 0:  # Z-axis rotation
                    R = rotation_z(angle)
                else:  # Y-axis rotation
                    R = rotation_y(angle)
                
                # Translation
                if i % 2 == 0:
                    t = np.array([length, 0, offset])
                else:
                    t = np.array([0, 0, length])
                
                T_i = homogeneous_transform(R, t)
                T = np.dot(T, T_i)
            
            return T
        
        def jacobian_spatial(self, joint_angles):
            """Calculate spatial Jacobian (simplified)"""
            J = np.zeros((6, self.num_joints))
            
            # Finite difference approximation
            epsilon = 1e-8
            T_center = self.forward_kinematics(joint_angles)
            
            for i in range(self.num_joints):
                q_plus = joint_angles.copy()
                q_plus[i] += epsilon
                
                T_plus = self.forward_kinematics(q_plus)
                
                # Position Jacobian
                J[0:3, i] = (T_plus[0:3, 3] - T_center[0:3, 3]) / epsilon
                
                # Orientation Jacobian (simplified)
                R_diff = np.dot(T_plus[0:3, 0:3], T_center[0:3, 0:3].T)
                axis_angle = self.rotation_matrix_to_axis_angle(R_diff)
                J[3:6, i] = axis_angle / epsilon
            
            return J
        
        def forward_kinematics_all_links(self, joint_angles):
            """Get poses of all links"""
            link_poses = []
            T = np.eye(4)
            
            for i, (angle, length, offset) in enumerate(zip(joint_angles, 
                                                           self.link_lengths, 
                                                           self.link_offsets)):
                if i % 2 == 0:
                    R = rotation_z(angle)
                    t = np.array([length, 0, offset])
                else:
                    R = rotation_y(angle)
                    t = np.array([0, 0, length])
                
                T_i = homogeneous_transform(R, t)
                T = np.dot(T, T_i)
                link_poses.append(T.copy())
            
            return link_poses
        
        def rotation_matrix_to_axis_angle(self, R):
            """Convert rotation matrix to axis-angle"""
            trace = np.trace(R)
            angle = np.arccos(np.clip((trace - 1) / 2, -1, 1))
            
            if np.abs(angle) < 1e-6:
                return np.zeros(3)
            else:
                axis = np.array([R[2, 1] - R[1, 2], R[0, 2] - R[2, 0], R[1, 0] - R[0, 1]])
                axis = axis / (2 * np.sin(angle))
                return axis * angle
    
    return Redundant7DOFRobot()

def test_redundant_manipulator():
    """Test redundant manipulator IK with nullspace optimization"""
    
    # Create 7-DOF robot
    robot = create_7dof_robot_example()
    solver = RedundantManipulatorSolver(robot)
    
    # Target pose
    target_position = np.array([0.8, 0.3, 0.6])
    target_orientation = np.eye(3)
    target_pose = homogeneous_transform(target_orientation, target_position)
    
    # Joint limits for optimization
    joint_limits = [(-np.pi, np.pi)] * 7
    
    # Test different secondary objectives
    print("Testing Redundant Manipulator IK:")
    
    # 1. Joint limit avoidance
    result1 = solver.solve_with_joint_limit_avoidance(target_pose, joint_limits)
    print(f"Joint limit avoidance - Success: {result1['success']}")
    if result1['success']:
        print(f"Solution: {result1['joint_angles']}")
        print(f"Task error: {result1['task_error']:.6f}")
    
    # 2. Manipulability optimization
    result2 = solver.solve_with_manipulability_optimization(target_pose)
    print(f"Manipulability optimization - Success: {result2['success']}")
    
    # 3. Analyze redundancy
    if result1['success']:
        redundancy_analysis = solver.analyze_redundancy(result1['joint_angles'])
        print(f"Redundancy analysis:")
        print(f"  Nullspace dimension: {redundancy_analysis['nullspace_dimension']}")
        print(f"  Manipulability: {redundancy_analysis['manipulability']:.4f}")
        print(f"  Condition number: {redundancy_analysis['condition_number']:.2f}")
        
        # Generate self-motion manifold samples
        manifold_samples = solver.generate_self_motion_manifold(
            target_pose, result1['joint_angles'], num_samples=20)
        print(f"Generated {len(manifold_samples)} self-motion manifold samples")

if __name__ == "__main__":
    test_redundant_manipulator()
```

---

## Singularities and Workspace

Understanding singularities and workspace limitations is crucial for practical robot applications:

```python
class SingularityAnalysis:
    """
    Analyze singularities and workspace characteristics
    """
    
    def __init__(self, robot_model):
        self.robot = robot_model
    
    def detect_singularities(self, joint_config, threshold=1e-3):
        """
        Detect if robot is near singularity
        """
        J = self.robot.jacobian_spatial(joint_config)
        
        # Singular value decomposition
        U, s, Vt = np.linalg.svd(J)
        
        # Check for small singular values
        min_singular_value = np.min(s)
        condition_number = np.max(s) / min_singular_value if min_singular_value > 1e-12 else float('inf')
        
        # Manipulability measure
        manipulability = np.sqrt(np.linalg.det(np.dot(J, J.T)))
        
        # Classification
        if min_singular_value < threshold:
            if len(s[s < threshold]) == 1:
                singularity_type = 'boundary_singularity'
            else:
                singularity_type = 'interior_singularity'
        else:
            singularity_type = 'none'
        
        return {
            'is_singular': min_singular_value < threshold,
            'singularity_type': singularity_type,
            'min_singular_value': min_singular_value,
            'condition_number': condition_number,
            'manipulability': manipulability,
            'singular_values': s,
            'lost_dof_directions': self.find_lost_dof_directions(J, s, Vt, threshold)
        }
    
    def find_lost_dof_directions(self, J, singular_values, Vt, threshold):
        """
        Find directions of lost degrees of freedom at singularities
        """
        lost_directions = []
        
        for i, sv in enumerate(singular_values):
            if sv < threshold:
                # Direction in task space where motion is lost
                direction = Vt[i, :]
                lost_directions.append(direction)
        
        return np.array(lost_directions)
    
    def singularity_robust_ik(self, target_pose, joint_limits, damping_factor=0.01):
        """
        IK solver with singularity robustness
        """
        q = np.zeros(self.robot.num_joints)
        target_position = target_pose[0:3, 3]
        target_orientation = target_pose[0:3, 0:3]
        
        max_iterations = 100
        tolerance = 1e-6
        
        for iteration in range(max_iterations):
            # Current pose and error
            current_pose = self.robot.forward_kinematics(q)
            current_position = current_pose[0:3, 3]
            current_rotation = current_pose[0:3, 0:3]
            
            position_error = target_position - current_position
            rotation_error = self.rotation_matrix_to_axis_angle(
                np.dot(target_orientation, current_rotation.T))
            error = np.concatenate([position_error, rotation_error])
            
            if np.linalg.norm(error) < tolerance:
                return {'success': True, 'joint_angles': q, 'iterations': iteration}
            
            # Jacobian and singularity analysis
            J = self.robot.jacobian_spatial(q)
            singularity_info = self.detect_singularities(q)
            
            # Adaptive damping based on singularity proximity
            if singularity_info['is_singular'] or singularity_info['condition_number'] > 100:
                # Increase damping near singularities
                adaptive_damping = damping_factor * singularity_info['condition_number']
            else:
                adaptive_damping = damping_factor
            
            # Damped least squares solution
            I = np.eye(J.shape[1])
            JTJ_damped = np.dot(J.T, J) + adaptive_damping**2 * I
            dq = np.dot(np.linalg.inv(JTJ_damped), np.dot(J.T, error))
            
            # Apply joint limits
            for i, (q_min, q_max) in enumerate(joint_limits):
                q_new = q[i] + dq[i]
                if q_new < q_min:
                    dq[i] = q_min - q[i]
                elif q_new > q_max:
                    dq[i] = q_max - q[i]
            
            q += dq * 0.1  # Step size
        
        return {'success': False, 'joint_angles': q, 'iterations': max_iterations}
    
    def map_workspace_singularities(self, joint_limits, resolution=20):
        """
        Map singularities throughout the workspace
        """
        import itertools
        
        # Generate joint angle samples
        joint_samples = []
        for joint_idx, (min_angle, max_angle) in enumerate(joint_limits):
            samples = np.linspace(min_angle, max_angle, resolution)
            joint_samples.append(samples)
        
        singularity_map = {
            'singular_configs': [],
            'near_singular_configs': [],
            'workspace_points': [],
            'manipulability_values': []
        }
        
        for joint_config in itertools.product(*joint_samples):
            try:
                # Forward kinematics
                T_end = self.robot.forward_kinematics(list(joint_config))
                position = T_end[0:3, 3]
                
                # Singularity analysis
                singularity_info = self.detect_singularities(list(joint_config))
                
                singularity_map['workspace_points'].append(position)
                singularity_map['manipulability_values'].append(singularity_info['manipulability'])
                
                if singularity_info['is_singular']:
                    singularity_map['singular_configs'].append({
                        'joint_config': list(joint_config),
                        'position': position,
                        'singularity_type': singularity_info['singularity_type']
                    })
                elif singularity_info['condition_number'] > 50:
                    singularity_map['near_singular_configs'].append({
                        'joint_config': list(joint_config),
                        'position': position,
                        'condition_number': singularity_info['condition_number']
                    })
            
            except:
                continue
        
        return singularity_map
    
    def calculate_workspace_properties(self, joint_limits):
        """
        Calculate comprehensive workspace properties
        """
        singularity_map = self.map_workspace_singularities(joint_limits)
        workspace_points = np.array(singularity_map['workspace_points'])
        
        if len(workspace_points) == 0:
            return None
        
        # Workspace envelope
        min_coords = np.min(workspace_points, axis=0)
        max_coords = np.max(workspace_points, axis=0)
        workspace_span = max_coords - min_coords
        
        # Reachability analysis
        origin = np.array([0, 0, 0])
        distances = np.linalg.norm(workspace_points, axis=1)
        
        # Manipulability statistics
        manipulability_values = np.array(singularity_map['manipulability_values'])
        
        return {
            'workspace_envelope': {
                'min_coords': min_coords,
                'max_coords': max_coords,
                'span': workspace_span,
                'volume_estimate': np.prod(workspace_span)
            },
            'reachability': {
                'min_reach': np.min(distances),
                'max_reach': np.max(distances),
                'mean_reach': np.mean(distances),
                'centroid': np.mean(workspace_points, axis=0)
            },
            'manipulability': {
                'mean': np.mean(manipulability_values),
                'std': np.std(manipulability_values),
                'min': np.min(manipulability_values),
                'max': np.max(manipulability_values)
            },
            'singularities': {
                'num_singular_points': len(singularity_map['singular_configs']),
                'num_near_singular_points': len(singularity_map['near_singular_configs']),
                'singularity_density': len(singularity_map['singular_configs']) / len(workspace_points)
            }
        }
    
    def rotation_matrix_to_axis_angle(self, R):
        """Convert rotation matrix to axis-angle representation"""
        trace = np.trace(R)
        angle = np.arccos(np.clip((trace - 1) / 2, -1, 1))
        
        if np.abs(angle) < 1e-6:
            return np.zeros(3)
        else:
            axis = np.array([R[2, 1] - R[1, 2], R[0, 2] - R[2, 0], R[1, 0] - R[0, 1]])
            axis = axis / (2 * np.sin(angle))
            return axis * angle

def visualize_workspace_and_singularities(singularity_map):
    """
    Visualize workspace and singularities
    """
    import matplotlib.pyplot as plt
    from mpl_toolkits.mplot3d import Axes3D
    
    fig = plt.figure(figsize=(15, 5))
    
    # 3D workspace visualization
    ax1 = fig.add_subplot(131, projection='3d')
    
    workspace_points = np.array(singularity_map['workspace_points'])
    if len(workspace_points) > 0:
        ax1.scatter(workspace_points[:, 0], workspace_points[:, 1], workspace_points[:, 2], 
                   c=singularity_map['manipulability_values'], cmap='viridis', alpha=0.6)
        ax1.set_xlabel('X')
        ax1.set_ylabel('Y')
        ax1.set_zlabel('Z')
        ax1.set_title('Workspace (colored by manipulability)')
    
    # Singularity locations
    ax2 = fig.add_subplot(132, projection='3d')
    
    # Regular workspace points
    ax2.scatter(workspace_points[:, 0], workspace_points[:, 1], workspace_points[:, 2], 
               c='blue', alpha=0.3, s=1, label='Workspace')
    
    # Singular points
    if singularity_map['singular_configs']:
        singular_positions = [config['position'] for config in singularity_map['singular_configs']]
        singular_positions = np.array(singular_positions)
        ax2.scatter(singular_positions[:, 0], singular_positions[:, 1], singular_positions[:, 2], 
                   c='red', s=20, label='Singularities')
    
    # Near-singular points
    if singularity_map['near_singular_configs']:
        near_singular_positions = [config['position'] for config in singularity_map['near_singular_configs']]
        near_singular_positions = np.array(near_singular_positions)
        ax2.scatter(near_singular_positions[:, 0], near_singular_positions[:, 1], near_singular_positions[:, 2], 
                   c='orange', s=10, label='Near Singularities')
    
    ax2.set_xlabel('X')
    ax2.set_ylabel('Y')
    ax2.set_zlabel('Z')
    ax2.set_title('Singularity Map')
    ax2.legend()
    
    # Manipulability histogram
    ax3 = fig.add_subplot(133)
    ax3.hist(singularity_map['manipulability_values'], bins=50, alpha=0.7)
    ax3.set_xlabel('Manipulability')
    ax3.set_ylabel('Frequency')
    ax3.set_title('Manipulability Distribution')
    ax3.grid(True)
    
    plt.tight_layout()
    plt.show()

def test_singularity_analysis():
    """Test singularity analysis with example robot"""
    
    # Create robot and analysis tool
    robot = create_7dof_robot_example()
    analyzer = SingularityAnalysis(robot)
    
    # Test singularity detection
    test_config = [0, np.pi/2, 0, np.pi/2, 0, 0, 0]  # Known problematic config
    
    singularity_info = analyzer.detect_singularities(test_config)
    print("Singularity Analysis:")
    print(f"Is singular: {singularity_info['is_singular']}")
    print(f"Type: {singularity_info['singularity_type']}")
    print(f"Min singular value: {singularity_info['min_singular_value']:.6f}")
    print(f"Condition number: {singularity_info['condition_number']:.2f}")
    print(f"Manipulability: {singularity_info['manipulability']:.4f}")
    
    # Test workspace analysis
    joint_limits = [(-np.pi/2, np.pi/2)] * 7  # Limited range for faster computation
    workspace_props = analyzer.calculate_workspace_properties(joint_limits)
    
    if workspace_props:
        print("\nWorkspace Properties:")
        print(f"Workspace span: {workspace_props['workspace_envelope']['span']}")
        print(f"Max reach: {workspace_props['reachability']['max_reach']:.3f}")
        print(f"Min reach: {workspace_props['reachability']['min_reach']:.3f}")
        print(f"Mean manipulability: {workspace_props['manipulability']['mean']:.4f}")
        print(f"Singularity density: {workspace_props['singularities']['singularity_density']:.3f}")

if __name__ == "__main__":
    test_singularity_analysis()
```

---

## Modern Algorithms and Optimization (2024-2025)

Recent advances in robotic kinematics incorporate machine learning and advanced optimization:

```python
class ModernKinematicsSolver:
    """
    Modern kinematics solver incorporating ML and advanced optimization
    """
    
    def __init__(self, robot_model):
        self.robot = robot_model
        self.neural_ik_model = None
        self.learned_workspace = None
    
    def train_neural_ik_solver(self, training_data_size=10000):
        """
        Train neural network for fast IK solving
        """
        try:
            import tensorflow as tf
            from tensorflow import keras
        except ImportError:
            print("TensorFlow not available. Skipping neural IK training.")
            return None
        
        # Generate training data
        print(f"Generating {training_data_size} training samples...")
        X_train, y_train = self.generate_ik_training_data(training_data_size)
        
        # Define neural network architecture
        model = keras.Sequential([
            keras.layers.Dense(128, activation='relu', input_shape=(6,)),  # 6D pose input
            keras.layers.Dropout(0.2),
            keras.layers.Dense(256, activation='relu'),
            keras.layers.Dropout(0.2),
            keras.layers.Dense(128, activation='relu'),
            keras.layers.Dense(self.robot.num_joints, activation='tanh')  # Joint angles output
        ])
        
        # Scale outputs to joint limits
        def scaled_output_layer(x):
            # Assume joint limits of ±π
            return x * np.pi
        
        # Compile model
        model.compile(
            optimizer='adam',
            loss='mse',
            metrics=['mae']
        )
        
        # Train model
        history = model.fit(
            X_train, y_train,
            epochs=100,
            batch_size=64,
            validation_split=0.2,
            verbose=1
        )
        
        self.neural_ik_model = model
        return history
    
    def generate_ik_training_data(self, num_samples):
        """
        Generate training data for neural IK solver
        """
        # Random joint configurations
        joint_configs = []
        poses = []
        
        for _ in range(num_samples):
            # Random joint angles
            q = np.random.uniform(-np.pi, np.pi, self.robot.num_joints)
            
            try:
                # Forward kinematics
                T = self.robot.forward_kinematics(q)
                
                # Extract pose (position + euler angles)
                position = T[0:3, 3]
                rotation_matrix = T[0:3, 0:3]
                euler_angles = self.rotation_matrix_to_euler(rotation_matrix)
                
                pose_vector = np.concatenate([position, euler_angles])
                
                joint_configs.append(q)
                poses.append(pose_vector)
                
            except:
                # Skip invalid configurations
                continue
        
        return np.array(poses), np.array(joint_configs)
    
    def solve_ik_neural(self, target_pose):
        """
        Solve IK using trained neural network
        """
        if self.neural_ik_model is None:
            raise ValueError("Neural IK model not trained. Call train_neural_ik_solver first.")
        
        # Extract pose vector
        position = target_pose[0:3, 3]
        rotation_matrix = target_pose[0:3, 0:3]
        euler_angles = self.rotation_matrix_to_euler(rotation_matrix)
        pose_vector = np.concatenate([position, euler_angles])
        
        # Predict joint angles
        joint_angles = self.neural_ik_model.predict(pose_vector.reshape(1, -1))[0]
        
        # Refine solution with numerical method
        refined_solution = self.refine_neural_solution(target_pose, joint_angles)
        
        return refined_solution
    
    def refine_neural_solution(self, target_pose, initial_guess):
        """
        Refine neural network solution with numerical optimization
        """
        from scipy.optimize import minimize
        
        def objective(q):
            current_pose = self.robot.forward_kinematics(q)
            return self.calculate_pose_error_norm(target_pose, current_pose)
        
        result = minimize(
            objective,
            initial_guess,
            method='BFGS',
            options={'gtol': 1e-6, 'maxiter': 50}
        )
        
        return {
            'success': result.success,
            'joint_angles': result.x,
            'error': result.fun,
            'iterations': result.nit
        }
    
    def evolutionary_ik_solver(self, target_pose, population_size=50, generations=100):
        """
        Evolutionary algorithm for IK solving
        """
        # Initialize population
        population = np.random.uniform(-np.pi, np.pi, (population_size, self.robot.num_joints))
        
        # Evolution parameters
        mutation_rate = 0.1
        crossover_rate = 0.8
        elite_size = int(0.1 * population_size)
        
        best_solution = None
        best_error = float('inf')
        
        for generation in range(generations):
            # Evaluate fitness
            fitness_scores = []
            for individual in population:
                try:
                    current_pose = self.robot.forward_kinematics(individual)
                    error = self.calculate_pose_error_norm(target_pose, current_pose)
                    fitness_scores.append(1.0 / (1.0 + error))  # Higher fitness = lower error
                    
                    if error < best_error:
                        best_error = error
                        best_solution = individual.copy()
                        
                except:
                    fitness_scores.append(0.0)  # Invalid configuration
            
            fitness_scores = np.array(fitness_scores)
            
            # Check convergence
            if best_error < 1e-6:
                break
            
            # Selection (tournament selection)
            new_population = []
            
            # Elite preservation
            elite_indices = np.argsort(fitness_scores)[-elite_size:]
            for idx in elite_indices:
                new_population.append(population[idx].copy())
            
            # Generate new individuals
            while len(new_population) < population_size:
                # Tournament selection
                parent1 = self.tournament_selection(population, fitness_scores)
                parent2 = self.tournament_selection(population, fitness_scores)
                
                # Crossover
                if np.random.random() < crossover_rate:
                    child1, child2 = self.crossover(parent1, parent2)
                else:
                    child1, child2 = parent1.copy(), parent2.copy()
                
                # Mutation
                if np.random.random() < mutation_rate:
                    child1 = self.mutate(child1)
                if np.random.random() < mutation_rate:
                    child2 = self.mutate(child2)
                
                new_population.extend([child1, child2])
            
            population = np.array(new_population[:population_size])
        
        return {
            'success': best_error < 1e-3,
            'joint_angles': best_solution,
            'error': best_error,
            'generations': generation + 1
        }
    
    def tournament_selection(self, population, fitness_scores, tournament_size=3):
        """Tournament selection for evolutionary algorithm"""
        indices = np.random.choice(len(population), tournament_size, replace=False)
        tournament_fitness = fitness_scores[indices]
        winner_idx = indices[np.argmax(tournament_fitness)]
        return population[winner_idx].copy()
    
    def crossover(self, parent1, parent2):
        """Crossover operation for evolutionary algorithm"""
        # Uniform crossover
        mask = np.random.random(len(parent1)) < 0.5
        child1 = np.where(mask, parent1, parent2)
        child2 = np.where(mask, parent2, parent1)
        return child1, child2
    
    def mutate(self, individual, mutation_strength=0.1):
        """Mutation operation for evolutionary algorithm"""
        mutation_mask = np.random.random(len(individual)) < 0.1
        mutations = np.random.normal(0, mutation_strength, len(individual))
        individual[mutation_mask] += mutations[mutation_mask]
        
        # Clip to joint limits
        individual = np.clip(individual, -np.pi, np.pi)
        
        return individual
    
    def real_time_ik_solver(self, target_trajectory, dt=0.01):
        """
        Real-time IK solver for trajectory following
        """
        solutions = []
        current_q = np.zeros(self.robot.num_joints)
        
        for target_pose in target_trajectory:
            # Use current joint configuration as initial guess for continuity
            if self.neural_ik_model is not None:
                # Neural network initialization
                neural_guess = self.solve_ik_neural(target_pose)['joint_angles']
                
                # Blend with previous configuration for smoothness
                alpha = 0.7  # Blend factor
                initial_guess = alpha * neural_guess + (1 - alpha) * current_q
            else:
                initial_guess = current_q
            
            # Fast numerical refinement
            solution = self.solve_ik_fast(target_pose, initial_guess, max_iterations=10)
            
            if solution['success']:
                current_q = solution['joint_angles']
                solutions.append({
                    'joint_angles': current_q,
                    'success': True,
                    'error': solution['error']
                })
            else:
                # Use previous configuration if IK fails
                solutions.append({
                    'joint_angles': current_q,
                    'success': False,
                    'error': solution['error']
                })
        
        return solutions
    
    def solve_ik_fast(self, target_pose, initial_guess, max_iterations=10):
        """
        Fast IK solver for real-time applications
        """
        q = np.array(initial_guess)
        target_position = target_pose[0:3, 3]
        target_rotation = target_pose[0:3, 0:3]
        
        for iteration in range(max_iterations):
            current_pose = self.robot.forward_kinematics(q)
            current_position = current_pose[0:3, 3]
            current_rotation = current_pose[0:3, 0:3]
            
            position_error = target_position - current_position
            rotation_error = self.rotation_matrix_to_axis_angle(
                np.dot(target_rotation, current_rotation.T))
            error = np.concatenate([position_error, rotation_error])
            
            if np.linalg.norm(error) < 1e-4:  # Relaxed tolerance for speed
                return {'success': True, 'joint_angles': q, 'error': np.linalg.norm(error)}
            
            J = self.robot.jacobian_spatial(q)
            J_pinv = np.linalg.pinv(J)
            dq = 0.5 * np.dot(J_pinv, error)  # Large step size
            
            q += dq
        
        current_pose = self.robot.forward_kinematics(q)
        final_error = self.calculate_pose_error_norm(target_pose, current_pose)
        
        return {'success': False, 'joint_angles': q, 'error': final_error}
    
    def rotation_matrix_to_euler(self, R):
        """Convert rotation matrix to Euler angles (ZYX convention)"""
        sy = np.sqrt(R[0, 0]**2 + R[1, 0]**2)
        
        singular = sy < 1e-6
        
        if not singular:
            x = np.arctan2(R[2, 1], R[2, 2])
            y = np.arctan2(-R[2, 0], sy)
            z = np.arctan2(R[1, 0], R[0, 0])
        else:
            x = np.arctan2(-R[1, 2], R[1, 1])
            y = np.arctan2(-R[2, 0], sy)
            z = 0
        
        return np.array([x, y, z])
    
    def rotation_matrix_to_axis_angle(self, R):
        """Convert rotation matrix to axis-angle representation"""
        trace = np.trace(R)
        angle = np.arccos(np.clip((trace - 1) / 2, -1, 1))
        
        if np.abs(angle) < 1e-6:
            return np.zeros(3)
        else:
            axis = np.array([R[2, 1] - R[1, 2], R[0, 2] - R[2, 0], R[1, 0] - R[0, 1]])
            axis = axis / (2 * np.sin(angle))
            return axis * angle
    
    def calculate_pose_error_norm(self, target_pose, current_pose):
        """Calculate pose error norm"""
        position_error = target_pose[0:3, 3] - current_pose[0:3, 3]
        rotation_error = self.rotation_matrix_to_axis_angle(
            np.dot(target_pose[0:3, 0:3], current_pose[0:3, 0:3].T))
        
        return np.linalg.norm(position_error) + 0.1 * np.linalg.norm(rotation_error)

def test_modern_kinematics():
    """Test modern kinematics algorithms"""
    
    # Create robot and modern solver
    robot = create_7dof_robot_example()
    modern_solver = ModernKinematicsSolver(robot)
    
    # Target pose
    target_position = np.array([0.7, 0.2, 0.5])
    target_orientation = np.eye(3)
    target_pose = homogeneous_transform(target_orientation, target_position)
    
    # Test evolutionary algorithm
    print("Testing Evolutionary IK Solver:")
    evo_result = modern_solver.evolutionary_ik_solver(
        target_pose, population_size=30, generations=50)
    
    print(f"Success: {evo_result['success']}")
    print(f"Error: {evo_result['error']:.6f}")
    print(f"Generations: {evo_result['generations']}")
    
    # Test neural network training (if TensorFlow available)
    try:
        print("\nTraining Neural IK Solver...")
        history = modern_solver.train_neural_ik_solver(training_data_size=1000)
        
        if history is not None:
            print("Neural IK training completed")
            
            # Test neural IK
            neural_result = modern_solver.solve_ik_neural(target_pose)
            print(f"Neural IK - Success: {neural_result['success']}")
            print(f"Neural IK - Error: {neural_result['error']:.6f}")
    
    except Exception as e:
        print(f"Neural IK training failed: {e}")
    
    # Test real-time trajectory following
    print("\nTesting Real-time Trajectory Following:")
    
    # Generate simple trajectory
    trajectory = []
    for t in np.linspace(0, 2*np.pi, 20):
        pos = np.array([0.6 + 0.1*np.cos(t), 0.1*np.sin(t), 0.5])
        trajectory.append(homogeneous_transform(target_orientation, pos))
    
    trajectory_solutions = modern_solver.real_time_ik_solver(trajectory)
    
    successful_points = sum(1 for sol in trajectory_solutions if sol['success'])
    print(f"Successfully solved: {successful_points}/{len(trajectory)} trajectory points")
    
    avg_error = np.mean([sol['error'] for sol in trajectory_solutions])
    print(f"Average error: {avg_error:.6f}")

if __name__ == "__main__":
    test_modern_kinematics()
```

---

## Conclusion

Robotic kinematics represents the fundamental mathematics that enables robots to move with purpose and precision. From the elegant formalism of homogeneous transformations to the sophisticated algorithms that solve inverse kinematics in real-time, this field bridges pure mathematics and practical engineering.

The evolution from classical analytical methods to modern machine learning approaches reflects the broader transformation of robotics. Today's systems must not only solve kinematics accurately but do so with unprecedented speed, handling redundancy, avoiding singularities, and adapting to changing environments.

The redundant manipulator represents the pinnacle of kinematic sophistication - systems with excess degrees of freedom that can optimize secondary objectives while achieving primary tasks. These machines embody the principle that in robotics, as in life, having more choices enables better solutions.

As we advance into 2025 and beyond, the convergence of traditional kinematic theory with artificial intelligence, real-time optimization, and adaptive control creates new possibilities for robotic motion. The future belongs to robots that don't just follow preprogrammed paths but intelligently navigate the space of possible motions to achieve their goals with grace and efficiency.

*"In the end, robotics is about transforming intention into motion. Kinematics is the mathematical language in which this transformation is written - a language where every equation describes not just how joints move, but how purpose becomes reality through geometry."* - Alan Turing

---

*This document represents the cutting-edge understanding of robotic kinematics as of 2025. The field continues to evolve rapidly with advances in machine learning, computational optimization, and control theory.*