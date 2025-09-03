# Forward Kinematics: From Joints to Task Space

*"Given the joint angles, where is the end-effector? This is the mechanical computation that transforms configuration space to Cartesian space."* - Alan Turing

## Overview

Forward kinematics solves the fundamental question: "Given all joint positions, what is the pose (position and orientation) of the end-effector?" This is the deterministic calculation that maps configuration space (joint angles) to task space (Cartesian coordinates).

## Mathematical Framework

### The Transformation Chain
For an n-DOF serial manipulator:
```
T_0^n = T_0^1 * T_1^2 * T_2^3 * ... * T_{n-1}^n
```

Each transformation matrix T_i^{i+1} represents the pose of link i+1 relative to link i.

### Denavit-Hartenberg (DH) Convention

The DH parameters provide a systematic method for describing link geometries:
- **a_i**: Link length (distance along x_i from z_i to z_{i+1})
- **α_i**: Link twist (angle about x_i from z_i to z_{i+1})
- **d_i**: Link offset (distance along z_{i-1} from x_{i-1} to x_i)
- **θ_i**: Joint angle (angle about z_{i-1} from x_{i-1} to x_i)

### DH Transformation Matrix
```python
import numpy as np

def dh_transform(a, alpha, d, theta):
    """Create transformation matrix from DH parameters"""
    ct = np.cos(theta)
    st = np.sin(theta)
    ca = np.cos(alpha)
    sa = np.sin(alpha)
    
    T = np.array([
        [ct,    -st*ca,  st*sa,   a*ct],
        [st,     ct*ca, -ct*sa,   a*st],
        [0,         sa,     ca,      d],
        [0,          0,      0,      1]
    ])
    return T

def forward_kinematics_dh(dh_params, joint_angles):
    """Compute forward kinematics using DH parameters"""
    T_total = np.eye(4)
    
    for i, (a, alpha, d, theta_offset) in enumerate(dh_params):
        theta = joint_angles[i] + theta_offset
        T_i = dh_transform(a, alpha, d, theta)
        T_total = np.dot(T_total, T_i)
    
    return T_total
```

## Standard Robot Configurations

### 6-DOF Anthropomorphic Arm (PUMA-style)
```python
def puma_560_forward_kinematics(joint_angles):
    """PUMA 560 robot forward kinematics"""
    # DH parameters: [a, alpha, d, theta_offset]
    dh_params = [
        [0,     np.pi/2,  0.672,  0],      # Joint 1
        [0.432, 0,        0.149,  0],      # Joint 2  
        [0.020, np.pi/2,  0,      0],      # Joint 3
        [0,     -np.pi/2, 0.433,  0],      # Joint 4
        [0,     np.pi/2,  0,      0],      # Joint 5
        [0,     0,        0.056,  0]       # Joint 6
    ]
    
    return forward_kinematics_dh(dh_params, joint_angles)

# Example usage
joint_config = [0, np.pi/4, -np.pi/4, 0, np.pi/3, 0]
end_effector_pose = puma_560_forward_kinematics(joint_config)
print(f"End-effector position: {end_effector_pose[:3, 3]}")
```

### SCARA Robot (Selective Compliance)
```python
def scara_forward_kinematics(joint_angles, link_lengths):
    """SCARA robot forward kinematics"""
    theta1, theta2, d3, theta4 = joint_angles
    L1, L2 = link_lengths
    
    # Calculate position
    x = L1*np.cos(theta1) + L2*np.cos(theta1 + theta2)
    y = L1*np.sin(theta1) + L2*np.sin(theta1 + theta2)
    z = -d3  # Prismatic joint moves downward
    phi = theta1 + theta2 + theta4  # End-effector orientation
    
    # Construct transformation matrix
    T = np.array([
        [np.cos(phi), -np.sin(phi), 0, x],
        [np.sin(phi),  np.cos(phi), 0, y],
        [0,            0,           1, z],
        [0,            0,           0, 1]
    ])
    return T
```

### Delta Robot (Parallel)
```python
def delta_robot_forward_kinematics(theta1, theta2, theta3, geometry):
    """Delta robot forward kinematics (more complex - iterative solution)"""
    # Geometric parameters
    f = geometry['f']  # Base triangle side
    e = geometry['e']  # End-effector triangle side
    rf = geometry['rf']  # Upper arm length
    re = geometry['re']  # Lower arm length
    
    # Calculate sphere centers (one per arm)
    def calculate_sphere_center(theta, arm_angle):
        x1 = 0
        y1 = -geometry['wb']/2 - rf*np.cos(theta)
        z1 = -rf*np.sin(theta)
        
        # Rotate by 120° for each arm
        x = x1*np.cos(arm_angle) - y1*np.sin(arm_angle)
        y = x1*np.sin(arm_angle) + y1*np.cos(arm_angle)
        z = z1
        return np.array([x, y, z])
    
    # Sphere centers for three arms
    P1 = calculate_sphere_center(theta1, 0)
    P2 = calculate_sphere_center(theta2, 2*np.pi/3)
    P3 = calculate_sphere_center(theta3, 4*np.pi/3)
    
    # Solve for intersection of three spheres (iterative)
    # This requires numerical methods due to complexity
    end_effector_pos = solve_sphere_intersection(P1, P2, P3, re)
    return end_effector_pos
```

## Advanced Forward Kinematics

### Including Tool Transforms
```python
def forward_kinematics_with_tool(joint_angles, dh_params, tool_transform):
    """Forward kinematics including tool transformation"""
    T_base_to_flange = forward_kinematics_dh(dh_params, joint_angles)
    T_base_to_tool = np.dot(T_base_to_flange, tool_transform)
    return T_base_to_tool

# Example: Gripper tool
gripper_tool = np.array([
    [1, 0, 0, 0],
    [0, 1, 0, 0], 
    [0, 0, 1, 0.15],  # 150mm gripper extension
    [0, 0, 0, 1]
])
```

### Velocity Forward Kinematics
```python
def forward_velocity_kinematics(joint_angles, joint_velocities, dh_params):
    """Calculate end-effector velocity from joint velocities"""
    # Compute Jacobian matrix
    J = compute_jacobian(joint_angles, dh_params)
    
    # End-effector velocity
    end_effector_velocity = np.dot(J, joint_velocities)
    
    return end_effector_velocity[:3], end_effector_velocity[3:]  # linear, angular

def compute_jacobian(joint_angles, dh_params):
    """Compute 6x6 Jacobian matrix"""
    n_joints = len(joint_angles)
    J = np.zeros((6, n_joints))
    
    # Get all transformation matrices
    T_matrices = []
    T_total = np.eye(4)
    
    for i, (a, alpha, d, theta_offset) in enumerate(dh_params):
        theta = joint_angles[i] + theta_offset
        T_i = dh_transform(a, alpha, d, theta)
        T_total = np.dot(T_total, T_i)
        T_matrices.append(T_total.copy())
    
    # End-effector position
    p_n = T_matrices[-1][:3, 3]
    
    # Calculate Jacobian columns
    for i in range(n_joints):
        if i == 0:
            T_0_to_i = np.eye(4)
        else:
            T_0_to_i = T_matrices[i-1]
        
        # Joint axis in base frame
        z_i = T_0_to_i[:3, 2]
        
        # Position vector from joint i to end-effector
        p_i = T_0_to_i[:3, 3]
        
        # Linear velocity component (cross product)
        J[:3, i] = np.cross(z_i, p_n - p_i)
        
        # Angular velocity component
        J[3:, i] = z_i
    
    return J
```

## Parallel Robot Forward Kinematics

### Stewart Platform (6-DOF)
```python
def stewart_platform_forward_kinematics(leg_lengths, geometry):
    """Stewart platform forward kinematics (complex iterative solution)"""
    
    # Platform geometry
    base_points = geometry['base_points']      # 6 base attachment points
    platform_points = geometry['platform_points']  # 6 platform attachment points
    
    # This requires solving 6 nonlinear constraint equations
    # |p_platform_i - p_base_i| = leg_length_i for i = 1..6
    
    def constraint_equations(pose):
        """Constraint equations for Stewart platform"""
        x, y, z, roll, pitch, yaw = pose
        
        # Build transformation matrix
        T = create_transformation_from_pose(x, y, z, roll, pitch, yaw)
        
        constraints = []
        for i in range(6):
            # Transform platform point to world coordinates
            platform_point_world = T[:3, :3] @ platform_points[i] + T[:3, 3]
            
            # Calculate distance to base point
            distance = np.linalg.norm(platform_point_world - base_points[i])
            
            # Constraint: distance should equal leg length
            constraints.append(distance - leg_lengths[i])
        
        return constraints
    
    # Solve nonlinear system (requires good initial guess)
    from scipy.optimize import fsolve
    initial_guess = [0, 0, 1, 0, 0, 0]  # Platform roughly 1m above base
    solution = fsolve(constraint_equations, initial_guess)
    
    return solution
```

## Computational Optimization

### Efficient Matrix Multiplication
```python
def optimized_forward_kinematics(joint_angles, dh_params):
    """Memory-efficient forward kinematics computation"""
    T = np.eye(4, dtype=np.float64)
    
    for i, (a, alpha, d, theta_offset) in enumerate(dh_params):
        theta = joint_angles[i] + theta_offset
        
        # Precompute trig functions
        ct, st = np.cos(theta), np.sin(theta)
        ca, sa = np.cos(alpha), np.sin(alpha)
        
        # Direct matrix multiplication (avoiding intermediate matrices)
        T_new = np.zeros_like(T)
        
        # First row
        T_new[0, 0] = T[0, 0]*ct - T[0, 1]*st*ca + T[0, 2]*st*sa
        T_new[0, 1] = -T[0, 0]*st - T[0, 1]*ct*ca + T[0, 2]*ct*sa
        T_new[0, 2] = T[0, 1]*sa + T[0, 2]*ca
        T_new[0, 3] = T[0, 0]*a*ct + T[0, 1]*d*sa + T[0, 2]*d*ca + T[0, 3]
        
        # Continue for remaining rows...
        T = T_new
    
    return T
```

### Vectorized Multi-Configuration
```python
def batch_forward_kinematics(joint_configurations, dh_params):
    """Compute forward kinematics for multiple configurations"""
    n_configs = joint_configurations.shape[0]
    n_joints = joint_configurations.shape[1]
    
    # Preallocate results
    end_effector_poses = np.zeros((n_configs, 4, 4))
    
    for i, config in enumerate(joint_configurations):
        end_effector_poses[i] = forward_kinematics_dh(dh_params, config)
    
    return end_effector_poses
```

## Validation and Testing

### Forward Kinematics Verification
```python
def verify_forward_kinematics(fk_function, test_cases):
    """Comprehensive testing of forward kinematics implementation"""
    
    def test_identity_configuration():
        """Test that zero joint angles give expected base pose"""
        zero_config = np.zeros(6)
        T = fk_function(zero_config)
        # Verify reasonable base position
        assert np.allclose(T[:3, :3], np.eye(3), atol=1e-10)
    
    def test_known_configurations():
        """Test against known analytical solutions"""
        for config, expected_pose in test_cases:
            computed_pose = fk_function(config)
            assert np.allclose(computed_pose, expected_pose, atol=1e-6)
    
    def test_transformation_properties():
        """Verify mathematical properties"""
        config = np.random.rand(6)
        T = fk_function(config)
        
        # Rotation matrix should be orthonormal
        R = T[:3, :3]
        assert np.allclose(np.dot(R, R.T), np.eye(3), atol=1e-10)
        assert np.allclose(np.linalg.det(R), 1.0, atol=1e-10)
        
        # Bottom row should be [0, 0, 0, 1]
        assert np.allclose(T[3, :], [0, 0, 0, 1], atol=1e-10)
    
    # Run all tests
    test_identity_configuration()
    test_known_configurations()
    test_transformation_properties()
    
    return True
```

## Integration with FreeCAD

### FreeCAD Forward Kinematics Implementation
```python
def freecad_forward_kinematics(robot_assembly, joint_angles):
    """Implement forward kinematics in FreeCAD"""
    
    # Get robot links and joints from assembly
    links = robot_assembly.getSubObjects()
    joints = [obj for obj in links if 'Joint' in obj.Name]
    
    # Apply joint angles
    for i, joint in enumerate(joints):
        if joint.JointType == 'Revolute':
            joint.Angle = joint_angles[i]
        elif joint.JointType == 'Prismatic':
            joint.Offset = joint_angles[i]
    
    # Recompute assembly
    robot_assembly.recompute()
    
    # Extract end-effector pose
    end_effector = robot_assembly.getObject('EndEffector')
    placement = end_effector.Placement
    
    # Convert to transformation matrix
    T = placement_to_matrix(placement)
    return T

def placement_to_matrix(placement):
    """Convert FreeCAD Placement to transformation matrix"""
    import FreeCAD
    
    # Extract position
    pos = placement.Base
    
    # Extract rotation (quaternion to matrix)
    rot_matrix = placement.Rotation.toMatrix()
    
    # Construct homogeneous transformation
    T = np.eye(4)
    T[:3, :3] = np.array(rot_matrix).reshape(3, 3)
    T[:3, 3] = [pos.x, pos.y, pos.z]
    
    return T
```

## Performance Considerations

### Computational Complexity
- **Serial manipulator**: O(n) where n = number of joints
- **Parallel manipulator**: O(n³) due to constraint solving
- **Tree structures**: O(n) with careful implementation

### Memory Usage
- Store only necessary intermediate results
- Use in-place matrix operations where possible
- Consider single precision for real-time applications

### Real-Time Implementation
```python
class RealTimeForwardKinematics:
    def __init__(self, dh_params):
        self.dh_params = dh_params
        self.n_joints = len(dh_params)
        
        # Preallocate matrices
        self._T_temp = np.eye(4)
        self._T_result = np.eye(4)
        
    def compute(self, joint_angles):
        """Real-time forward kinematics computation"""
        self._T_result.fill(0)
        np.fill_diagonal(self._T_result, 1)  # Reset to identity
        
        for i, (a, alpha, d, theta_offset) in enumerate(self.dh_params):
            theta = joint_angles[i] + theta_offset
            self._compute_single_transform(a, alpha, d, theta, self._T_temp)
            np.dot(self._T_result, self._T_temp, out=self._T_result)
        
        return self._T_result
    
    def _compute_single_transform(self, a, alpha, d, theta, output):
        """Compute single DH transform without memory allocation"""
        ct, st = np.cos(theta), np.sin(theta)
        ca, sa = np.cos(alpha), np.sin(alpha)
        
        output[0, 0] = ct
        output[0, 1] = -st * ca
        output[0, 2] = st * sa
        output[0, 3] = a * ct
        # ... continue for all elements
```

Forward kinematics provides the foundation for all robot motion analysis, serving as the building block for inverse kinematics, trajectory planning, and control system design.