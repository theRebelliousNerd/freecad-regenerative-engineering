# Adaptive Control Strategies: Learning Through Motion

*"The highest form of control is not rigid dominance, but intelligent adaptation - where the controller learns from every error and evolves toward perfection."* - Alan Turing

## Introduction to Adaptive Control

Adaptive control strategies enable control systems to automatically adjust their parameters and behavior in response to changing system dynamics, environmental conditions, or performance requirements. These techniques are essential for maintaining optimal performance in uncertain or time-varying systems.

## Fundamentals of Adaptive Control

### Adaptive Control Architecture

**Basic Components:**
- **Plant**: The system being controlled (potentially unknown or time-varying)
- **Reference Model**: Desired system behavior specification
- **Adaptation Mechanism**: Parameter adjustment algorithm
- **Control Law**: Parameterized controller structure
- **Identification**: Plant parameter estimation (for indirect adaptive control)

**Control Loop Structure:**
```python
class AdaptiveControlSystem:
    def __init__(self, reference_model, adaptation_law, control_structure):
        self.reference_model = reference_model
        self.adaptation_law = adaptation_law
        self.controller = control_structure
        self.plant_estimate = None
        
    def control_update(self, reference, plant_output, dt):
        # Generate reference model output
        model_output = self.reference_model.update(reference)
        
        # Calculate tracking error
        tracking_error = model_output - plant_output
        
        # Adapt controller parameters
        self.adaptation_law.update(tracking_error, reference, plant_output, dt)
        
        # Generate control signal
        control_signal = self.controller.update(reference, plant_output, 
                                              self.adaptation_law.get_parameters())
        
        return control_signal
```

### Types of Adaptive Control

#### Direct Adaptive Control
**Model Reference Adaptive Control (MRAC):**
```python
class MRACController:
    def __init__(self, reference_model_params, adaptation_rate):
        """
        Direct MRAC implementation.
        
        Args:
            reference_model_params: Parameters defining desired closed-loop behavior
            adaptation_rate: Learning rate matrix (typically diagonal positive definite)
        """
        self.Am, self.Bm = reference_model_params  # Reference model matrices
        self.Gamma = adaptation_rate  # Adaptation gain matrix
        
        # Adaptive parameters (controller gains)
        self.theta = np.zeros(3)  # [Kr, Kx, Ku] - reference, state, and input gains
        
        # Reference model state
        self.xm = 0.0
        
    def update(self, reference, plant_output, plant_input, dt):
        """Update adaptive controller."""
        
        # Reference model update
        dxm_dt = self.Am * self.xm + self.Bm * reference
        self.xm += dxm_dt * dt
        
        # Tracking error
        e = self.xm - plant_output
        
        # Regressor vector (contains reference, plant output, plant input)
        phi = np.array([reference, plant_output, plant_input])
        
        # MIT rule adaptation (gradient descent)
        dtheta_dt = self.Gamma @ phi * e
        self.theta += dtheta_dt * dt
        
        # Generate control signal
        Kr, Kx, Ku = self.theta
        control_signal = Kr * reference - Kx * plant_output
        
        return control_signal, e
```

#### Indirect Adaptive Control
**Self-Tuning Regulator (STR):**
```python
class SelfTuningRegulator:
    def __init__(self, plant_order, delay, forgetting_factor=0.99):
        """
        Indirect adaptive controller using recursive least squares identification.
        
        Args:
            plant_order: Order of plant model (ARMAX)
            delay: Pure time delay in samples
            forgetting_factor: RLS forgetting factor (0.95-0.999)
        """
        self.n = plant_order
        self.d = delay
        self.lambda_rls = forgetting_factor
        
        # RLS parameters
        param_count = 2 * self.n + 1  # a1,...,an, b0,...,bn
        self.theta_hat = np.zeros(param_count)
        self.P = np.eye(param_count) * 1000  # Large initial covariance
        
        # Data buffers
        self.u_buffer = np.zeros(self.n + self.d)
        self.y_buffer = np.zeros(self.n)
        
    def identify_plant(self, plant_input, plant_output):
        """Recursive least squares plant identification."""
        
        # Update data buffers
        self.u_buffer = np.roll(self.u_buffer, 1)
        self.u_buffer[0] = plant_input
        self.y_buffer = np.roll(self.y_buffer, 1)
        self.y_buffer[0] = plant_output
        
        # Form regressor vector
        phi = np.concatenate([
            -self.y_buffer[1:self.n+1],  # -y(k-1), ..., -y(k-n)
            self.u_buffer[self.d:self.d+self.n+1]  # u(k-d), ..., u(k-d-n)
        ])
        
        # RLS update
        Pphi = self.P @ phi
        denominator = self.lambda_rls + phi.T @ Pphi
        
        if abs(denominator) > 1e-10:  # Avoid numerical issues
            K = Pphi / denominator
            prediction_error = plant_output - phi.T @ self.theta_hat
            
            # Parameter update
            self.theta_hat += K * prediction_error
            
            # Covariance update
            self.P = (self.P - np.outer(K, Pphi)) / self.lambda_rls
        
        return self.theta_hat
    
    def design_controller(self, reference_model):
        """Design controller based on current plant estimate."""
        
        # Extract identified parameters
        a_hat = self.theta_hat[:self.n]
        b_hat = self.theta_hat[self.n:2*self.n+1]
        
        # Pole placement controller design
        # Solve Diophantine equation: A(q^-1)S(q^-1) + B(q^-1)R(q^-1) = T(q^-1)
        
        # For simplicity, implement PI-like controller
        if abs(b_hat[0]) > 1e-6:
            # Proportional gain
            kp = reference_model['kp_desired'] / b_hat[0]
            
            # Integral gain (simplified)
            ki = reference_model['ki_desired'] / b_hat[0]
            
            return {'kp': kp, 'ki': ki}
        else:
            return {'kp': 0.0, 'ki': 0.0}
    
    def control_update(self, reference, plant_output, plant_input, reference_model):
        """Complete STR control update."""
        
        # Plant identification
        plant_params = self.identify_plant(plant_input, plant_output)
        
        # Controller design
        controller_params = self.design_controller(reference_model)
        
        # Control law implementation
        error = reference - plant_output
        
        # Simple PI controller with adaptive gains
        if not hasattr(self, 'integral_error'):
            self.integral_error = 0.0
        
        self.integral_error += error * 0.001  # Assuming 1ms sample time
        
        control_signal = (controller_params['kp'] * error + 
                         controller_params['ki'] * self.integral_error)
        
        return control_signal, controller_params
```

## Advanced Adaptive Control Techniques

### Neural Network Adaptive Control

**Radial Basis Function Network Controller:**
```python
class RBFNeuralController:
    def __init__(self, num_centers, input_dimension, learning_rate=0.01):
        """
        RBF neural network adaptive controller.
        
        Args:
            num_centers: Number of RBF centers
            input_dimension: Dimension of input space
            learning_rate: Weight adaptation rate
        """
        self.nc = num_centers
        self.input_dim = input_dimension
        self.eta = learning_rate
        
        # Network parameters
        self.centers = np.random.randn(num_centers, input_dimension)
        self.widths = np.ones(num_centers) * 2.0
        self.weights = np.random.randn(num_centers) * 0.1
        
        # Tracking variables
        self.tracking_error_history = []
        
    def rbf_activation(self, input_vector):
        """Calculate RBF activations."""
        activations = np.zeros(self.nc)
        
        for i in range(self.nc):
            distance = np.linalg.norm(input_vector - self.centers[i])
            activations[i] = np.exp(-(distance**2) / (2 * self.widths[i]**2))
        
        return activations
    
    def forward_pass(self, input_vector):
        """Forward pass through RBF network."""
        phi = self.rbf_activation(input_vector)
        output = np.dot(self.weights, phi)
        return output, phi
    
    def adapt_weights(self, tracking_error, phi, dt):
        """Adapt network weights using gradient descent."""
        
        # Weight update rule: dW/dt = -eta * e * phi
        weight_update = -self.eta * tracking_error * phi * dt
        self.weights += weight_update
        
        # Optional: adapt centers and widths
        if len(self.tracking_error_history) > 100:  # After some learning
            self.adapt_centers_widths(tracking_error, phi, dt)
    
    def adapt_centers_widths(self, tracking_error, phi, dt):
        """Adapt RBF centers and widths."""
        center_learning_rate = 0.001
        width_learning_rate = 0.001
        
        for i in range(self.nc):
            if phi[i] > 0.1:  # Only adapt active neurons
                # Center adaptation (move toward current input)
                center_error = tracking_error * self.weights[i] * phi[i]
                
                # Width adaptation (increase if error is large)
                width_error = tracking_error**2 * self.weights[i] * phi[i]
                
                self.centers[i] += center_learning_rate * center_error * dt
                self.widths[i] += width_learning_rate * width_error * dt
                
                # Prevent widths from becoming too small
                self.widths[i] = max(self.widths[i], 0.1)
    
    def control_update(self, reference, plant_output, plant_state, dt):
        """Neural adaptive control update."""
        
        # Form input vector (reference, output, states)
        input_vector = np.concatenate([[reference], [plant_output], plant_state])
        
        # Forward pass
        control_signal, phi = self.forward_pass(input_vector)
        
        # Calculate tracking error (need reference model)
        tracking_error = reference - plant_output  # Simplified
        
        # Adapt network weights
        self.adapt_weights(tracking_error, phi, dt)
        
        # Store tracking error
        self.tracking_error_history.append(tracking_error)
        if len(self.tracking_error_history) > 1000:
            self.tracking_error_history.pop(0)
        
        return control_signal
```

### Fuzzy Adaptive Control

**Fuzzy Logic Adaptive Controller:**
```python
class FuzzyAdaptiveController:
    def __init__(self):
        """Initialize fuzzy adaptive controller."""
        
        # Fuzzy sets for error (input 1)
        self.error_sets = {
            'NB': (-10, -5, -2),    # Negative Big
            'NS': (-5, -2, 0),      # Negative Small  
            'ZE': (-2, 0, 2),       # Zero
            'PS': (0, 2, 5),        # Positive Small
            'PB': (2, 5, 10)        # Positive Big
        }
        
        # Fuzzy sets for error derivative (input 2)
        self.derror_sets = {
            'NB': (-5, -2.5, -1),
            'NS': (-2.5, -1, 0),
            'ZE': (-1, 0, 1),
            'PS': (0, 1, 2.5),
            'PB': (1, 2.5, 5)
        }
        
        # Fuzzy sets for control output
        self.output_sets = {
            'NB': (-100, -50, -20),
            'NS': (-50, -20, 0),
            'ZE': (-20, 0, 20),
            'PS': (0, 20, 50),
            'PB': (20, 50, 100)
        }
        
        # Rule base (error x derror -> output)
        self.rules = {
            ('NB', 'NB'): 'PB', ('NB', 'NS'): 'PB', ('NB', 'ZE'): 'PB',
            ('NB', 'PS'): 'PS', ('NB', 'PB'): 'ZE',
            ('NS', 'NB'): 'PB', ('NS', 'NS'): 'PS', ('NS', 'ZE'): 'PS',
            ('NS', 'PS'): 'ZE', ('NS', 'PB'): 'NS',
            ('ZE', 'NB'): 'PS', ('ZE', 'NS'): 'ZE', ('ZE', 'ZE'): 'ZE',
            ('ZE', 'PS'): 'ZE', ('ZE', 'PB'): 'NS',
            ('PS', 'NB'): 'PS', ('PS', 'NS'): 'ZE', ('PS', 'ZE'): 'NS',
            ('PS', 'PS'): 'NS', ('PS', 'PB'): 'NB',
            ('PB', 'NB'): 'ZE', ('PB', 'NS'): 'NS', ('PB', 'ZE'): 'NB',
            ('PB', 'PS'): 'NB', ('PB', 'PB'): 'NB'
        }
        
        # Adaptive parameters
        self.scale_factors = {'error': 1.0, 'derror': 1.0, 'output': 1.0}
        self.adaptation_rate = 0.01
        
    def triangular_membership(self, x, params):
        """Calculate triangular membership function value."""
        a, b, c = params
        
        if x <= a or x >= c:
            return 0.0
        elif x <= b:
            return (x - a) / (b - a) if b != a else 1.0
        else:
            return (c - x) / (c - b) if c != b else 1.0
    
    def fuzzify(self, value, fuzzy_sets):
        """Fuzzify crisp input value."""
        memberships = {}
        for label, params in fuzzy_sets.items():
            memberships[label] = self.triangular_membership(value, params)
        return memberships
    
    def defuzzify(self, output_memberships):
        """Defuzzify using center of gravity method."""
        numerator = 0.0
        denominator = 0.0
        
        for label, membership in output_memberships.items():
            if membership > 0:
                # Center of triangular set
                center = self.output_sets[label][1]
                numerator += membership * center
                denominator += membership
        
        return numerator / denominator if denominator > 0 else 0.0
    
    def fuzzy_inference(self, error, derror):
        """Perform fuzzy inference."""
        
        # Scale inputs
        scaled_error = error * self.scale_factors['error']
        scaled_derror = derror * self.scale_factors['derror']
        
        # Fuzzification
        error_memberships = self.fuzzify(scaled_error, self.error_sets)
        derror_memberships = self.fuzzify(scaled_derror, self.derror_sets)
        
        # Rule evaluation
        output_memberships = {label: 0.0 for label in self.output_sets.keys()}
        
        for (error_label, derror_label), output_label in self.rules.items():
            # Rule strength (minimum of antecedents)
            rule_strength = min(error_memberships[error_label],
                              derror_memberships[derror_label])
            
            # Aggregate output (maximum)
            output_memberships[output_label] = max(
                output_memberships[output_label], rule_strength
            )
        
        # Defuzzification
        control_output = self.defuzzify(output_memberships)
        
        return control_output * self.scale_factors['output']
    
    def adapt_scaling_factors(self, performance_measure, dt):
        """Adapt fuzzy controller scaling factors."""
        
        # Simple adaptation based on performance
        # In practice, more sophisticated methods would be used
        
        if performance_measure > 1.0:  # Poor performance
            self.scale_factors['error'] *= (1 + self.adaptation_rate * dt)
            self.scale_factors['derror'] *= (1 + self.adaptation_rate * dt)
        elif performance_measure < 0.5:  # Good performance
            self.scale_factors['error'] *= (1 - self.adaptation_rate * dt * 0.5)
            self.scale_factors['derror'] *= (1 - self.adaptation_rate * dt * 0.5)
        
        # Limit scaling factors
        for key in self.scale_factors:
            self.scale_factors[key] = np.clip(self.scale_factors[key], 0.1, 10.0)
    
    def control_update(self, reference, plant_output, dt):
        """Fuzzy adaptive control update."""
        
        # Calculate error and error derivative
        error = reference - plant_output
        
        if not hasattr(self, 'previous_error'):
            self.previous_error = error
        
        derror = (error - self.previous_error) / dt
        self.previous_error = error
        
        # Fuzzy control
        control_signal = self.fuzzy_inference(error, derror)
        
        # Performance measure (for adaptation)
        performance = abs(error)  # Simplified measure
        
        # Adapt scaling factors
        self.adapt_scaling_factors(performance, dt)
        
        return control_signal
```

## Robust Adaptive Control

### L1 Adaptive Control

**L1 Adaptive Controller Implementation:**
```python
class L1AdaptiveController:
    def __init__(self, reference_model, low_pass_filter_bandwidth, adaptation_rate):
        """
        L1 adaptive controller with fast adaptation and robustness.
        
        Args:
            reference_model: Desired system behavior
            low_pass_filter_bandwidth: C(s) filter bandwidth for robustness
            adaptation_rate: Adaptation gain (large for fast adaptation)
        """
        self.Am = reference_model['Am']  # Reference model matrix
        self.Bm = reference_model['Bm']  # Reference model input matrix
        self.omega_c = low_pass_filter_bandwidth
        self.Gamma = adaptation_rate
        
        # State variables
        self.x_ref = 0.0      # Reference model state
        self.x_hat = 0.0      # State predictor
        self.sigma_hat = 0.0  # Uncertainty estimate
        self.u_ad = 0.0       # Adaptive control component
        
        # Low-pass filter for control signal
        self.filter_state = 0.0
        
    def update(self, reference, plant_output, dt):
        """L1 adaptive control update."""
        
        # Reference model
        dx_ref_dt = self.Am * self.x_ref + self.Bm * reference
        self.x_ref += dx_ref_dt * dt
        
        # State predictor (with uncertainty compensation)
        dx_hat_dt = self.Am * self.x_hat + self.Bm * (self.u_ad + reference)
        self.x_hat += dx_hat_dt * dt
        
        # Prediction error
        x_tilde = self.x_hat - plant_output
        
        # Adaptation law (fast adaptation)
        dsigma_dt = -self.Gamma * x_tilde * self.Bm
        self.sigma_hat += dsigma_dt * dt
        
        # Control law (before filtering)
        u_unfiltered = -self.sigma_hat
        
        # Low-pass filter for robustness (C(s) = omega_c / (s + omega_c))
        filter_error = u_unfiltered - self.filter_state
        dfilter_dt = self.omega_c * filter_error
        self.filter_state += dfilter_dt * dt
        self.u_ad = self.filter_state
        
        # Total control signal
        control_signal = reference + self.u_ad
        
        return control_signal, {
            'x_ref': self.x_ref,
            'x_hat': self.x_hat,
            'sigma_hat': self.sigma_hat,
            'u_ad': self.u_ad,
            'prediction_error': x_tilde
        }
```

### Sliding Mode Adaptive Control

**Adaptive Sliding Mode Controller:**
```python
class AdaptiveSlidingModeController:
    def __init__(self, sliding_surface_params, adaptation_law_params):
        """
        Adaptive sliding mode controller with uncertainty estimation.
        
        Args:
            sliding_surface_params: Parameters for sliding surface design
            adaptation_law_params: Parameters for adaptive law
        """
        self.lambda_s = sliding_surface_params['lambda']  # Sliding surface slope
        self.eta = sliding_surface_params['eta']          # Reaching law parameter
        self.phi = sliding_surface_params['phi']          # Boundary layer thickness
        
        self.gamma = adaptation_law_params['gamma']       # Adaptation rate
        self.sigma_max = adaptation_law_params['sigma_max']  # Max uncertainty bound
        
        # Adaptive parameters
        self.theta_hat = 0.0  # Uncertainty bound estimate
        
    def sliding_surface(self, error, derror):
        """Calculate sliding surface variable."""
        s = derror + self.lambda_s * error
        return s
    
    def reaching_law(self, s):
        """Reaching law for sliding mode control."""
        if abs(s) > self.phi:
            # Outside boundary layer - discontinuous control
            u_reach = -self.eta * np.sign(s)
        else:
            # Inside boundary layer - continuous control
            u_reach = -self.eta * s / self.phi
        
        return u_reach
    
    def adaptation_law(self, s, dt):
        """Adaptive law for uncertainty bound estimation."""
        
        # Adaptation law: dtheta/dt = gamma * |s|
        dtheta_dt = self.gamma * abs(s)
        self.theta_hat += dtheta_dt * dt
        
        # Saturation to prevent overestimation
        self.theta_hat = min(self.theta_hat, self.sigma_max)
        
        return self.theta_hat
    
    def control_update(self, reference, plant_output, plant_input_prev, dt):
        """Adaptive sliding mode control update."""
        
        # Calculate error and derivative
        error = reference - plant_output
        
        if not hasattr(self, 'previous_error'):
            self.previous_error = error
            
        derror = (error - self.previous_error) / dt
        self.previous_error = error
        
        # Sliding surface
        s = self.sliding_surface(error, derror)
        
        # Adaptation law
        theta_current = self.adaptation_law(s, dt)
        
        # Control law components
        u_equivalent = 0.0  # Would be calculated from system model
        u_reaching = self.reaching_law(s)
        u_adaptive = -theta_current * np.sign(s)
        
        # Total control signal
        control_signal = u_equivalent + u_reaching + u_adaptive
        
        return control_signal, {
            'sliding_surface': s,
            'theta_hat': self.theta_hat,
            'u_equivalent': u_equivalent,
            'u_reaching': u_reaching,
            'u_adaptive': u_adaptive
        }
```

## Practical Implementation Considerations

### Stability and Robustness

**Lyapunov-Based Design Verification:**
```python
def verify_adaptive_stability(controller_params, plant_bounds):
    """
    Verify adaptive controller stability using Lyapunov analysis.
    
    Args:
        controller_params: Controller design parameters
        plant_bounds: Known bounds on plant parameters
        
    Returns:
        stability_analysis: Dict with stability margins and conditions
    """
    
    # Example for MRAC stability verification
    Am = controller_params['reference_model']['Am']
    Gamma = controller_params['adaptation_rate']
    
    # Check SPR condition for reference model
    spr_condition = check_spr_condition(Am)
    
    # Calculate stability margins
    if spr_condition:
        # Lyapunov equation: Am^T P + P Am = -Q
        Q = np.eye(Am.shape[0])  # Positive definite matrix
        P = solve_lyapunov(Am.T, -Q)
        
        # Adaptation gain bounds for stability
        gamma_max = calculate_max_adaptation_gain(P, plant_bounds)
        
        stability_analysis = {
            'stable': np.all(np.linalg.eigvals(Gamma) < gamma_max),
            'spr_condition': spr_condition,
            'lyapunov_matrix': P,
            'max_adaptation_gain': gamma_max
        }
    else:
        stability_analysis = {
            'stable': False,
            'spr_condition': False,
            'recommendation': 'Redesign reference model for SPR property'
        }
    
    return stability_analysis

def check_spr_condition(Am):
    """Check Strictly Positive Real (SPR) condition."""
    # Implementation of SPR check
    # For single-input single-output case: check if transfer function is SPR
    pass

def calculate_max_adaptation_gain(P, plant_bounds):
    """Calculate maximum adaptation gain for stability."""
    # Implementation based on Lyapunov stability analysis
    pass
```

### Performance Monitoring and Diagnostics

**Adaptive Controller Health Monitoring:**
```python
class AdaptiveControlMonitor:
    def __init__(self, performance_thresholds):
        self.thresholds = performance_thresholds
        self.performance_history = {
            'tracking_error_rms': [],
            'parameter_variation': [],
            'adaptation_activity': [],
            'control_effort': []
        }
        self.alerts = []
        
    def update_performance_metrics(self, tracking_error, parameters, control_signal, dt):
        """Update performance monitoring metrics."""
        
        # RMS tracking error (sliding window)
        if not hasattr(self, 'error_window'):
            self.error_window = []
        
        self.error_window.append(tracking_error**2)
        if len(self.error_window) > 100:  # 100-sample window
            self.error_window.pop(0)
        
        rms_error = np.sqrt(np.mean(self.error_window))
        self.performance_history['tracking_error_rms'].append(rms_error)
        
        # Parameter variation rate
        if hasattr(self, 'previous_parameters'):
            param_change = np.linalg.norm(parameters - self.previous_parameters) / dt
            self.performance_history['parameter_variation'].append(param_change)
        
        self.previous_parameters = parameters.copy()
        
        # Control effort
        control_effort = abs(control_signal)
        self.performance_history['control_effort'].append(control_effort)
        
        # Check for alerts
        self.check_performance_alerts(rms_error, param_change if hasattr(self, 'previous_parameters') else 0)
        
    def check_performance_alerts(self, rms_error, param_change_rate):
        """Check for performance issues and generate alerts."""
        
        current_time = time.time()
        
        # High tracking error
        if rms_error > self.thresholds['max_tracking_error']:
            self.alerts.append({
                'time': current_time,
                'type': 'HIGH_TRACKING_ERROR',
                'value': rms_error,
                'severity': 'HIGH' if rms_error > 2 * self.thresholds['max_tracking_error'] else 'MEDIUM'
            })
        
        # Excessive parameter variation
        if param_change_rate > self.thresholds['max_parameter_change_rate']:
            self.alerts.append({
                'time': current_time,
                'type': 'EXCESSIVE_ADAPTATION',
                'value': param_change_rate,
                'severity': 'MEDIUM'
            })
        
        # Parameter drift detection
        if len(self.performance_history['parameter_variation']) > 1000:
            recent_variation = np.mean(self.performance_history['parameter_variation'][-100:])
            if recent_variation < 0.001:  # Very low adaptation activity
                self.alerts.append({
                    'time': current_time,
                    'type': 'PARAMETER_STAGNATION',
                    'value': recent_variation,
                    'severity': 'LOW'
                })
        
        # Keep only recent alerts
        self.alerts = [alert for alert in self.alerts 
                      if current_time - alert['time'] < 3600]  # Last hour
    
    def get_health_status(self):
        """Get overall health status of adaptive controller."""
        
        recent_alerts = [alert for alert in self.alerts 
                        if time.time() - alert['time'] < 300]  # Last 5 minutes
        
        high_severity_count = sum(1 for alert in recent_alerts if alert['severity'] == 'HIGH')
        medium_severity_count = sum(1 for alert in recent_alerts if alert['severity'] == 'MEDIUM')
        
        if high_severity_count > 0:
            return 'CRITICAL'
        elif medium_severity_count > 2:
            return 'WARNING'
        elif len(recent_alerts) > 5:
            return 'CAUTION'
        else:
            return 'HEALTHY'
```

## Advanced Applications

### Multi-Model Adaptive Control

**Multiple Model Adaptive Control (MMAC):**
```python
class MultipleModelAdaptiveController:
    def __init__(self, model_set, switching_threshold=0.1):
        """
        Multiple model adaptive control for systems with parameter jumps.
        
        Args:
            model_set: List of possible plant models
            switching_threshold: Threshold for model switching
        """
        self.models = model_set
        self.num_models = len(model_set)
        self.switching_threshold = switching_threshold
        
        # Model probabilities
        self.probabilities = np.ones(self.num_models) / self.num_models
        
        # Individual controllers for each model
        self.controllers = []
        for i, model in enumerate(self.models):
            controller = MRACController(model['reference'], model['adaptation_rate'])
            self.controllers.append(controller)
        
        # Active model index
        self.active_model = 0
        
    def update_model_probabilities(self, plant_output, control_signals, dt):
        """Update model probabilities based on prediction errors."""
        
        prediction_errors = np.zeros(self.num_models)
        
        for i, (model, controller) in enumerate(zip(self.models, self.controllers)):
            # Predict output for each model
            predicted_output = self.predict_model_output(model, control_signals[i], dt)
            prediction_errors[i] = abs(plant_output - predicted_output)
        
        # Update probabilities (Bayesian update)
        for i in range(self.num_models):
            # Likelihood (inverse of prediction error)
            likelihood = 1.0 / (1.0 + prediction_errors[i])
            self.probabilities[i] *= likelihood
        
        # Normalize probabilities
        prob_sum = np.sum(self.probabilities)
        if prob_sum > 0:
            self.probabilities /= prob_sum
        else:
            self.probabilities = np.ones(self.num_models) / self.num_models
        
    def select_active_model(self):
        """Select active model based on probabilities."""
        
        max_prob_index = np.argmax(self.probabilities)
        
        # Switch model if probability is significantly higher
        if (self.probabilities[max_prob_index] > self.switching_threshold and
            max_prob_index != self.active_model):
            
            self.active_model = max_prob_index
            print(f"Switched to model {self.active_model} (prob: {self.probabilities[max_prob_index]:.3f})")
        
        return self.active_model
    
    def control_update(self, reference, plant_output, dt):
        """MMAC control update."""
        
        # Update all controllers
        control_signals = []
        for controller in self.controllers:
            control_signal, _ = controller.update(reference, plant_output, 0.0, dt)
            control_signals.append(control_signal)
        
        # Update model probabilities
        self.update_model_probabilities(plant_output, control_signals, dt)
        
        # Select active model
        active_index = self.select_active_model()
        
        # Return control signal from active controller
        return control_signals[active_index], {
            'active_model': active_index,
            'model_probabilities': self.probabilities.copy(),
            'prediction_errors': [abs(plant_output - self.predict_model_output(
                self.models[i], control_signals[i], dt)) for i in range(self.num_models)]
        }
```

## Conclusion

Adaptive control strategies provide powerful tools for handling uncertainty, time-varying parameters, and changing operating conditions in control systems. Key aspects include:

1. **Model Reference Adaptive Control**: Direct adaptation of controller parameters to match desired behavior
2. **Self-Tuning Regulators**: Indirect adaptation through plant identification and controller redesign
3. **Neural/Fuzzy Adaptive**: Non-linear adaptive approaches for complex, uncertain systems
4. **Robust Adaptive**: Methods ensuring stability despite modeling errors and disturbances
5. **Multiple Model Adaptive**: Handling discrete parameter changes and multiple operating modes

Success factors for adaptive control implementation:
- **Stability Assurance**: Rigorous stability analysis and verification
- **Performance Monitoring**: Continuous health assessment and diagnostics
- **Robustness**: Handling unmodeled dynamics and disturbances
- **Practical Constraints**: Consideration of actuator limits and computational requirements

Modern adaptive control benefits from:
- **Machine Learning**: Integration with neural networks and reinforcement learning
- **Data-Driven Methods**: Utilizing large datasets for better adaptation
- **Distributed Systems**: Adaptive control for networked and multi-agent systems
- **Safety Guarantees**: Ensuring safe adaptation in critical applications

The future of adaptive control emphasizes intelligent systems that can:
- Learn optimal behavior from minimal prior knowledge
- Guarantee safety and stability during adaptation
- Handle complex, multi-physics systems with strong coupling
- Operate reliably in safety-critical applications

These advanced adaptive strategies enable control systems to maintain optimal performance despite significant uncertainties, parameter variations, and changing operational requirements.

---

*This comprehensive guide provides theoretical foundations and practical implementations for adaptive control strategies. Specific applications require careful stability analysis and performance validation.*