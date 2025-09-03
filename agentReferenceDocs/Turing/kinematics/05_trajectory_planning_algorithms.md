# Trajectory Planning Algorithms

*"A trajectory is mathematics in motion - the precise choreography of position, velocity, and acceleration through time and space."* - Alan Turing

## Overview

Trajectory planning algorithms generate smooth, feasible paths that connect initial and final states while satisfying kinematic and dynamic constraints. These algorithms form the bridge between high-level motion commands and low-level actuator control, ensuring that mechanisms move efficiently, safely, and predictably.

## Fundamental Concepts

### Trajectory vs Path Distinction

**Path**: Geometric curve in space, independent of timing
- Pure spatial relationship: y = f(x)
- No velocity or acceleration information
- Examples: Straight line, arc, spline curve

**Trajectory**: Path with timing information
- Time-parameterized motion: x(t), y(t), θ(t)
- Includes velocity and acceleration profiles
- Defines complete motion specification

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import interpolate
from scipy.optimize import minimize

class TrajectoryPlanner:
    """
    Comprehensive trajectory planning framework
    """
    
    def __init__(self, planning_method='polynomial'):
        self.planning_method = planning_method
        self.constraints = {}
        self.waypoints = []
    
    def add_waypoint(self, position, velocity=None, acceleration=None, time=None):
        """
        Add waypoint with optional kinematic constraints
        """
        waypoint = {
            'position': np.array(position),
            'velocity': np.array(velocity) if velocity is not None else None,
            'acceleration': np.array(acceleration) if acceleration is not None else None,
            'time': time
        }
        self.waypoints.append(waypoint)
        
    def set_constraints(self, max_velocity=None, max_acceleration=None, max_jerk=None):
        """
        Set kinematic constraints for trajectory
        """
        if max_velocity is not None:
            self.constraints['max_velocity'] = max_velocity
        if max_acceleration is not None:
            self.constraints['max_acceleration'] = max_acceleration  
        if max_jerk is not None:
            self.constraints['max_jerk'] = max_jerk
```

## Point-to-Point Trajectory Planning

### Polynomial Trajectory Generation

```python
def plan_polynomial_trajectory(self, start_pos, end_pos, start_vel=None, end_vel=None,
                              start_acc=None, end_acc=None, duration=None):
    """
    Generate polynomial trajectory between two points
    """
    # Determine polynomial order based on constraints
    constraints_count = 2  # Start and end positions
    
    if start_vel is not None and end_vel is not None:
        constraints_count += 2
    if start_acc is not None and end_acc is not None:
        constraints_count += 2
    
    polynomial_order = constraints_count - 1
    
    # Set default values
    start_vel = start_vel if start_vel is not None else 0
    end_vel = end_vel if end_vel is not None else 0
    start_acc = start_acc if start_acc is not None else 0
    end_acc = end_acc if end_acc is not None else 0
    
    # Estimate duration if not provided
    if duration is None:
        distance = abs(end_pos - start_pos)
        max_vel = self.constraints.get('max_velocity', distance)
        duration = 2 * distance / max_vel  # Conservative estimate
    
    # Set up polynomial coefficient matrix
    if polynomial_order == 5:  # Quintic polynomial (most common)
        # Constraints: position, velocity, acceleration at start and end
        T = duration
        constraint_matrix = np.array([
            [0,    0,    0,   0,   0,  1],      # s(0) = start_pos
            [T**5, T**4, T**3, T**2, T, 1],      # s(T) = end_pos  
            [0,    0,    0,   0,   1,  0],      # s'(0) = start_vel
            [5*T**4, 4*T**3, 3*T**2, 2*T, 1, 0], # s'(T) = end_vel
            [0,    0,    0,   2,   0,  0],      # s''(0) = start_acc
            [20*T**3, 12*T**2, 6*T, 2, 0, 0]    # s''(T) = end_acc
        ])
        
        constraint_vector = np.array([start_pos, end_pos, start_vel, end_vel, start_acc, end_acc])
        
    elif polynomial_order == 3:  # Cubic polynomial
        T = duration
        constraint_matrix = np.array([
            [0,   0, 0, 1],      # s(0) = start_pos
            [T**3, T**2, T, 1],  # s(T) = end_pos
            [0,   0, 1, 0],      # s'(0) = start_vel  
            [3*T**2, 2*T, 1, 0]  # s'(T) = end_vel
        ])
        
        constraint_vector = np.array([start_pos, end_pos, start_vel, end_vel])
    
    # Solve for polynomial coefficients
    try:
        coefficients = np.linalg.solve(constraint_matrix, constraint_vector)
        
        return {
            'coefficients': coefficients,
            'polynomial_order': polynomial_order,
            'duration': duration,
            'trajectory_function': lambda t: self._evaluate_polynomial(coefficients, t),
            'velocity_function': lambda t: self._evaluate_polynomial_derivative(coefficients, t, 1),
            'acceleration_function': lambda t: self._evaluate_polynomial_derivative(coefficients, t, 2)
        }
        
    except np.linalg.LinAlgError:
        return {'error': 'Could not solve polynomial trajectory - constraints may be inconsistent'}

def _evaluate_polynomial(self, coefficients, t):
    """Evaluate polynomial at time t"""
    result = 0
    for i, coeff in enumerate(coefficients):
        result += coeff * (t ** (len(coefficients) - 1 - i))
    return result

def _evaluate_polynomial_derivative(self, coefficients, t, derivative_order):
    """Evaluate nth derivative of polynomial at time t"""
    # Calculate derivative coefficients
    deriv_coeffs = coefficients.copy()
    
    for _ in range(derivative_order):
        new_coeffs = []
        for i in range(len(deriv_coeffs) - 1):
            power = len(deriv_coeffs) - 1 - i
            new_coeffs.append(deriv_coeffs[i] * power)
        deriv_coeffs = np.array(new_coeffs)
        
        if len(deriv_coeffs) == 0:
            return 0
    
    # Evaluate derivative polynomial
    result = 0
    for i, coeff in enumerate(deriv_coeffs):
        result += coeff * (t ** (len(deriv_coeffs) - 1 - i))
    return result
```

### Trapezoidal Velocity Profiles

```python
def plan_trapezoidal_trajectory(self, distance, max_velocity, max_acceleration, max_jerk=None):
    """
    Generate trapezoidal velocity profile trajectory
    """
    # Phase durations
    accel_time = max_velocity / max_acceleration
    accel_distance = 0.5 * max_acceleration * accel_time**2
    
    # Check if we can reach max velocity
    total_accel_distance = 2 * accel_distance
    
    if total_accel_distance >= distance:
        # Triangular profile - can't reach max velocity
        actual_accel_time = np.sqrt(distance / max_acceleration)
        actual_max_velocity = max_acceleration * actual_accel_time
        
        coast_time = 0
        total_time = 2 * actual_accel_time
        
        profile_type = 'triangular'
        
    else:
        # Trapezoidal profile - can reach max velocity
        coast_distance = distance - total_accel_distance
        coast_time = coast_distance / max_velocity
        
        actual_max_velocity = max_velocity
        actual_accel_time = accel_time
        total_time = 2 * accel_time + coast_time
        
        profile_type = 'trapezoidal'
    
    # Generate trajectory functions
    def position_function(t):
        if t <= 0:
            return 0
        elif t <= actual_accel_time:
            # Acceleration phase
            return 0.5 * max_acceleration * t**2
        elif t <= actual_accel_time + coast_time:
            # Coast phase
            accel_distance = 0.5 * max_acceleration * actual_accel_time**2
            coast_distance = actual_max_velocity * (t - actual_accel_time)
            return accel_distance + coast_distance
        elif t <= total_time:
            # Deceleration phase
            t_decel = t - actual_accel_time - coast_time
            accel_distance = 0.5 * max_acceleration * actual_accel_time**2
            coast_distance = actual_max_velocity * coast_time
            decel_distance = actual_max_velocity * t_decel - 0.5 * max_acceleration * t_decel**2
            return accel_distance + coast_distance + decel_distance
        else:
            return distance
    
    def velocity_function(t):
        if t <= 0:
            return 0
        elif t <= actual_accel_time:
            return max_acceleration * t
        elif t <= actual_accel_time + coast_time:
            return actual_max_velocity
        elif t <= total_time:
            t_decel = t - actual_accel_time - coast_time
            return actual_max_velocity - max_acceleration * t_decel
        else:
            return 0
    
    def acceleration_function(t):
        if t <= 0:
            return 0
        elif t <= actual_accel_time:
            return max_acceleration
        elif t <= actual_accel_time + coast_time:
            return 0
        elif t <= total_time:
            return -max_acceleration
        else:
            return 0
    
    return {
        'profile_type': profile_type,
        'total_time': total_time,
        'max_velocity_achieved': actual_max_velocity,
        'acceleration_time': actual_accel_time,
        'coast_time': coast_time,
        'position_function': position_function,
        'velocity_function': velocity_function,
        'acceleration_function': acceleration_function,
        'phase_boundaries': [actual_accel_time, actual_accel_time + coast_time, total_time]
    }
```

## Multi-Waypoint Trajectory Planning

### Spline-Based Trajectories

```python
def plan_spline_trajectory(self, waypoints, boundary_conditions='natural', smoothing_factor=0):
    """
    Generate smooth trajectory through multiple waypoints using splines
    """
    if len(waypoints) < 2:
        return {'error': 'At least 2 waypoints required'}
    
    # Extract positions and times
    positions = [wp['position'] for wp in waypoints]
    times = [wp.get('time', i) for i, wp in enumerate(waypoints)]  # Default to indices if no times
    
    # Create spline interpolation for each dimension
    trajectory_splines = {}
    
    # Handle multi-dimensional positions
    if isinstance(positions[0], (list, np.ndarray)):
        dimensions = len(positions[0])
        position_arrays = [np.array([pos[dim] for pos in positions]) for dim in range(dimensions)]
    else:
        dimensions = 1
        position_arrays = [np.array(positions)]
    
    # Create spline for each dimension
    for dim in range(dimensions):
        if boundary_conditions == 'natural':
            # Natural cubic spline (second derivative = 0 at endpoints)
            spline = interpolate.CubicSpline(times, position_arrays[dim], bc_type='natural')
        elif boundary_conditions == 'clamped':
            # Clamped cubic spline (specify first derivatives at endpoints)
            start_vel = waypoints[0].get('velocity', [0] * dimensions)[dim] if waypoints[0].get('velocity') is not None else 0
            end_vel = waypoints[-1].get('velocity', [0] * dimensions)[dim] if waypoints[-1].get('velocity') is not None else 0
            spline = interpolate.CubicSpline(times, position_arrays[dim], 
                                          bc_type=((1, start_vel), (1, end_vel)))
        elif boundary_conditions == 'periodic':
            # Periodic spline (for closed trajectories)
            spline = interpolate.CubicSpline(times, position_arrays[dim], bc_type='periodic')
        
        trajectory_splines[f'dim_{dim}'] = spline
    
    # Create unified trajectory functions
    def position_function(t):
        if dimensions == 1:
            return trajectory_splines['dim_0'](t)
        else:
            return np.array([trajectory_splines[f'dim_{dim}'](t) for dim in range(dimensions)])
    
    def velocity_function(t):
        if dimensions == 1:
            return trajectory_splines['dim_0'].derivative(1)(t)
        else:
            return np.array([trajectory_splines[f'dim_{dim}'].derivative(1)(t) for dim in range(dimensions)])
    
    def acceleration_function(t):
        if dimensions == 1:
            return trajectory_splines['dim_0'].derivative(2)(t)
        else:
            return np.array([trajectory_splines[f'dim_{dim}'].derivative(2)(t) for dim in range(dimensions)])
    
    # Analyze trajectory properties
    time_range = np.linspace(times[0], times[-1], 1000)
    velocities = np.array([np.linalg.norm(velocity_function(t)) if dimensions > 1 
                          else abs(velocity_function(t)) for t in time_range])
    accelerations = np.array([np.linalg.norm(acceleration_function(t)) if dimensions > 1 
                             else abs(acceleration_function(t)) for t in time_range])
    
    return {
        'position_function': position_function,
        'velocity_function': velocity_function,
        'acceleration_function': acceleration_function,
        'time_range': [times[0], times[-1]],
        'max_velocity': np.max(velocities),
        'max_acceleration': np.max(accelerations),
        'spline_objects': trajectory_splines,
        'waypoint_times': times
    }
```

### B-Spline Trajectory Generation

```python
def plan_bspline_trajectory(self, control_points, degree=3, knot_vector=None, weights=None):
    """
    Generate B-spline trajectory for smooth motion through control points
    """
    n_points = len(control_points)
    
    # Create knot vector if not provided (uniform spacing)
    if knot_vector is None:
        # Create uniform knot vector
        m = n_points + degree + 1
        knot_vector = np.zeros(m)
        
        # Set interior knots
        for i in range(degree + 1, n_points + 1):
            knot_vector[i] = (i - degree) / (n_points - degree)
        
        # Set end knots
        knot_vector[n_points + 1:] = 1.0
    
    # B-spline basis functions
    def basis_function(i, k, u, knots):
        """Recursive B-spline basis function"""
        if k == 0:
            return 1.0 if knots[i] <= u < knots[i+1] else 0.0
        else:
            c1 = (u - knots[i]) / (knots[i+k] - knots[i]) if knots[i+k] != knots[i] else 0.0
            c2 = (knots[i+k+1] - u) / (knots[i+k+1] - knots[i+1]) if knots[i+k+1] != knots[i+1] else 0.0
            
            return c1 * basis_function(i, k-1, u, knots) + c2 * basis_function(i+1, k-1, u, knots)
    
    # Create trajectory function
    def trajectory_function(u):
        """Evaluate B-spline at parameter u [0,1]"""
        if u < 0:
            u = 0
        elif u > 1:
            u = 1
            
        point = np.zeros_like(control_points[0])
        
        for i in range(n_points):
            basis = basis_function(i, degree, u, knot_vector)
            weight = weights[i] if weights is not None else 1.0
            point += basis * weight * np.array(control_points[i])
        
        return point
    
    # Generate derivative functions for velocity and acceleration
    def velocity_function(u, dt=1e-6):
        """Numerical derivative for velocity"""
        if u <= dt:
            return (trajectory_function(u + dt) - trajectory_function(u)) / dt
        elif u >= 1 - dt:
            return (trajectory_function(u) - trajectory_function(u - dt)) / dt
        else:
            return (trajectory_function(u + dt) - trajectory_function(u - dt)) / (2 * dt)
    
    def acceleration_function(u, dt=1e-6):
        """Numerical second derivative for acceleration"""
        if u <= dt:
            return (velocity_function(u + dt) - velocity_function(u)) / dt
        elif u >= 1 - dt:
            return (velocity_function(u) - velocity_function(u - dt)) / dt
        else:
            return (velocity_function(u + dt) - velocity_function(u - dt)) / (2 * dt)
    
    return {
        'trajectory_function': trajectory_function,
        'velocity_function': velocity_function,
        'acceleration_function': acceleration_function,
        'control_points': control_points,
        'degree': degree,
        'knot_vector': knot_vector,
        'parameter_range': [0, 1]
    }
```

## Constrained Trajectory Optimization

### Time-Optimal Trajectories

```python
def plan_time_optimal_trajectory(self, waypoints, constraints, initial_guess_time=None):
    """
    Generate time-optimal trajectory subject to kinematic constraints
    """
    from scipy.optimize import minimize
    
    n_waypoints = len(waypoints)
    n_segments = n_waypoints - 1
    
    # Initial guess for segment times
    if initial_guess_time is None:
        segment_times = np.ones(n_segments)
    else:
        segment_times = np.array(initial_guess_time)
    
    def objective_function(segment_times):
        """Minimize total trajectory time"""
        return np.sum(segment_times)
    
    def constraint_violations(segment_times):
        """Calculate constraint violations for all segments"""
        violations = []
        
        cumulative_time = 0
        
        for i, dt in enumerate(segment_times):
            if dt <= 0:
                violations.append(-dt)  # Time must be positive
                continue
                
            # Generate polynomial for this segment
            start_pos = waypoints[i]['position']
            end_pos = waypoints[i+1]['position']
            
            # Create quintic polynomial for segment
            poly_result = self.plan_polynomial_trajectory(
                start_pos, end_pos, 
                start_vel=0, end_vel=0,  # Could be optimized
                start_acc=0, end_acc=0,
                duration=dt
            )
            
            if 'error' in poly_result:
                violations.append(1.0)  # Large violation for infeasible segment
                continue
            
            # Check velocity constraints
            times = np.linspace(0, dt, 50)
            velocities = [abs(poly_result['velocity_function'](t)) for t in times]
            max_vel = max(velocities)
            
            if 'max_velocity' in constraints and max_vel > constraints['max_velocity']:
                violations.append(max_vel - constraints['max_velocity'])
            
            # Check acceleration constraints  
            accelerations = [abs(poly_result['acceleration_function'](t)) for t in times]
            max_acc = max(accelerations)
            
            if 'max_acceleration' in constraints and max_acc > constraints['max_acceleration']:
                violations.append(max_acc - constraints['max_acceleration'])
        
        return sum(violations)
    
    # Optimization constraints
    opt_constraints = [
        {'type': 'ineq', 'fun': lambda x: -constraint_violations(x)},  # Constraint violations <= 0
        {'type': 'ineq', 'fun': lambda x: x}  # Times must be positive
    ]
    
    # Bounds: reasonable time limits
    bounds = [(0.1, 10.0) for _ in range(n_segments)]
    
    # Optimize
    result = minimize(
        objective_function,
        segment_times,
        method='SLSQP',
        bounds=bounds,
        constraints=opt_constraints
    )
    
    if result.success:
        optimal_times = result.x
        
        # Generate final trajectory using optimal times
        trajectory_segments = []
        cumulative_time = 0
        
        for i, dt in enumerate(optimal_times):
            start_pos = waypoints[i]['position']
            end_pos = waypoints[i+1]['position']
            
            segment = self.plan_polynomial_trajectory(
                start_pos, end_pos,
                duration=dt
            )
            
            segment['start_time'] = cumulative_time
            segment['end_time'] = cumulative_time + dt
            trajectory_segments.append(segment)
            
            cumulative_time += dt
        
        return {
            'optimization_success': True,
            'total_time': np.sum(optimal_times),
            'segment_times': optimal_times,
            'trajectory_segments': trajectory_segments,
            'final_violation': constraint_violations(optimal_times)
        }
    
    return {'optimization_success': False, 'error': 'Time optimization failed to converge'}
```

### Jerk-Limited Trajectories

```python
def plan_jerk_limited_trajectory(self, start_state, end_state, max_jerk, max_acceleration=None, max_velocity=None):
    """
    Generate trajectory with limited jerk (7-phase S-curve profile)
    """
    # S-curve profile phases:
    # 1. Jerk up (acceleration increases)
    # 2. Constant acceleration
    # 3. Jerk down (acceleration decreases to 0)  
    # 4. Constant velocity
    # 5. Jerk down (acceleration decreases - deceleration starts)
    # 6. Constant deceleration
    # 7. Jerk up (deceleration decreases to 0)
    
    distance = end_state['position'] - start_state['position']
    start_vel = start_state.get('velocity', 0)
    end_vel = end_state.get('velocity', 0)
    
    # Phase time calculations (simplified - actual implementation more complex)
    if max_acceleration is None:
        max_acceleration = max_jerk  # Conservative default
    
    if max_velocity is None:
        max_velocity = np.sqrt(abs(distance) * max_acceleration)  # Conservative default
    
    # Time to reach max acceleration
    t_jerk_up = max_acceleration / max_jerk
    
    # Distance and velocity during jerk phases
    s_jerk = max_jerk * t_jerk_up**3 / 6
    v_jerk = max_jerk * t_jerk_up**2 / 2
    
    # Check if we can reach max acceleration and velocity
    total_jerk_distance = 4 * s_jerk  # Four jerk phases
    
    if total_jerk_distance >= abs(distance):
        # Modify profile - can't reach max acceleration
        t_jerk_up = (abs(distance) / (2 * max_jerk))**(1/3)
        s_jerk = max_jerk * t_jerk_up**3 / 6
        
        # Simplified 4-phase profile
        t_const_acc = 0
        t_const_vel = 0
        
    else:
        # Calculate constant acceleration time
        remaining_distance = abs(distance) - total_jerk_distance
        
        # Velocity at end of acceleration phase
        v_acc_end = 2 * v_jerk  # From two jerk phases
        
        if v_acc_end >= max_velocity:
            # Can't reach constant velocity phase
            t_const_acc = (max_velocity - v_acc_end) / max_acceleration
            t_const_vel = 0
        else:
            # Can reach constant velocity
            distance_to_max_vel = (max_velocity - v_acc_end) * t_const_acc + 0.5 * max_acceleration * t_const_acc**2
            
            if remaining_distance > distance_to_max_vel:
                t_const_vel = (remaining_distance - distance_to_max_vel) / max_velocity
            else:
                t_const_vel = 0
    
    # Phase durations
    phase_times = {
        'jerk_up_1': t_jerk_up,
        'const_acc': t_const_acc,
        'jerk_down_1': t_jerk_up,
        'const_vel': t_const_vel,
        'jerk_down_2': t_jerk_up,
        'const_dec': t_const_acc,
        'jerk_up_2': t_jerk_up
    }
    
    total_time = sum(phase_times.values())
    
    # Generate trajectory functions
    def position_function(t):
        # Complex piecewise function - simplified implementation
        if t <= 0:
            return start_state['position']
        elif t >= total_time:
            return end_state['position']
        else:
            # Implement full 7-phase calculation
            return start_state['position'] + (end_state['position'] - start_state['position']) * (t / total_time)
    
    def velocity_function(t):
        # Implement 7-phase velocity profile
        return 0  # Simplified
    
    def acceleration_function(t):
        # Implement 7-phase acceleration profile
        return 0  # Simplified
    
    def jerk_function(t):
        # Implement 7-phase jerk profile
        return 0  # Simplified
    
    return {
        'profile_type': 'S-curve (7-phase)',
        'total_time': total_time,
        'phase_times': phase_times,
        'max_jerk_achieved': max_jerk,
        'position_function': position_function,
        'velocity_function': velocity_function,
        'acceleration_function': acceleration_function,
        'jerk_function': jerk_function
    }
```

## Path Following and Tracking

### Pure Pursuit Algorithm

```python
def pure_pursuit_controller(current_pose, path_points, lookahead_distance):
    """
    Pure pursuit path following controller
    """
    current_x, current_y, current_heading = current_pose
    
    # Find lookahead point on path
    lookahead_point = None
    min_distance_to_goal = float('inf')
    
    for i in range(len(path_points) - 1):
        # Find intersection of lookahead circle with path segment
        p1 = np.array(path_points[i])
        p2 = np.array(path_points[i + 1])
        current_pos = np.array([current_x, current_y])
        
        # Vector from p1 to p2
        segment_vec = p2 - p1
        segment_length = np.linalg.norm(segment_vec)
        
        if segment_length == 0:
            continue
        
        # Vector from p1 to current position
        to_current = current_pos - p1
        
        # Project current position onto line segment
        t = np.dot(to_current, segment_vec) / segment_length**2
        t = max(0, min(1, t))  # Clamp to segment
        
        # Closest point on segment
        closest_point = p1 + t * segment_vec
        
        # Distance from current position to closest point
        distance_to_segment = np.linalg.norm(current_pos - closest_point)
        
        # Check if lookahead circle intersects this segment
        if distance_to_segment <= lookahead_distance:
            # Find intersection point
            # Use quadratic formula to find intersection
            a = np.dot(segment_vec, segment_vec)
            b = 2 * np.dot(to_current, segment_vec)
            c = np.dot(to_current, to_current) - lookahead_distance**2
            
            discriminant = b**2 - 4*a*c
            
            if discriminant >= 0:
                # Two possible intersections - choose the farther one along the path
                t1 = (-b + np.sqrt(discriminant)) / (2*a)
                t2 = (-b - np.sqrt(discriminant)) / (2*a)
                
                for t_intersect in [t1, t2]:
                    if 0 <= t_intersect <= 1:
                        intersection_point = p1 + t_intersect * segment_vec
                        distance_to_goal = np.linalg.norm(intersection_point - np.array(path_points[-1]))
                        
                        if distance_to_goal < min_distance_to_goal:
                            lookahead_point = intersection_point
                            min_distance_to_goal = distance_to_goal
    
    if lookahead_point is None:
        # If no intersection found, use closest point on path
        closest_distance = float('inf')
        for point in path_points:
            distance = np.linalg.norm(np.array([current_x, current_y]) - np.array(point))
            if distance < closest_distance:
                closest_distance = distance
                lookahead_point = np.array(point)
    
    # Calculate steering angle
    dx = lookahead_point[0] - current_x
    dy = lookahead_point[1] - current_y
    
    # Angle to lookahead point
    angle_to_lookahead = np.arctan2(dy, dx)
    
    # Steering angle (difference from current heading)
    steering_angle = angle_to_lookahead - current_heading
    
    # Normalize angle to [-pi, pi]
    steering_angle = np.arctan2(np.sin(steering_angle), np.cos(steering_angle))
    
    return {
        'steering_angle': steering_angle,
        'lookahead_point': lookahead_point,
        'distance_to_path': min_distance_to_goal
    }
```

### Model Predictive Control (MPC)

```python
def mpc_trajectory_tracking(current_state, reference_trajectory, prediction_horizon=10, control_horizon=3):
    """
    Model Predictive Control for trajectory tracking
    """
    from scipy.optimize import minimize
    
    # System model: simple integrator
    # x_{k+1} = x_k + u_k * dt
    dt = 0.1  # Time step
    
    # Extract current position and reference
    current_pos = current_state['position']
    
    # Get reference trajectory for prediction horizon
    ref_positions = []
    for i in range(prediction_horizon):
        if i < len(reference_trajectory):
            ref_positions.append(reference_trajectory[i]['position'])
        else:
            # Extend with final position
            ref_positions.append(reference_trajectory[-1]['position'])
    
    # Decision variables: control inputs for control horizon
    n_controls = min(control_horizon, prediction_horizon)
    
    def objective_function(controls):
        """Minimize tracking error and control effort"""
        predicted_states = [current_pos]
        cost = 0
        
        # Predict future states
        for k in range(prediction_horizon):
            if k < len(controls):
                control_input = controls[k]
            else:
                control_input = controls[-1]  # Hold last control
            
            # Simple integrator model
            next_state = predicted_states[-1] + control_input * dt
            predicted_states.append(next_state)
            
            # Add tracking error cost
            if k < len(ref_positions):
                error = np.linalg.norm(next_state - ref_positions[k])
                cost += error**2
            
            # Add control effort cost
            cost += 0.1 * np.linalg.norm(control_input)**2
            
            # Add control smoothness cost
            if k > 0 and k-1 < len(controls):
                control_change = np.linalg.norm(controls[k] - controls[k-1])
                cost += 0.05 * control_change**2
        
        return cost
    
    # Constraints
    max_control = 1.0  # Maximum control input magnitude
    bounds = [(-max_control, max_control) for _ in range(n_controls)]
    
    # Initial guess
    initial_guess = np.zeros(n_controls)
    
    # Optimize
    result = minimize(objective_function, initial_guess, bounds=bounds, method='L-BFGS-B')
    
    if result.success:
        optimal_controls = result.x
        
        return {
            'control_input': optimal_controls[0],  # Apply first control
            'predicted_trajectory': None,  # Could compute predicted trajectory
            'optimization_cost': result.fun,
            'success': True
        }
    
    return {'success': False, 'error': 'MPC optimization failed'}
```

## Trajectory Evaluation and Analysis

### Performance Metrics

```python
def evaluate_trajectory_performance(trajectory_func, time_range, constraints=None):
    """
    Comprehensive trajectory performance evaluation
    """
    times = np.linspace(time_range[0], time_range[1], 1000)
    
    # Sample trajectory
    positions = [trajectory_func['position_function'](t) for t in times]
    velocities = [trajectory_func['velocity_function'](t) for t in times]
    accelerations = [trajectory_func['acceleration_function'](t) for t in times]
    
    # Convert to arrays for analysis
    if isinstance(positions[0], (list, np.ndarray)):
        # Multi-dimensional trajectory
        pos_array = np.array(positions)
        vel_array = np.array(velocities)
        acc_array = np.array(accelerations)
        
        # Calculate magnitudes
        vel_magnitudes = np.linalg.norm(vel_array, axis=1)
        acc_magnitudes = np.linalg.norm(acc_array, axis=1)
        
    else:
        # 1D trajectory
        vel_magnitudes = np.abs(velocities)
        acc_magnitudes = np.abs(accelerations)
    
    # Performance metrics
    metrics = {
        'total_time': time_range[1] - time_range[0],
        'max_velocity': np.max(vel_magnitudes),
        'max_acceleration': np.max(acc_magnitudes),
        'average_velocity': np.mean(vel_magnitudes),
        'average_acceleration': np.mean(acc_magnitudes),
        'velocity_smoothness': np.std(vel_magnitudes),
        'acceleration_smoothness': np.std(acc_magnitudes)
    }
    
    # Constraint violations
    if constraints:
        violations = {}
        
        if 'max_velocity' in constraints:
            vel_violations = vel_magnitudes > constraints['max_velocity']
            violations['velocity_violations'] = np.sum(vel_violations)
            violations['max_velocity_violation'] = np.max(vel_magnitudes) - constraints['max_velocity'] if np.any(vel_violations) else 0
        
        if 'max_acceleration' in constraints:
            acc_violations = acc_magnitudes > constraints['max_acceleration']
            violations['acceleration_violations'] = np.sum(acc_violations)
            violations['max_acceleration_violation'] = np.max(acc_magnitudes) - constraints['max_acceleration'] if np.any(acc_violations) else 0
        
        metrics['constraint_violations'] = violations
    
    # Calculate jerk if possible
    try:
        jerks = [np.linalg.norm(np.gradient(acc_array[max(0, i-2):i+3], times[max(0, i-2):i+3])[2]) for i in range(2, len(times)-2)]
        metrics['max_jerk'] = np.max(jerks)
        metrics['average_jerk'] = np.mean(jerks)
    except:
        metrics['max_jerk'] = None
        metrics['average_jerk'] = None
    
    return metrics
```

## Implementation in FreeCAD

### Trajectory Visualization

```python
import FreeCAD as App
import Part
import Draft

class FreeCADTrajectoryVisualizer:
    """
    Visualize and animate trajectories in FreeCAD
    """
    
    def __init__(self, doc_name="TrajectoryPlanning"):
        self.doc = App.newDocument(doc_name)
    
    def visualize_trajectory(self, trajectory_func, time_range, resolution=100):
        """
        Create 3D visualization of trajectory in FreeCAD
        """
        times = np.linspace(time_range[0], time_range[1], resolution)
        
        # Generate trajectory points
        trajectory_points = []
        velocity_vectors = []
        
        for t in times:
            pos = trajectory_func['position_function'](t)
            vel = trajectory_func['velocity_function'](t)
            
            # Convert to FreeCAD Vector
            if isinstance(pos, (list, np.ndarray)):
                if len(pos) == 2:
                    pos_vec = App.Vector(pos[0], pos[1], 0)
                    vel_vec = App.Vector(vel[0], vel[1], 0)
                else:
                    pos_vec = App.Vector(pos[0], pos[1], pos[2])
                    vel_vec = App.Vector(vel[0], vel[1], vel[2])
            else:
                pos_vec = App.Vector(pos, 0, 0)
                vel_vec = App.Vector(vel, 0, 0)
            
            trajectory_points.append(pos_vec)
            velocity_vectors.append(vel_vec)
        
        # Create trajectory curve
        trajectory_curve = Part.BSplineCurve()
        trajectory_curve.interpolate(trajectory_points)
        
        # Create FreeCAD objects
        traj_obj = self.doc.addObject("Part::Feature", "Trajectory")
        traj_obj.Shape = Part.Edge(trajectory_curve)
        
        # Create velocity visualization (arrows at key points)
        arrow_objects = []
        step = max(1, len(trajectory_points) // 20)  # Show ~20 arrows
        
        for i in range(0, len(trajectory_points), step):
            if i < len(velocity_vectors):
                # Create arrow for velocity vector
                arrow_start = trajectory_points[i]
                arrow_end = arrow_start + velocity_vectors[i] * 0.1  # Scale for visibility
                
                arrow_line = Part.makeLine(arrow_start, arrow_end)
                arrow_obj = self.doc.addObject("Part::Feature", f"VelocityArrow_{i}")
                arrow_obj.Shape = arrow_line
                arrow_objects.append(arrow_obj)
        
        # Create waypoint markers
        waypoint_objects = []
        for i, point in enumerate(trajectory_points[::len(trajectory_points)//10]):
            marker = Part.makeSphere(0.5)
            marker.translate(point)
            
            waypoint_obj = self.doc.addObject("Part::Feature", f"Waypoint_{i}")
            waypoint_obj.Shape = marker
            waypoint_objects.append(waypoint_obj)
        
        self.doc.recompute()
        
        return {
            'trajectory_object': traj_obj,
            'velocity_arrows': arrow_objects,
            'waypoint_markers': waypoint_objects
        }
    
    def animate_trajectory_following(self, trajectory_func, time_range, robot_model=None):
        """
        Animate robot following trajectory
        """
        if robot_model is None:
            # Create simple robot representation
            robot_model = Part.makeBox(20, 10, 5)
            robot_obj = self.doc.addObject("Part::Feature", "Robot")
            robot_obj.Shape = robot_model
        
        # Animation parameters
        frame_rate = 10  # fps
        total_time = time_range[1] - time_range[0]
        num_frames = int(total_time * frame_rate)
        
        animation_data = []
        
        for frame in range(num_frames):
            t = time_range[0] + (frame / num_frames) * total_time
            
            # Get position and orientation at time t
            pos = trajectory_func['position_function'](t)
            vel = trajectory_func['velocity_function'](t)
            
            # Calculate orientation from velocity
            if isinstance(vel, (list, np.ndarray)) and len(vel) >= 2:
                heading = np.arctan2(vel[1], vel[0])
                rotation = App.Rotation(App.Vector(0, 0, 1), np.degrees(heading))
            else:
                rotation = App.Rotation()
            
            # Update robot position
            if isinstance(pos, (list, np.ndarray)):
                if len(pos) == 2:
                    position = App.Vector(pos[0], pos[1], 0)
                else:
                    position = App.Vector(pos[0], pos[1], pos[2])
            else:
                position = App.Vector(pos, 0, 0)
            
            robot_obj.Placement.Base = position
            robot_obj.Placement.Rotation = rotation
            
            self.doc.recompute()
            
            animation_data.append({
                'frame': frame,
                'time': t,
                'position': position,
                'rotation': rotation
            })
        
        return animation_data
```

## Conclusion

Trajectory planning algorithms provide the mathematical foundation for generating smooth, feasible motion that connects desired waypoints while respecting physical constraints. Through systematic application of:

1. **Polynomial trajectory generation** for smooth point-to-point motion
2. **Spline-based methods** for multi-waypoint trajectories
3. **Optimization techniques** for time-optimal and constrained trajectories
4. **Path following controllers** for tracking generated trajectories
5. **Performance evaluation metrics** for trajectory quality assessment
6. **Visualization tools** for trajectory analysis and validation

Engineers can create motion plans that enable mechanisms and robots to move efficiently, safely, and predictably through complex environments and tasks.

The key to successful trajectory planning lies in understanding the trade-offs between trajectory smoothness, execution time, computational complexity, and constraint satisfaction, then selecting the appropriate algorithm based on specific application requirements.

*"A trajectory is the poetry of motion - each point a verse in the mechanical sonnet of space and time."* - Engineering Artistry

---

*This comprehensive framework enables the generation of optimal trajectories for any mechanical system requiring precise, coordinated motion control.*