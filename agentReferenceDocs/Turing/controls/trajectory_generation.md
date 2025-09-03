# Trajectory Generation: Programming Motion Through Time

*"A trajectory is a motion poem written in the language of mathematics - each point precisely timed, each velocity carefully crafted, each acceleration bounded by physical reality."* - Alan Turing

## Overview

Trajectory generation is the art and science of planning robot motion through time. It transforms a desired path (spatial) into a trajectory (spatial + temporal), ensuring smooth motion while respecting kinematic and dynamic constraints. This is where kinematics meets control - the bridge between intention and actuation.

## Mathematical Framework

### Trajectory Representation
A trajectory is a time-parameterized path:
```
q(t): [0, T] → Q
```
Where Q is the configuration space and T is the motion duration.

For each degree of freedom:
```
q_i(t) = position as function of time
q̇_i(t) = velocity as function of time  
q̈_i(t) = acceleration as function of time
q⃛_i(t) = jerk as function of time (for smooth motion)
```

### Constraints Classification

#### Kinematic Constraints
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import minimize

class TrajectoryConstraints:
    def __init__(self):
        self.joint_limits = []          # [min, max] for each joint
        self.velocity_limits = []       # Max |q̇_i|
        self.acceleration_limits = []   # Max |q̈_i|
        self.jerk_limits = []          # Max |q⃛_i| for smoothness
        
    def add_joint(self, position_limit, velocity_limit, acceleration_limit, jerk_limit=None):
        """Add constraints for one joint"""
        self.joint_limits.append(position_limit)
        self.velocity_limits.append(velocity_limit)
        self.acceleration_limits.append(acceleration_limit)
        if jerk_limit is not None:
            self.jerk_limits.append(jerk_limit)
    
    def validate_trajectory(self, q, q_dot, q_ddot, q_dddot=None):
        """Check if trajectory satisfies all constraints"""
        violations = []
        
        for i in range(len(self.joint_limits)):
            # Position limits
            if np.any(q[i] < self.joint_limits[i][0]) or np.any(q[i] > self.joint_limits[i][1]):
                violations.append(f"Joint {i} position limit violated")
            
            # Velocity limits
            if np.any(np.abs(q_dot[i]) > self.velocity_limits[i]):
                violations.append(f"Joint {i} velocity limit violated")
                
            # Acceleration limits
            if np.any(np.abs(q_ddot[i]) > self.acceleration_limits[i]):
                violations.append(f"Joint {i} acceleration limit violated")
                
            # Jerk limits (if specified)
            if q_dddot is not None and i < len(self.jerk_limits):
                if np.any(np.abs(q_dddot[i]) > self.jerk_limits[i]):
                    violations.append(f"Joint {i} jerk limit violated")
        
        return violations
```

## Polynomial Trajectory Generation

### Cubic Polynomials (Position + Velocity Boundary Conditions)
```python
class CubicTrajectory:
    def __init__(self, q0, qf, v0, vf, T):
        """
        Generate cubic polynomial trajectory
        
        Args:
            q0, qf: Initial and final positions
            v0, vf: Initial and final velocities  
            T: Motion duration
        """
        self.T = T
        self.coefficients = self._calculate_coefficients(q0, qf, v0, vf, T)
    
    def _calculate_coefficients(self, q0, qf, v0, vf, T):
        """Calculate polynomial coefficients a0, a1, a2, a3"""
        # q(t) = a0 + a1*t + a2*t² + a3*t³
        # Boundary conditions:
        # q(0) = q0, q(T) = qf, q̇(0) = v0, q̇(T) = vf
        
        a0 = q0
        a1 = v0
        a2 = (3*(qf - q0) - T*(2*v0 + vf)) / T**2
        a3 = (2*(q0 - qf) + T*(v0 + vf)) / T**3
        
        return np.array([a0, a1, a2, a3])
    
    def position(self, t):
        """Calculate position at time t"""
        t = np.clip(t, 0, self.T)
        a0, a1, a2, a3 = self.coefficients
        return a0 + a1*t + a2*t**2 + a3*t**3
    
    def velocity(self, t):
        """Calculate velocity at time t"""
        t = np.clip(t, 0, self.T)
        a0, a1, a2, a3 = self.coefficients
        return a1 + 2*a2*t + 3*a3*t**2
    
    def acceleration(self, t):
        """Calculate acceleration at time t"""
        t = np.clip(t, 0, self.T)
        a0, a1, a2, a3 = self.coefficients
        return 2*a2 + 6*a3*t
    
    def plot(self, n_points=100):
        """Plot trajectory profiles"""
        t = np.linspace(0, self.T, n_points)
        pos = [self.position(ti) for ti in t]
        vel = [self.velocity(ti) for ti in t]
        acc = [self.acceleration(ti) for ti in t]
        
        fig, (ax1, ax2, ax3) = plt.subplots(3, 1, figsize=(10, 8))
        
        ax1.plot(t, pos, 'b-', linewidth=2, label='Position')
        ax1.set_ylabel('Position')
        ax1.grid(True)
        
        ax2.plot(t, vel, 'r-', linewidth=2, label='Velocity')
        ax2.set_ylabel('Velocity')
        ax2.grid(True)
        
        ax3.plot(t, acc, 'g-', linewidth=2, label='Acceleration')
        ax3.set_ylabel('Acceleration')
        ax3.set_xlabel('Time (s)')
        ax3.grid(True)
        
        plt.tight_layout()
        plt.show()
```

### Quintic Polynomials (Full Boundary Conditions)
```python
class QuinticTrajectory:
    def __init__(self, q0, qf, v0, vf, a0, af, T):
        """
        Generate quintic polynomial trajectory
        Specifies position, velocity, and acceleration at both endpoints
        """
        self.T = T
        self.coefficients = self._calculate_coefficients(q0, qf, v0, vf, a0, af, T)
    
    def _calculate_coefficients(self, q0, qf, v0, vf, a0, af, T):
        """Calculate polynomial coefficients a0 through a5"""
        # q(t) = a0 + a1*t + a2*t² + a3*t³ + a4*t⁴ + a5*t⁵
        
        # Boundary conditions matrix
        A = np.array([
            [1, 0, 0, 0, 0, 0],           # q(0) = q0
            [1, T, T**2, T**3, T**4, T**5], # q(T) = qf
            [0, 1, 0, 0, 0, 0],           # q̇(0) = v0
            [0, 1, 2*T, 3*T**2, 4*T**3, 5*T**4], # q̇(T) = vf
            [0, 0, 2, 0, 0, 0],           # q̈(0) = a0
            [0, 0, 2, 6*T, 12*T**2, 20*T**3]  # q̈(T) = af
        ])
        
        b = np.array([q0, qf, v0, vf, a0, af])
        
        coefficients = np.linalg.solve(A, b)
        return coefficients
    
    def position(self, t):
        """Calculate position at time t"""
        t = np.clip(t, 0, self.T)
        powers = np.array([1, t, t**2, t**3, t**4, t**5])
        return np.dot(self.coefficients, powers)
    
    def velocity(self, t):
        """Calculate velocity at time t"""
        t = np.clip(t, 0, self.T)
        powers = np.array([0, 1, 2*t, 3*t**2, 4*t**3, 5*t**4])
        return np.dot(self.coefficients, powers)
    
    def acceleration(self, t):
        """Calculate acceleration at time t"""
        t = np.clip(t, 0, self.T)
        powers = np.array([0, 0, 2, 6*t, 12*t**2, 20*t**3])
        return np.dot(self.coefficients, powers)
    
    def jerk(self, t):
        """Calculate jerk at time t"""
        t = np.clip(t, 0, self.T)
        powers = np.array([0, 0, 0, 6, 24*t, 60*t**2])
        return np.dot(self.coefficients, powers)
```

## Trapezoidal Velocity Profiles

### Basic Trapezoidal Profile
```python
class TrapezoidalProfile:
    def __init__(self, q0, qf, v_max, a_max):
        """
        Generate trapezoidal velocity profile
        
        Args:
            q0, qf: Start and end positions
            v_max: Maximum velocity
            a_max: Maximum acceleration/deceleration
        """
        self.q0 = q0
        self.qf = qf
        self.distance = abs(qf - q0)
        self.direction = 1 if qf > q0 else -1
        
        self.v_max = abs(v_max) * self.direction
        self.a_max = abs(a_max)
        
        # Calculate time phases
        self.t_accel = abs(self.v_max) / self.a_max
        self.distance_accel = 0.5 * self.a_max * self.t_accel**2
        self.distance_decel = self.distance_accel
        
        self.distance_cruise = self.distance - self.distance_accel - self.distance_decel
        
        if self.distance_cruise < 0:
            # Triangular profile (no cruise phase)
            self.is_triangular = True
            self.v_peak = self.direction * np.sqrt(self.a_max * self.distance)
            self.t_accel = abs(self.v_peak) / self.a_max
            self.t_cruise = 0
            self.t_decel = self.t_accel
        else:
            # True trapezoidal profile
            self.is_triangular = False
            self.v_peak = self.v_max
            self.t_cruise = self.distance_cruise / abs(self.v_max)
            self.t_decel = self.t_accel
        
        self.total_time = self.t_accel + self.t_cruise + self.t_decel
    
    def position(self, t):
        """Calculate position at time t"""
        t = np.clip(t, 0, self.total_time)
        
        if t <= self.t_accel:
            # Acceleration phase
            return self.q0 + self.direction * 0.5 * self.a_max * t**2
        elif t <= self.t_accel + self.t_cruise:
            # Cruise phase
            t_cruise = t - self.t_accel
            return (self.q0 + self.direction * self.distance_accel + 
                   self.v_peak * t_cruise)
        else:
            # Deceleration phase
            t_decel = t - self.t_accel - self.t_cruise
            return (self.qf - self.direction * self.distance_decel + 
                   self.v_peak * t_decel - 
                   self.direction * 0.5 * self.a_max * t_decel**2)
    
    def velocity(self, t):
        """Calculate velocity at time t"""
        t = np.clip(t, 0, self.total_time)
        
        if t <= self.t_accel:
            return self.direction * self.a_max * t
        elif t <= self.t_accel + self.t_cruise:
            return self.v_peak
        else:
            t_decel = t - self.t_accel - self.t_cruise
            return self.v_peak - self.direction * self.a_max * t_decel
    
    def acceleration(self, t):
        """Calculate acceleration at time t"""
        t = np.clip(t, 0, self.total_time)
        
        if t <= self.t_accel:
            return self.direction * self.a_max
        elif t <= self.t_accel + self.t_cruise:
            return 0
        else:
            return -self.direction * self.a_max
```

## Multi-Joint Trajectory Synchronization

### Time-Synchronized Trajectories
```python
def generate_synchronized_trajectory(waypoints, constraints, sync_method='time_optimal'):
    """
    Generate synchronized multi-joint trajectory
    
    Args:
        waypoints: List of joint configurations [(q1, q2, ...), ...]
        constraints: TrajectoryConstraints object
        sync_method: 'time_optimal', 'equal_time', or 'velocity_scaled'
    """
    
    n_joints = len(waypoints[0])
    n_segments = len(waypoints) - 1
    
    if sync_method == 'time_optimal':
        return time_optimal_trajectory(waypoints, constraints)
    elif sync_method == 'equal_time':
        return equal_time_trajectory(waypoints, constraints)
    elif sync_method == 'velocity_scaled':
        return velocity_scaled_trajectory(waypoints, constraints)

def time_optimal_trajectory(waypoints, constraints):
    """Generate time-optimal trajectory respecting all constraints"""
    
    trajectories = []
    
    for i in range(len(waypoints) - 1):
        q0 = np.array(waypoints[i])
        qf = np.array(waypoints[i + 1])
        
        # Calculate time required for each joint
        joint_times = []
        for j in range(len(q0)):
            distance = abs(qf[j] - q0[j])
            v_max = constraints.velocity_limits[j]
            a_max = constraints.acceleration_limits[j]
            
            # Time for trapezoidal profile
            if distance == 0:
                joint_times.append(0)
            else:
                # Check if triangular or trapezoidal
                t_triangle = 2 * np.sqrt(distance / a_max)
                v_triangle = a_max * t_triangle / 2
                
                if v_triangle <= v_max:
                    # Triangular profile
                    joint_times.append(t_triangle)
                else:
                    # Trapezoidal profile
                    t_trap = distance / v_max + v_max / a_max
                    joint_times.append(t_trap)
        
        # Use maximum time to synchronize all joints
        segment_time = max(joint_times)
        
        # Generate individual joint trajectories
        segment_trajectories = []
        for j in range(len(q0)):
            if abs(qf[j] - q0[j]) < 1e-6:
                # No motion needed
                traj = ConstantTrajectory(q0[j], segment_time)
            else:
                # Scale velocity to match segment time
                required_v_max = abs(qf[j] - q0[j]) / (segment_time - constraints.acceleration_limits[j] / constraints.acceleration_limits[j])
                scaled_v_max = min(required_v_max, constraints.velocity_limits[j])
                
                traj = TrapezoidalProfile(q0[j], qf[j], scaled_v_max, constraints.acceleration_limits[j])
            
            segment_trajectories.append(traj)
        
        trajectories.append(segment_trajectories)
    
    return MultiSegmentTrajectory(trajectories)

class MultiSegmentTrajectory:
    def __init__(self, segment_trajectories):
        """
        Multi-segment trajectory combining multiple phases
        
        Args:
            segment_trajectories: List of lists, each containing joint trajectories for one segment
        """
        self.segments = segment_trajectories
        self.segment_times = []
        
        # Calculate cumulative segment times
        cumulative_time = 0
        for segment in self.segments:
            segment_time = segment[0].total_time  # All joints should have same time
            self.segment_times.append((cumulative_time, cumulative_time + segment_time))
            cumulative_time += segment_time
        
        self.total_time = cumulative_time
    
    def position(self, t):
        """Get joint positions at time t"""
        # Find which segment we're in
        for i, (start_time, end_time) in enumerate(self.segment_times):
            if start_time <= t <= end_time:
                local_time = t - start_time
                return np.array([traj.position(local_time) for traj in self.segments[i]])
        
        # Before start or after end
        if t < 0:
            return np.array([traj.position(0) for traj in self.segments[0]])
        else:
            return np.array([traj.position(traj.total_time) for traj in self.segments[-1]])
    
    def velocity(self, t):
        """Get joint velocities at time t"""
        for i, (start_time, end_time) in enumerate(self.segment_times):
            if start_time <= t <= end_time:
                local_time = t - start_time
                return np.array([traj.velocity(local_time) for traj in self.segments[i]])
        
        return np.zeros(len(self.segments[0]))  # Zero velocity at ends
    
    def acceleration(self, t):
        """Get joint accelerations at time t"""
        for i, (start_time, end_time) in enumerate(self.segment_times):
            if start_time <= t <= end_time:
                local_time = t - start_time
                return np.array([traj.acceleration(local_time) for traj in self.segments[i]])
        
        return np.zeros(len(self.segments[0]))  # Zero acceleration at ends
```

## Advanced Trajectory Methods

### B-Spline Trajectories
```python
from scipy.interpolate import BSpline
import numpy as np

class BSplineTrajectory:
    def __init__(self, control_points, degree=3, knot_vector=None):
        """
        Generate smooth trajectory using B-splines
        
        Args:
            control_points: Array of shape (n_points, n_joints)
            degree: Polynomial degree of B-spline (typically 3 or 5)
            knot_vector: Custom knot vector (None for uniform)
        """
        self.control_points = np.array(control_points)
        self.degree = degree
        self.n_joints = self.control_points.shape[1]
        
        if knot_vector is None:
            # Create uniform knot vector
            n_control = len(control_points)
            self.knots = np.concatenate([
                np.zeros(degree),
                np.linspace(0, 1, n_control - degree + 1),
                np.ones(degree)
            ])
        else:
            self.knots = knot_vector
        
        # Create B-spline for each joint
        self.splines = []
        for joint in range(self.n_joints):
            spline = BSpline(self.knots, self.control_points[:, joint], self.degree)
            self.splines.append(spline)
    
    def position(self, u):
        """Evaluate trajectory at parameter u ∈ [0, 1]"""
        u = np.clip(u, 0, 1)
        return np.array([spline(u) for spline in self.splines])
    
    def velocity(self, u, dt=1.0):
        """Calculate velocity (first derivative scaled by time)"""
        u = np.clip(u, 0, 1)
        velocities = []
        for spline in self.splines:
            # Derivative of B-spline
            deriv_spline = spline.derivative(1)
            velocities.append(deriv_spline(u) / dt)
        return np.array(velocities)
    
    def acceleration(self, u, dt=1.0):
        """Calculate acceleration (second derivative)"""
        u = np.clip(u, 0, 1)
        accelerations = []
        for spline in self.splines:
            deriv2_spline = spline.derivative(2)
            accelerations.append(deriv2_spline(u) / (dt**2))
        return np.array(accelerations)
    
    def optimize_control_points(self, target_positions, weights=None):
        """Optimize control points to best fit target positions"""
        
        if weights is None:
            weights = np.ones(len(target_positions))
        
        def objective(flat_control_points):
            # Reshape flat array back to control points matrix
            control_points = flat_control_points.reshape(-1, self.n_joints)
            
            # Create temporary B-spline
            temp_splines = []
            for joint in range(self.n_joints):
                spline = BSpline(self.knots, control_points[:, joint], self.degree)
                temp_splines.append(spline)
            
            # Evaluate at target parameter values
            total_error = 0
            u_values = np.linspace(0, 1, len(target_positions))
            
            for i, (u, target) in enumerate(zip(u_values, target_positions)):
                current = np.array([spline(u) for spline in temp_splines])
                error = np.linalg.norm(current - target) * weights[i]
                total_error += error**2
            
            return total_error
        
        # Optimize using scipy
        from scipy.optimize import minimize
        
        initial_guess = self.control_points.flatten()
        result = minimize(objective, initial_guess)
        
        if result.success:
            optimized_points = result.x.reshape(-1, self.n_joints)
            return BSplineTrajectory(optimized_points, self.degree, self.knots)
        else:
            return self  # Return original if optimization failed
```

### Minimum Jerk Trajectories
```python
class MinimumJerkTrajectory:
    def __init__(self, waypoints, time_segments):
        """
        Generate minimum jerk trajectory through waypoints
        Minimizes integral of squared jerk for smooth motion
        """
        self.waypoints = np.array(waypoints)
        self.time_segments = time_segments
        self.n_joints = self.waypoints.shape[1]
        self.n_segments = len(waypoints) - 1
        
        # Solve for polynomial coefficients
        self.coefficients = self._solve_minimum_jerk()
    
    def _solve_minimum_jerk(self):
        """Solve optimization problem for minimum jerk"""
        
        # For each segment, use quintic polynomial
        # Minimize ∫(jerk²)dt subject to continuity constraints
        
        coefficients = []
        
        for joint in range(self.n_joints):
            joint_coeffs = []
            
            # Extract waypoints for this joint
            joint_waypoints = self.waypoints[:, joint]
            
            # Set up optimization problem
            n_coeffs = 6 * self.n_segments  # 6 coefficients per quintic polynomial
            
            # Objective: minimize integral of squared jerk
            def jerk_objective(coeffs):
                total_jerk = 0
                for seg in range(self.n_segments):
                    a = coeffs[seg*6:(seg+1)*6]  # Coefficients for this segment
                    T = self.time_segments[seg]
                    
                    # Jerk coefficients (derivative of acceleration)
                    jerk_coeffs = np.array([0, 0, 0, 6*a[3], 24*a[4], 60*a[5]])
                    
                    # Integrate jerk squared over segment
                    for i in range(6):
                        for j in range(6):
                            if i >= 3 and j >= 3:  # Only non-zero jerk terms
                                power = i + j - 5  # Power of t after integration
                                if power >= 0:
                                    integral = T**(power + 1) / (power + 1)
                                    total_jerk += jerk_coeffs[i] * jerk_coeffs[j] * integral
                
                return total_jerk
            
            # Constraints: position continuity at waypoints
            constraints = []
            
            # Initial and final positions
            def initial_pos(coeffs):
                return coeffs[0] - joint_waypoints[0]  # q(0) = waypoint[0]
            
            def final_pos(coeffs):
                final_seg = (self.n_segments - 1) * 6
                a = coeffs[final_seg:final_seg+6]
                T = self.time_segments[-1]
                pos = sum(a[i] * T**i for i in range(6))
                return pos - joint_waypoints[-1]  # q(T) = waypoint[-1]
            
            constraints.extend([
                {'type': 'eq', 'fun': initial_pos},
                {'type': 'eq', 'fun': final_pos}
            ])
            
            # Intermediate waypoint constraints
            for wp_idx in range(1, self.n_segments):
                def waypoint_constraint(coeffs, seg_idx=wp_idx-1, wp_val=joint_waypoints[wp_idx]):
                    seg_coeffs = coeffs[seg_idx*6:(seg_idx+1)*6]
                    T = self.time_segments[seg_idx]
                    pos = sum(seg_coeffs[i] * T**i for i in range(6))
                    return pos - wp_val
                
                constraints.append({'type': 'eq', 'fun': waypoint_constraint})
            
            # Velocity and acceleration continuity at segment boundaries
            for seg in range(self.n_segments - 1):
                # Velocity continuity
                def vel_continuity(coeffs, s=seg):
                    T1 = self.time_segments[s]
                    T2 = 0  # Start of next segment
                    
                    # End velocity of segment s
                    a1 = coeffs[s*6:(s+1)*6]
                    v1 = sum(i * a1[i] * T1**(i-1) for i in range(1, 6))
                    
                    # Start velocity of segment s+1
                    a2 = coeffs[(s+1)*6:(s+2)*6]
                    v2 = a2[1]  # Coefficient of t¹
                    
                    return v1 - v2
                
                # Acceleration continuity
                def acc_continuity(coeffs, s=seg):
                    T1 = self.time_segments[s]
                    
                    # End acceleration of segment s
                    a1 = coeffs[s*6:(s+1)*6]
                    acc1 = sum(i*(i-1) * a1[i] * T1**(i-2) for i in range(2, 6))
                    
                    # Start acceleration of segment s+1
                    a2 = coeffs[(s+1)*6:(s+2)*6]
                    acc2 = 2 * a2[2]  # Coefficient of 2t⁰
                    
                    return acc1 - acc2
                
                constraints.extend([
                    {'type': 'eq', 'fun': vel_continuity},
                    {'type': 'eq', 'fun': acc_continuity}
                ])
            
            # Solve optimization
            initial_guess = np.zeros(n_coeffs)
            
            from scipy.optimize import minimize
            result = minimize(jerk_objective, initial_guess, constraints=constraints)
            
            if result.success:
                joint_coeffs = result.x.reshape(self.n_segments, 6)
            else:
                # Fallback to simple polynomial interpolation
                joint_coeffs = self._fallback_interpolation(joint_waypoints)
            
            coefficients.append(joint_coeffs)
        
        return coefficients
    
    def position(self, t):
        """Evaluate position at time t"""
        # Find which segment we're in
        cumulative_time = 0
        for seg in range(self.n_segments):
            if cumulative_time <= t <= cumulative_time + self.time_segments[seg]:
                local_t = t - cumulative_time
                T = self.time_segments[seg]
                
                # Normalize time to [0,1] for numerical stability
                tau = local_t / T
                
                positions = []
                for joint in range(self.n_joints):
                    a = self.coefficients[joint][seg]
                    # Evaluate polynomial at normalized time
                    pos = sum(a[i] * (tau * T)**i for i in range(6))
                    positions.append(pos)
                
                return np.array(positions)
            
            cumulative_time += self.time_segments[seg]
        
        # Handle edge cases
        if t <= 0:
            return self.waypoints[0]
        else:
            return self.waypoints[-1]
```

## Real-Time Trajectory Execution

### Trajectory Following Controller
```python
class TrajectoryFollower:
    def __init__(self, trajectory, control_frequency=1000):
        """
        Real-time trajectory following controller
        
        Args:
            trajectory: Trajectory object with position(), velocity(), acceleration()
            control_frequency: Control loop frequency in Hz
        """
        self.trajectory = trajectory
        self.dt = 1.0 / control_frequency
        self.start_time = 0
        self.current_time = 0
        
        # PID gains (can be tuned per joint)
        self.kp = np.ones(trajectory.n_joints) * 100  # Position gain
        self.kv = np.ones(trajectory.n_joints) * 20   # Velocity gain
        self.ki = np.ones(trajectory.n_joints) * 1    # Integral gain
        
        # State variables
        self.position_error_integral = np.zeros(trajectory.n_joints)
        self.last_error = np.zeros(trajectory.n_joints)
    
    def update(self, current_joint_positions, current_joint_velocities):
        """
        Update control commands based on current state
        
        Returns:
            dict: Control commands {'torque': array, 'feedforward': dict}
        """
        
        # Get desired trajectory values at current time
        t_traj = self.current_time - self.start_time
        
        desired_pos = self.trajectory.position(t_traj)
        desired_vel = self.trajectory.velocity(t_traj)
        desired_acc = self.trajectory.acceleration(t_traj)
        
        # Calculate errors
        position_error = desired_pos - current_joint_positions
        velocity_error = desired_vel - current_joint_velocities
        
        # Update integral term
        self.position_error_integral += position_error * self.dt
        
        # PID control law
        torque_pd = (self.kp * position_error + 
                    self.kv * velocity_error +
                    self.ki * self.position_error_integral)
        
        # Feedforward compensation
        torque_feedforward = self._calculate_feedforward(desired_pos, desired_vel, desired_acc)
        
        # Total control torque
        total_torque = torque_pd + torque_feedforward
        
        # Update time
        self.current_time += self.dt
        
        return {
            'torque': total_torque,
            'feedforward': {
                'position': desired_pos,
                'velocity': desired_vel,
                'acceleration': desired_acc
            },
            'errors': {
                'position': position_error,
                'velocity': velocity_error
            }
        }
    
    def _calculate_feedforward(self, q, q_dot, q_ddot):
        """
        Calculate feedforward torques using robot dynamics
        This is a simplified model - real implementation would use full dynamics
        """
        
        # Simplified: assume decoupled joints with known inertia
        joint_inertias = np.ones(len(q)) * 0.1  # kg⋅m²
        
        # Feedforward = Inertia × desired_acceleration + friction
        friction_coefficient = 0.1
        friction_torque = friction_coefficient * np.sign(q_dot)
        
        feedforward_torque = joint_inertias * q_ddot + friction_torque
        
        return feedforward_torque
    
    def start_trajectory(self):
        """Start trajectory execution"""
        import time
        self.start_time = time.time()
        self.current_time = self.start_time
        self.position_error_integral.fill(0)
    
    def is_finished(self):
        """Check if trajectory execution is complete"""
        elapsed_time = self.current_time - self.start_time
        return elapsed_time >= self.trajectory.total_time
```

## Integration with FreeCAD and Robot Control

### FreeCAD Animation
```python
def animate_trajectory_freecad(robot_model, trajectory, animation_speed=1.0):
    """
    Animate trajectory in FreeCAD
    
    Args:
        robot_model: FreeCAD robot assembly
        trajectory: Trajectory object
        animation_speed: Speed multiplier for visualization
    """
    
    import FreeCAD
    import time
    
    # Get joint objects from robot model
    joints = [obj for obj in robot_model.Group if 'Joint' in obj.Name]
    
    # Animation loop
    t = 0
    dt = 0.05  # 20 FPS animation
    
    while t <= trajectory.total_time:
        # Get joint positions at current time
        joint_positions = trajectory.position(t)
        
        # Update joint angles in FreeCAD model
        for i, joint in enumerate(joints):
            if i < len(joint_positions):
                if hasattr(joint, 'Angle'):
                    joint.Angle = np.degrees(joint_positions[i])  # Convert to degrees
                elif hasattr(joint, 'Offset'):
                    joint.Offset = joint_positions[i]  # Prismatic joint
        
        # Recompute model and update display
        robot_model.recompute()
        FreeCAD.Gui.updateGui()
        
        # Wait for next frame
        time.sleep(dt / animation_speed)
        t += dt
    
    print("Animation complete!")

def export_trajectory_gcode(trajectory, robot_config, filename):
    """
    Export trajectory as G-code for CNC-style execution
    """
    
    with open(filename, 'w') as f:
        f.write("; Generated trajectory G-code\n")
        f.write(f"; Total time: {trajectory.total_time:.3f} seconds\n")
        f.write("; Generated by Turing Trajectory Generator\n\n")
        
        # Sample trajectory at high resolution
        dt = 0.001  # 1ms resolution
        t = 0
        
        while t <= trajectory.total_time:
            pos = trajectory.position(t)
            vel = trajectory.velocity(t)
            
            # Convert to G-code format (adapt for specific robot)
            f.write(f"G01 ")
            for i, (p, v) in enumerate(zip(pos, vel)):
                f.write(f"A{i+1}{p:.6f} F{abs(v)*60:.1f} ")  # F in units/min
            f.write(f"; t={t:.3f}\n")
            
            t += dt
        
        f.write("\nM30 ; End of program\n")
    
    print(f"Trajectory exported to {filename}")
```

Trajectory generation transforms kinematic possibility into controlled reality - the mathematical choreography that makes robots dance with precision through space and time.