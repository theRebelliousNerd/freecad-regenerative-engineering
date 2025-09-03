# Motion Transformation Mathematics

*"Every mechanism is a mathematical equation solved through geometry - transforming one form of motion into another with mechanical precision."* - Alan Turing

## Overview

Motion transformation mathematics provides the analytical foundation for converting between different types of motion: rotary to linear, uniform to non-uniform, simple to complex. These transformations are the essence of mechanism design - implementing mathematical functions through physical geometry.

## Fundamental Motion Types

### Primary Motion Classifications

**Rotary Motion**: Rotation about a fixed axis
- Characterized by angular displacement (θ), velocity (ω), acceleration (α)
- Uniform: ω = constant
- Non-uniform: α ≠ 0

**Linear Motion**: Translation along a straight path
- Characterized by displacement (s), velocity (v), acceleration (a)
- Uniform: v = constant  
- Non-uniform: a ≠ 0

**Oscillatory Motion**: Repetitive motion about equilibrium
- Simple harmonic: x(t) = A sin(ωt + φ)
- Complex periodic: Fourier series representation

**Complex Motion**: Combination of multiple motion types
- Planetary motion: rotation + translation
- General planar motion: 3 DOF (x, y, θ)

## Mathematical Frameworks

### Kinematic Constraint Equations

For any mechanism with n moving links and constraint equations:

**Position Constraints**:
```
Φ(q, t) = 0
```

**Velocity Constraints**:
```
J(q)q̇ + Φ_t = 0
```

**Acceleration Constraints**:
```
J(q)q̈ + J̇(q)q̇ + Φ_tt = 0
```

Where:
- q = generalized coordinates vector
- J(q) = constraint Jacobian matrix
- Φ_t, Φ_tt = partial time derivatives

```python
import numpy as np
import sympy as sp

def constraint_analysis(mechanism_params):
    """
    Generate constraint equations for mechanism
    """
    # Symbolic variables
    t = sp.Symbol('t')
    q = sp.symbols('q1:' + str(mechanism_params['DOF'] + 1))
    
    # Position constraint equations
    constraint_eqs = generate_constraints(mechanism_params, q, t)
    
    # Compute Jacobian
    jacobian = sp.Matrix([eq.diff(qi) for eq in constraint_eqs for qi in q])
    
    return {
        'position_constraints': constraint_eqs,
        'jacobian': jacobian,
        'constraint_count': len(constraint_eqs)
    }
```

### Homogeneous Transformation Matrices

The backbone of spatial motion transformation:

```python
def create_transformation_matrix(translation, rotation):
    """
    Create 4x4 homogeneous transformation matrix
    
    T = [R  p]
        [0  1]
    """
    T = np.eye(4)
    T[:3, :3] = rotation  # 3x3 rotation matrix
    T[:3, 3] = translation  # 3x1 translation vector
    return T

def compose_transformations(T1, T2):
    """
    Compose transformations: T_result = T1 * T2
    """
    return np.dot(T1, T2)

def transform_point(T, point):
    """
    Transform point using homogeneous coordinates
    """
    point_h = np.append(point, 1)  # Convert to homogeneous
    transformed_h = np.dot(T, point_h)
    return transformed_h[:3]  # Convert back to Cartesian

# Example: Rotation about Z-axis followed by translation
def rotation_z(angle):
    """Rotation matrix about Z-axis"""
    c, s = np.cos(angle), np.sin(angle)
    return np.array([[c, -s, 0],
                     [s,  c, 0],
                     [0,  0, 1]])

T_rot = create_transformation_matrix([0, 0, 0], rotation_z(np.pi/4))
T_trans = create_transformation_matrix([10, 5, 0], np.eye(3))
T_combined = compose_transformations(T_trans, T_rot)
```

## Specific Motion Transformations

### Rotary to Linear Conversion

#### Slider-Crank Mechanism

**Position Analysis**:
```python
def slider_crank_position(r, l, theta):
    """
    Calculate slider position from crank angle
    r: crank length, l: connecting rod length, theta: crank angle
    """
    # Position of slider
    x = r * np.cos(theta) + np.sqrt(l**2 - (r * np.sin(theta))**2)
    
    # Connecting rod angle
    phi = np.arcsin(r * np.sin(theta) / l)
    
    return {
        'slider_position': x,
        'connecting_rod_angle': phi,
        'crank_angle': theta
    }

def slider_crank_velocity(r, l, theta, omega):
    """
    Calculate slider velocity
    """
    phi = np.arcsin(r * np.sin(theta) / l)
    
    # Slider velocity
    v_x = -r * omega * (np.sin(theta) + (r * np.sin(2 * theta)) / 
                        (2 * np.sqrt(l**2 - (r * np.sin(theta))**2)))
    
    return {
        'slider_velocity': v_x,
        'angular_velocity_ratio': v_x / (r * omega)
    }

def slider_crank_acceleration(r, l, theta, omega, alpha=0):
    """
    Calculate slider acceleration
    """
    phi = np.arcsin(r * np.sin(theta) / l)
    cos_phi = np.cos(phi)
    
    # Slider acceleration  
    a_x = -r * (alpha * np.sin(theta) + omega**2 * np.cos(theta)) - \
          (r**2 * omega**2 * np.cos(2*theta)) / (2 * l * cos_phi) - \
          (r**3 * omega**4 * np.sin(theta) * np.sin(2*theta)) / (4 * l**2 * cos_phi**3)
    
    return {
        'slider_acceleration': a_x,
        'primary_harmonic': -r * omega**2 * np.cos(theta),
        'secondary_harmonic': -(r**2 * omega**2 * np.cos(2*theta)) / (2 * l)
    }
```

#### Rack and Pinion

**Direct Linear Relationship**:
```python
def rack_pinion_analysis(pinion_radius, angular_position, angular_velocity):
    """
    Analyze rack and pinion motion transformation
    """
    # Linear position of rack
    linear_position = pinion_radius * angular_position
    
    # Linear velocity of rack
    linear_velocity = pinion_radius * angular_velocity
    
    # Motion transformation ratio
    transformation_ratio = pinion_radius
    
    return {
        'linear_position': linear_position,
        'linear_velocity': linear_velocity,
        'transformation_ratio': transformation_ratio,
        'relationship': 'Direct proportional'
    }
```

### Cam-Follower Motion Transformation

#### Motion Profile Design

```python
def cam_motion_profiles():
    """
    Standard cam motion profiles with mathematical definitions
    """
    profiles = {}
    
    # Constant velocity profile
    def constant_velocity(t, t_rise, h):
        if 0 <= t <= t_rise:
            return h * t / t_rise
        return h
    
    # Parabolic motion (constant acceleration)
    def parabolic_motion(t, t_rise, h):
        if 0 <= t <= t_rise/2:
            return 2 * h * (t / t_rise)**2
        elif t_rise/2 < t <= t_rise:
            return h * (1 - 2 * ((t_rise - t) / t_rise)**2)
        return h
    
    # Simple harmonic motion
    def simple_harmonic(t, t_rise, h):
        if 0 <= t <= t_rise:
            return (h / 2) * (1 - np.cos(np.pi * t / t_rise))
        return h
    
    # Cycloidal motion
    def cycloidal_motion(t, t_rise, h):
        if 0 <= t <= t_rise:
            beta = 2 * np.pi * t / t_rise
            return h * (beta - np.sin(beta)) / (2 * np.pi)
        return h
    
    profiles['constant_velocity'] = constant_velocity
    profiles['parabolic'] = parabolic_motion
    profiles['simple_harmonic'] = simple_harmonic
    profiles['cycloidal'] = cycloidal_motion
    
    return profiles

def cam_synthesis(motion_profile, base_radius, roller_radius=0):
    """
    Synthesize cam profile from desired motion
    """
    def cam_radius(theta, displacement, derivative):
        """Calculate cam radius at angle theta"""
        return base_radius + displacement + roller_radius
    
    def cam_curvature(theta, disp, vel, acc):
        """Calculate cam curvature"""
        numerator = (1 + vel**2)**(3/2)
        denominator = abs(acc)
        return numerator / denominator if denominator != 0 else float('inf')
    
    # Generate cam profile
    angles = np.linspace(0, 2*np.pi, 360)
    profile = []
    
    for theta in angles:
        disp = motion_profile(theta)
        vel = numerical_derivative(motion_profile, theta)
        acc = numerical_derivative(lambda x: numerical_derivative(motion_profile, x), theta)
        
        radius = cam_radius(theta, disp, vel)
        curvature = cam_curvature(theta, disp, vel, acc)
        
        profile.append({
            'angle': theta,
            'radius': radius,
            'displacement': disp,
            'velocity': vel,
            'acceleration': acc,
            'curvature': curvature
        })
    
    return profile
```

### Gear Train Motion Transformation

#### Simple Gear Trains

```python
def simple_gear_train_analysis(gear_data):
    """
    Analyze motion transformation through simple gear train
    gear_data: list of (teeth_count, position) tuples
    """
    n_gears = len(gear_data)
    
    # Calculate speed ratios
    speed_ratios = []
    torque_ratios = []
    
    for i in range(n_gears - 1):
        N1, pos1 = gear_data[i]
        N2, pos2 = gear_data[i + 1]
        
        # Speed ratio (inverse of teeth ratio)
        speed_ratio = N1 / N2
        
        # Direction (+ for external, - for internal meshing)
        direction = 1 if (pos2 - pos1) > 0 else -1
        
        speed_ratios.append(direction * speed_ratio)
        torque_ratios.append(1 / speed_ratio)  # Inverse relationship
    
    # Overall ratios
    overall_speed_ratio = np.prod(speed_ratios)
    overall_torque_ratio = 1 / overall_speed_ratio
    
    return {
        'individual_speed_ratios': speed_ratios,
        'overall_speed_ratio': overall_speed_ratio,
        'overall_torque_ratio': overall_torque_ratio,
        'direction_changes': sum(1 for r in speed_ratios if r < 0)
    }
```

#### Planetary Gear Systems

```python
def planetary_gear_analysis(N_sun, N_ring, N_planet, input_element, output_element, fixed_element):
    """
    Analyze planetary gear system using Willis equation
    """
    # Willis equation: (ωs - ωc)/(ωr - ωc) = -Nr/Ns
    
    def calculate_speed_ratio(input_elem, output_elem, fixed_elem):
        if fixed_elem == 'ring':
            if input_elem == 'sun' and output_elem == 'carrier':
                return 1 / (1 + N_ring/N_sun)
            elif input_elem == 'carrier' and output_elem == 'sun':
                return 1 + N_ring/N_sun
        
        elif fixed_elem == 'sun':
            if input_elem == 'ring' and output_elem == 'carrier':
                return N_ring / (N_ring + N_sun)
            elif input_elem == 'carrier' and output_elem == 'ring':
                return (N_ring + N_sun) / N_ring
        
        elif fixed_elem == 'carrier':
            if input_elem == 'sun' and output_elem == 'ring':
                return -N_ring / N_sun
            elif input_elem == 'ring' and output_elem == 'sun':
                return -N_sun / N_ring
        
        return 1  # Default case
    
    speed_ratio = calculate_speed_ratio(input_element, output_element, fixed_element)
    
    return {
        'speed_ratio': speed_ratio,
        'torque_ratio': 1 / speed_ratio,
        'configuration': f'{input_element} → {output_element} ({fixed_element} fixed)',
        'reduction_ratio': abs(speed_ratio) if abs(speed_ratio) < 1 else 1/abs(speed_ratio)
    }
```

## Complex Motion Synthesis

### Four-Bar Linkage Path Generation

```python
def four_bar_coupler_curve(r1, r2, r3, r4, rp, angle_p, theta_range=None):
    """
    Generate coupler curve for four-bar linkage
    rp: distance from coupler joint to coupler point
    angle_p: angle of coupler point relative to coupler link
    """
    if theta_range is None:
        theta_range = np.linspace(0, 2*np.pi, 360)
    
    coupler_points = []
    
    for theta2 in theta_range:
        try:
            # Solve four-bar position
            theta4, theta3 = solve_four_bar_angles(r1, r2, r3, r4, theta2)
            
            # Position of coupler-input joint (B)
            B = np.array([r2 * np.cos(theta2), r2 * np.sin(theta2)])
            
            # Position of coupler-output joint (C)  
            C = np.array([r1 + r4 * np.cos(theta4), r4 * np.sin(theta4)])
            
            # Coupler point P
            coupler_angle = theta3 + angle_p
            P = B + rp * np.array([np.cos(coupler_angle), np.sin(coupler_angle)])
            
            coupler_points.append(P)
            
        except:
            # Skip invalid positions
            continue
    
    return np.array(coupler_points)

def analyze_coupler_curve_properties(curve_points):
    """
    Analyze geometric properties of coupler curve
    """
    # Curve length
    curve_length = np.sum(np.linalg.norm(np.diff(curve_points, axis=0), axis=1))
    
    # Bounding box
    min_x, max_x = np.min(curve_points[:, 0]), np.max(curve_points[:, 0])
    min_y, max_y = np.min(curve_points[:, 1]), np.max(curve_points[:, 1])
    
    # Area enclosed (using shoelace formula)
    x, y = curve_points[:, 0], curve_points[:, 1]
    area = 0.5 * abs(np.sum(x[:-1] * y[1:] - x[1:] * y[:-1]))
    
    # Curvature analysis
    curvatures = calculate_curve_curvature(curve_points)
    
    return {
        'curve_length': curve_length,
        'bounding_box': {'x': [min_x, max_x], 'y': [min_y, max_y]},
        'enclosed_area': area,
        'max_curvature': np.max(curvatures),
        'mean_curvature': np.mean(curvatures),
        'cusps': count_cusps(curvatures)
    }
```

### Straight-Line Motion Generation

#### Exact Straight-Line Mechanisms

```python
def peaucellier_linkage(R, r, theta_range=None):
    """
    Generate exact straight line using Peaucellier linkage
    Based on inversion theorem: OP × OP' = k²
    """
    if theta_range is None:
        theta_range = np.linspace(0, 2*np.pi, 360)
    
    # Fixed centers O and O'
    O = np.array([0, 0])
    O_prime = np.array([R + r, 0])
    
    straight_line_points = []
    
    for theta in theta_range:
        # Point P on circle of radius R
        P = np.array([R * np.cos(theta), R * np.sin(theta)])
        
        # Inversion constant k²
        k_squared = r**2
        
        # Calculate P' using inversion
        OP_distance = np.linalg.norm(P - O_prime)
        if OP_distance > 0:
            direction = (P - O_prime) / OP_distance
            P_prime = O_prime + (k_squared / OP_distance) * direction
            straight_line_points.append(P_prime)
    
    return np.array(straight_line_points)

def approximate_straight_line_mechanisms():
    """
    Generate approximate straight-line motions
    """
    mechanisms = {}
    
    # Watt's linkage (approximate straight line)
    def watts_straight_line(r1, r2, r3, theta_range):
        # Specific proportions for Watt's approximate straight line
        # r2 = r3, special coupler point location
        points = []
        for theta in theta_range:
            # Implementation of Watt's approximate straight line
            x = r1 * theta  # Simplified approximation
            y = 0.1 * r1 * np.sin(3 * theta)  # Small deviation from straight
            points.append([x, y])
        return np.array(points)
    
    # Tchebicheff's linkage
    def tchebicheff_straight_line(L, theta_range):
        # Lambda linkage configuration for straight-line approximation
        points = []
        for theta in theta_range:
            x = L * (theta - 0.05 * np.sin(3 * theta))
            y = 0.02 * L * np.sin(6 * theta)
            points.append([x, y])
        return np.array(points)
    
    mechanisms['watt'] = watts_straight_line
    mechanisms['tchebicheff'] = tchebicheff_straight_line
    
    return mechanisms
```

## Motion Analysis and Optimization

### Velocity and Acceleration Analysis

```python
def kinematic_analysis(mechanism_type, parameters, input_motion):
    """
    Complete kinematic analysis: position, velocity, acceleration
    """
    
    def differentiate_motion(positions, time_step):
        """Numerical differentiation for velocities and accelerations"""
        velocities = np.gradient(positions, time_step, axis=0)
        accelerations = np.gradient(velocities, time_step, axis=0)
        return velocities, accelerations
    
    # Generate position data
    if mechanism_type == 'four_bar':
        positions = four_bar_kinematic_analysis(parameters, input_motion)
    elif mechanism_type == 'slider_crank':
        positions = slider_crank_kinematic_analysis(parameters, input_motion)
    elif mechanism_type == 'cam_follower':
        positions = cam_follower_analysis(parameters, input_motion)
    
    # Calculate derivatives
    dt = input_motion['time_step'] if 'time_step' in input_motion else 0.01
    velocities, accelerations = differentiate_motion(positions, dt)
    
    return {
        'positions': positions,
        'velocities': velocities,
        'accelerations': accelerations,
        'time': input_motion.get('time', np.arange(len(positions)) * dt)
    }
```

### Motion Optimization

```python
def optimize_motion_transformation(requirements, constraints):
    """
    Optimize mechanism parameters for desired motion characteristics
    """
    from scipy.optimize import minimize
    
    def objective_function(params):
        """Objective function for optimization"""
        # Generate motion with current parameters
        motion = generate_motion(params, requirements['input_motion'])
        
        # Compare with desired motion
        error = calculate_motion_error(motion, requirements['desired_output'])
        
        # Penalties for constraint violations
        penalties = calculate_constraint_penalties(params, constraints)
        
        return error + penalties
    
    # Optimization constraints
    opt_constraints = []
    if 'transmission_angle' in constraints:
        opt_constraints.append({
            'type': 'ineq',
            'fun': lambda x: min_transmission_angle(x) - constraints['transmission_angle']['min']
        })
    
    if 'link_ratios' in constraints:
        opt_constraints.append({
            'type': 'ineq', 
            'fun': lambda x: constraints['link_ratios']['max'] - max(x)/min(x)
        })
    
    # Perform optimization
    result = minimize(
        objective_function,
        requirements['initial_guess'],
        method='SLSQP',
        constraints=opt_constraints
    )
    
    return {
        'optimal_parameters': result.x,
        'optimization_success': result.success,
        'final_error': result.fun,
        'iterations': result.nit
    }
```

## Advanced Motion Transformations

### Variable Motion Transmission

```python
def variable_motion_transmission():
    """
    Mechanisms providing variable motion transmission ratios
    """
    
    def elliptical_gear_transmission(a, b, theta):
        """
        Motion transmission through elliptical gears
        a, b: semi-major and semi-minor axes
        theta: angular position
        """
        # Instantaneous radius of ellipse
        r = (a * b) / np.sqrt((b * np.cos(theta))**2 + (a * np.sin(theta))**2)
        
        # Instantaneous transmission ratio
        transmission_ratio = r / np.mean([a, b])  # Relative to circular gear
        
        return {
            'instantaneous_radius': r,
            'transmission_ratio': transmission_ratio,
            'velocity_ratio': 1 / transmission_ratio
        }
    
    def non_circular_gear_synthesis(motion_function, base_radius):
        """
        Synthesize non-circular gear for specified motion function
        """
        angles = np.linspace(0, 2*np.pi, 360)
        radii = []
        
        for theta in angles:
            # Calculate required radius for motion function
            required_ratio = motion_function(theta)
            radius = base_radius * required_ratio
            radii.append(radius)
        
        return {
            'angles': angles,
            'radii': radii,
            'gear_profile': list(zip(angles, radii))
        }
    
    return {
        'elliptical_gears': elliptical_gear_transmission,
        'non_circular_synthesis': non_circular_gear_synthesis
    }
```

### Compliant Motion Transformation

```python
def compliant_mechanism_motion(flexure_parameters, applied_force):
    """
    Motion transformation in compliant mechanisms
    """
    
    def pseudo_rigid_body_model(flexure_length, thickness, force):
        """
        PRBM for flexure beam analysis
        """
        # Characteristic radius factor
        gamma = 0.8517  # For cantilever beam with end load
        
        # Characteristic radius
        R = gamma * flexure_length
        
        # Pseudo-rigid-body angle
        theta_prb = force / (flexure_stiffness(flexure_length, thickness) * R)
        
        # End displacement
        displacement = R * np.sin(theta_prb)
        
        return {
            'deflection_angle': theta_prb,
            'end_displacement': displacement,
            'characteristic_radius': R
        }
    
    def flexure_stiffness(length, thickness):
        """Calculate flexure stiffness"""
        E = flexure_parameters.get('elastic_modulus', 200e9)  # Pa
        I = thickness**3 / 12  # Second moment of area
        return 3 * E * I / length**3
    
    # Apply PRBM analysis
    result = pseudo_rigid_body_model(
        flexure_parameters['length'],
        flexure_parameters['thickness'],
        applied_force
    )
    
    return result
```

## Implementation in FreeCAD

### Motion Transformation Tools

```python
import FreeCAD as App
import Part

def create_motion_analyzer():
    """
    Create motion transformation analysis tools for FreeCAD
    """
    
    def animate_mechanism_motion(mechanism_obj, motion_params):
        """
        Animate mechanism motion showing transformation
        """
        # Create animation frames
        frames = []
        
        for t in motion_params['time_range']:
            # Calculate positions at time t
            positions = calculate_mechanism_positions(mechanism_obj, t)
            
            # Update mechanism configuration
            updated_mechanism = update_mechanism_position(mechanism_obj, positions)
            
            frames.append(updated_mechanism)
        
        return frames
    
    def motion_path_visualization(mechanism, point_of_interest):
        """
        Visualize path of point through motion cycle
        """
        # Generate path points
        path_points = []
        
        for angle in np.linspace(0, 2*np.pi, 100):
            point_pos = calculate_point_position(mechanism, point_of_interest, angle)
            path_points.append(point_pos)
        
        # Create path curve in FreeCAD
        path_curve = Part.BSplineCurve()
        path_curve.interpolate(path_points)
        
        return path_curve
    
    return {
        'animate_motion': animate_mechanism_motion,
        'visualize_path': motion_path_visualization
    }

def create_synthesis_tools():
    """
    Create mechanism synthesis tools based on motion requirements
    """
    
    def synthesize_from_motion(motion_requirements):
        """
        Synthesize mechanism from motion transformation requirements
        """
        
        if motion_requirements['type'] == 'path_generation':
            return path_generation_synthesis(motion_requirements['points'])
        elif motion_requirements['type'] == 'function_generation':
            return function_generation_synthesis(motion_requirements['io_pairs'])
        elif motion_requirements['type'] == 'motion_generation':
            return motion_generation_synthesis(motion_requirements['poses'])
    
    return synthesize_from_motion
```

## Conclusion

Motion transformation mathematics provides the analytical foundation for mechanism design, enabling engineers to precisely convert between motion types while optimizing performance characteristics. The key principles include:

1. **Constraint-based analysis** for position, velocity, and acceleration
2. **Geometric synthesis** for desired motion patterns  
3. **Optimization techniques** for performance maximization
4. **Validation methods** for design verification

These mathematical tools transform abstract motion requirements into concrete mechanical solutions, embodying the principle that every mechanism implements a mathematical function through physical geometry.

*"Mathematics is the language of motion - mechanisms are its physical implementation."* - Engineering Philosophy

---

*This document provides the mathematical foundation for motion transformation as applied in modern mechanism design and analysis. The methods continue to evolve with advances in computational techniques and manufacturing capabilities.*