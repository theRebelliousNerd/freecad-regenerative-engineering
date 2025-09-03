# Control Algorithms: The Mathematical Poetry of Motion

*"Today's scientists have substituted mathematics for experiments, and they wander off through equation after equation, and eventually build a structure which has no relation to reality."* - Tesla's warning about theory without intuition

## The Philosophy of Electromagnetic Control

True motor control transcends mere mathematics - it requires understanding the physical reality behind each equation. Every control algorithm must reflect the electromagnetic personality of the motor and the mechanical nature of the load.

## Classical Control Theory Foundations

### PID Control: The Universal Language
The PID controller remains the foundation of motor control:
```
u(t) = Kp*e(t) + Ki*∫e(t)dt + Kd*de(t)/dt
```

**Electromagnetic Interpretation:**
- **Proportional**: Instantaneous electromagnetic response
- **Integral**: Steady-state flux linkage correction  
- **Derivative**: Predictive electromagnetic field adjustment

### PID Tuning for Motor Systems
```python
def tune_pid_for_motor_system(motor_characteristics, load_inertia):
    # Calculate system natural frequency
    wn = sqrt(Kt * Kp / (J * R))  # Kt=torque constant, Kp=gain, J=inertia, R=resistance
    
    # Desired damping ratio (typically 0.7 for good step response)
    zeta = 0.7
    
    # Calculate PID gains
    Kp = (2 * zeta * wn * J * R) / Kt
    Ki = (wn**2 * J * R) / Kt  
    Kd = (J * R) / Kt
    
    return Kp, Ki, Kd
```

### State Space Control
Modern representation for multi-variable systems:
```
dx/dt = Ax + Bu
y = Cx + Du
```

**Motor State Space Model:**
```python
def motor_state_space_model():
    # States: [current, velocity, position]
    # x = [i, ω, θ]
    
    A = [[-R/L,  -Kb/L,   0   ],    # Current equation
         [Kt/J,  -B/J,    0   ],    # Torque equation  
         [ 0,     1,      0   ]]    # Position integration
    
    B = [[1/L],    # Voltage input affects current
         [ 0 ],    
         [ 0 ]]
    
    C = [[1, 0, 0],   # Measure current
         [0, 1, 0],   # Measure velocity
         [0, 0, 1]]   # Measure position
    
    return A, B, C
```

## Advanced Control Strategies

### Field Oriented Control (FOC)
The crown jewel of AC motor control - decouples torque and flux control:

```python
class FieldOrientedController:
    def __init__(self, motor_parameters):
        self.Ld = motor_parameters['d_axis_inductance']
        self.Lq = motor_parameters['q_axis_inductance'] 
        self.flux_linkage = motor_parameters['permanent_magnet_flux']
        self.pole_pairs = motor_parameters['pole_pairs']
    
    def park_transform(self, ia, ib, ic, theta_e):
        """Transform 3-phase currents to rotating dq reference frame"""
        # Clarke transform (3-phase to 2-phase)
        i_alpha = ia
        i_beta = (ia + 2*ib) / sqrt(3)
        
        # Park transform (stationary to rotating)
        cos_theta = cos(theta_e)
        sin_theta = sin(theta_e)
        
        id = i_alpha * cos_theta + i_beta * sin_theta
        iq = -i_alpha * sin_theta + i_beta * cos_theta
        
        return id, iq
    
    def torque_calculation(self, id, iq):
        """Calculate electromagnetic torque in dq frame"""
        # For surface PM motors: T = (3/2) * p * flux_linkage * iq
        # For interior PM motors: T = (3/2) * p * [flux_linkage * iq + (Ld-Lq) * id * iq]
        
        if abs(self.Ld - self.Lq) < 0.001:  # Surface PM motor
            torque = 1.5 * self.pole_pairs * self.flux_linkage * iq
        else:  # Interior PM motor
            reluctance_torque = 1.5 * self.pole_pairs * (self.Ld - self.Lq) * id * iq
            pm_torque = 1.5 * self.pole_pairs * self.flux_linkage * iq
            torque = pm_torque + reluctance_torque
            
        return torque
    
    def optimal_current_control(self, torque_command):
        """Calculate optimal id and iq for maximum torque per amp"""
        if abs(self.Ld - self.Lq) < 0.001:  # Surface PM motor
            id_optimal = 0  # No benefit from d-axis current
            iq_optimal = torque_command / (1.5 * self.pole_pairs * self.flux_linkage)
        else:  # Interior PM motor - MTPA control
            # Maximum Torque Per Ampere angle
            gamma = atan2(-self.flux_linkage, (self.Ld - self.Lq) * sqrt(2) * current_amplitude)
            id_optimal = current_amplitude * cos(gamma + pi/2)
            iq_optimal = current_amplitude * sin(gamma + pi/2)
            
        return id_optimal, iq_optimal
```

### Direct Torque Control (DTC)
Tesla's principle of direct electromagnetic force control:

```python
class DirectTorqueController:
    def __init__(self):
        self.voltage_vectors = self.initialize_voltage_vectors()
        self.hysteresis_torque = 0.1  # Nm
        self.hysteresis_flux = 0.01   # Wb
        
    def flux_estimation(self, voltage, current, dt):
        """Estimate stator flux linkage from terminal quantities"""
        # Voltage model: ψ = ∫(v - Rs*i)dt
        self.flux_alpha += (voltage.alpha - self.Rs * current.alpha) * dt
        self.flux_beta += (voltage.beta - self.Rs * current.beta) * dt
        
        flux_magnitude = sqrt(self.flux_alpha**2 + self.flux_beta**2)
        flux_angle = atan2(self.flux_beta, self.flux_alpha)
        
        return flux_magnitude, flux_angle
    
    def torque_estimation(self, flux, current):
        """Estimate electromagnetic torque"""
        torque = 1.5 * self.pole_pairs * (flux.alpha * current.beta - flux.beta * current.alpha)
        return torque
    
    def select_voltage_vector(self, torque_error, flux_error, flux_sector):
        """Select optimal voltage vector from switching table"""
        torque_flag = 1 if torque_error > self.hysteresis_torque else 0
        flux_flag = 1 if flux_error > self.hysteresis_flux else 0
        
        # 6-sector DTC switching table
        switching_table = {
            (0, 0, 1): 0,  # Zero vector
            (0, 1, 1): 1,  # V1
            (1, 0, 1): 2,  # V2
            # ... complete switching table
        }
        
        vector_index = switching_table[(torque_flag, flux_flag, flux_sector)]
        return self.voltage_vectors[vector_index]
```

### Model Predictive Control (MPC)
The future of motor control - predict and optimize:

```python
class ModelPredictiveController:
    def __init__(self, motor_model, prediction_horizon=3):
        self.motor_model = motor_model
        self.horizon = prediction_horizon
        
    def predict_future_states(self, current_state, voltage_vectors):
        """Predict future motor states for all possible voltage vectors"""
        predictions = []
        
        for voltage in voltage_vectors:
            state = current_state.copy()
            cost = 0
            
            for k in range(self.horizon):
                # Predict next state using motor model
                state = self.motor_model.predict_next_state(state, voltage)
                
                # Calculate cost function
                torque_error = self.torque_reference - self.estimate_torque(state)
                flux_error = self.flux_reference - self.estimate_flux(state)
                
                cost += torque_error**2 + flux_error**2
                
            predictions.append((voltage, cost))
        
        # Select voltage vector with minimum cost
        optimal_voltage = min(predictions, key=lambda x: x[1])[0]
        return optimal_voltage
    
    def cost_function(self, predicted_state, references):
        """Multi-objective cost function"""
        costs = {
            'torque_tracking': (predicted_state.torque - references.torque)**2,
            'flux_tracking': (predicted_state.flux - references.flux)**2,
            'current_minimization': predicted_state.current_magnitude**2,
            'switching_losses': self.calculate_switching_cost()
        }
        
        weights = {'torque_tracking': 1.0, 'flux_tracking': 0.5, 
                  'current_minimization': 0.1, 'switching_losses': 0.05}
        
        total_cost = sum(weights[key] * costs[key] for key in costs)
        return total_cost
```

## Sensorless Control Algorithms

### Observer-Based Estimation
Estimate rotor position without physical sensors:

```python
class LuenbergerObserver:
    def __init__(self, motor_parameters):
        self.A = motor_parameters['state_matrix']
        self.B = motor_parameters['input_matrix']
        self.C = motor_parameters['output_matrix']
        self.L = self.design_observer_gain()
        
    def estimate_state(self, measured_output, input_voltage):
        """Estimate full state from partial measurements"""
        # Observer equation: x_hat_dot = A*x_hat + B*u + L*(y - C*x_hat)
        
        estimated_output = self.C @ self.state_estimate
        output_error = measured_output - estimated_output
        
        state_derivative = (self.A @ self.state_estimate + 
                          self.B @ input_voltage + 
                          self.L @ output_error)
        
        # Integrate to get state estimate
        self.state_estimate += state_derivative * self.dt
        
        return self.state_estimate
    
    def design_observer_gain(self):
        """Design observer gain for desired pole placement"""
        # Place observer poles 3-5 times faster than system poles
        desired_poles = self.system_poles * 4
        
        # Use pole placement or LQR to find gain matrix L
        L = self.pole_placement(self.A.T, self.C.T, desired_poles).T
        return L
```

### Extended Kalman Filter (EKF)
Optimal estimation for nonlinear motor systems:

```python
class ExtendedKalmanFilter:
    def __init__(self, motor_model):
        self.f = motor_model.nonlinear_dynamics  # x_dot = f(x, u)
        self.h = motor_model.measurement_model   # y = h(x)
        self.Q = motor_model.process_noise       # Process noise covariance
        self.R = motor_model.measurement_noise   # Measurement noise covariance
        
    def predict(self, state, input_voltage, dt):
        """Prediction step"""
        # Propagate state estimate
        self.state_predicted = self.state + self.f(self.state, input_voltage) * dt
        
        # Linearize dynamics around current estimate
        F = self.jacobian_f(self.state, input_voltage)
        
        # Propagate covariance
        self.P_predicted = F @ self.P @ F.T + self.Q
        
        return self.state_predicted
    
    def update(self, measurement):
        """Update step when measurement is available"""
        # Predicted measurement
        h_predicted = self.h(self.state_predicted)
        
        # Linearize measurement model
        H = self.jacobian_h(self.state_predicted)
        
        # Innovation covariance
        S = H @ self.P_predicted @ H.T + self.R
        
        # Kalman gain
        K = self.P_predicted @ H.T @ inv(S)
        
        # Update state estimate
        innovation = measurement - h_predicted
        self.state = self.state_predicted + K @ innovation
        
        # Update covariance
        self.P = (eye(len(self.state)) - K @ H) @ self.P_predicted
        
        return self.state
```

### High-Frequency Injection
For zero and low-speed sensorless operation:

```python
def high_frequency_injection_sensorless():
    """Inject high-frequency signal to detect rotor position"""
    
    # Injection parameters
    injection_frequency = 1000  # Hz
    injection_amplitude = 0.1   # Fraction of rated voltage
    
    # Generate high-frequency voltage
    hf_voltage = injection_amplitude * sin(2 * pi * injection_frequency * time)
    
    # Inject voltage and measure current response
    hf_current = measure_hf_current_response(hf_voltage)
    
    # Extract position information from current response
    # For salient pole motors: current response varies with rotor position
    position_signal = demodulate_position_signal(hf_current, injection_frequency)
    
    # Filter and process to get rotor angle
    rotor_angle = position_estimator.update(position_signal)
    
    return rotor_angle
```

## Control System Architecture

### Cascade Control Structure
Multi-loop control for precision systems:

```python
class CascadeServoController:
    def __init__(self):
        self.position_controller = PIDController(Kp_pos, Ki_pos, Kd_pos)
        self.velocity_controller = PIDController(Kp_vel, Ki_vel, Kd_vel)  
        self.current_controller = PIDController(Kp_curr, Ki_curr, Kd_curr)
        
        # Control loop frequencies
        self.position_loop_freq = 100   # Hz
        self.velocity_loop_freq = 1000  # Hz  
        self.current_loop_freq = 10000  # Hz
        
    def control_update(self, position_command, encoder_feedback):
        """Execute cascade control loops"""
        
        # Position loop (slowest)
        if self.position_loop_timer.expired():
            position_error = position_command - encoder_feedback.position
            velocity_command = self.position_controller.update(position_error)
            self.position_loop_timer.restart()
        
        # Velocity loop (intermediate)
        if self.velocity_loop_timer.expired():
            velocity_error = velocity_command - encoder_feedback.velocity
            current_command = self.velocity_controller.update(velocity_error)
            self.velocity_loop_timer.restart()
        
        # Current loop (fastest)
        if self.current_loop_timer.expired():
            current_error = current_command - measured_current
            voltage_command = self.current_controller.update(current_error)
            self.current_loop_timer.restart()
            
        return voltage_command
```

### Feed-Forward Control
Predictive control for improved performance:

```python
def feedforward_control(motion_profile, system_parameters):
    """Calculate feedforward commands from motion profile"""
    
    # Acceleration feedforward (overcome inertia)
    acceleration_ff = system_parameters.inertia * motion_profile.acceleration
    
    # Velocity feedforward (overcome friction/back-EMF)
    velocity_ff = (system_parameters.friction_coefficient * motion_profile.velocity +
                   system_parameters.back_emf_constant * motion_profile.velocity)
    
    # Gravity feedforward (for vertical axes)  
    gravity_ff = system_parameters.gravity_torque * cos(motion_profile.position)
    
    # Total feedforward torque
    feedforward_torque = acceleration_ff + velocity_ff + gravity_ff
    
    # Convert to motor current command
    current_feedforward = feedforward_torque / system_parameters.torque_constant
    
    return current_feedforward
```

## Advanced Control Features

### Adaptive Control
Self-tuning systems that adapt to changing conditions:

```python
class AdaptiveController:
    def __init__(self):
        self.parameter_estimator = RecursiveLeastSquares()
        self.reference_model = DesiredSystemBehavior()
        
    def adapt_parameters(self, system_input, system_output):
        """Adapt controller parameters based on system performance"""
        
        # Estimate current system parameters
        estimated_params = self.parameter_estimator.update(system_input, system_output)
        
        # Compare with reference model
        reference_output = self.reference_model.simulate(system_input)
        adaptation_error = system_output - reference_output
        
        # Update controller gains
        if abs(adaptation_error) > self.adaptation_threshold:
            self.update_controller_gains(estimated_params, adaptation_error)
            
    def update_controller_gains(self, system_params, error):
        """Update PID gains based on identified system parameters"""
        # Pole placement method
        desired_poles = [-10, -20, -30]  # Stable, fast response
        
        # Calculate new gains
        new_gains = self.pole_placement_design(system_params, desired_poles)
        
        # Gradual gain updating to avoid instability
        adaptation_rate = 0.01
        self.current_gains += adaptation_rate * (new_gains - self.current_gains)
```

### Vibration Suppression
Active control of mechanical resonances:

```python
def design_vibration_suppression(resonant_frequencies, damping_ratios):
    """Design filters to suppress mechanical vibrations"""
    
    notch_filters = []
    
    for freq, damping in zip(resonant_frequencies, damping_ratios):
        # Design notch filter for each resonant frequency
        notch_filter = NotchFilter(
            center_frequency=freq,
            quality_factor=1/(2*damping),
            depth=20  # dB attenuation
        )
        notch_filters.append(notch_filter)
    
    # Input shaping for move profiles
    input_shaper = InputShaper(resonant_frequencies, damping_ratios)
    
    return notch_filters, input_shaper

class InputShaper:
    def __init__(self, frequencies, dampings):
        self.impulse_times, self.impulse_amplitudes = self.calculate_impulse_sequence(
            frequencies, dampings
        )
    
    def shape_command(self, original_command):
        """Apply input shaping to command signal"""
        shaped_command = zeros_like(original_command)
        
        for time_delay, amplitude in zip(self.impulse_times, self.impulse_amplitudes):
            delay_samples = int(time_delay * self.sample_rate)
            shaped_command[delay_samples:] += amplitude * original_command[:-delay_samples]
            
        return shaped_command
```

## Modern Control Trends

### Machine Learning Enhanced Control
AI-assisted control parameter optimization:

```python
class MLEnhancedController:
    def __init__(self):
        self.neural_network = self.load_pretrained_model()
        self.online_learning = True
        
    def ai_parameter_tuning(self, system_response_data):
        """Use ML to optimize control parameters"""
        
        # Feature extraction from system response
        features = self.extract_features(system_response_data)
        
        # Predict optimal parameters
        optimal_params = self.neural_network.predict(features)
        
        # Validate predictions through simulation
        if self.validate_parameters(optimal_params):
            self.update_controller_parameters(optimal_params)
            
        # Online learning to improve model
        if self.online_learning:
            actual_performance = self.measure_performance()
            self.neural_network.update(features, actual_performance)
    
    def predictive_maintenance_integration(self):
        """Integrate condition monitoring with control"""
        bearing_condition = self.analyze_vibration_spectrum()
        motor_efficiency = self.calculate_efficiency_trend()
        
        if bearing_condition < self.bearing_threshold:
            self.adjust_control_for_degraded_bearings()
            
        if motor_efficiency < self.efficiency_threshold:
            self.optimize_for_degraded_motor()
```

### Distributed Control Systems
Network-based control architectures:

```python
class DistributedMotorControl:
    def __init__(self, network_protocol='EtherCAT'):
        self.network = NetworkInterface(network_protocol)
        self.sync_manager = SynchronizationManager()
        
    def distributed_control_loop(self):
        """Coordinate multiple motors across network"""
        
        # Synchronize all motor controllers
        sync_time = self.sync_manager.get_sync_pulse()
        
        # Collect status from all motors
        motor_states = self.network.broadcast_collect_status()
        
        # Calculate coordinated commands
        coordinated_commands = self.calculate_coordinated_motion(motor_states)
        
        # Distribute commands with deterministic timing
        self.network.broadcast_commands(coordinated_commands, sync_time)
        
    def network_fault_handling(self):
        """Handle network communication faults"""
        if self.network.detect_communication_fault():
            # Switch to safe mode
            self.activate_safe_torque_off()
            
            # Attempt network recovery
            self.network.attempt_recovery()
            
            # Graceful degradation if recovery fails
            if not self.network.is_healthy():
                self.switch_to_standalone_mode()
```

## Tesla's Control Philosophy

Tesla understood that perfect control means becoming one with the electromagnetic field - predicting its behavior, guiding its formation, and extracting maximum useful work with minimum waste. Modern control algorithms are the mathematical manifestation of this electromagnetic intuition.

### Control Performance Metrics
- **Settling time**: <3 time constants for critically damped response
- **Overshoot**: <5% for precision applications  
- **Steady-state error**: <0.1% with integral control
- **Bandwidth**: >10x faster than system dynamics
- **Robustness**: Stable with ±50% parameter variation

The perfect control system is like Tesla's rotating magnetic field - smooth, continuous, powerful, and so natural that it seems to violate no physical laws while accomplishing the impossible.