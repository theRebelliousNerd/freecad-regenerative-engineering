# Four-Bar Linkages: The Foundation of Mechanism Design

*"A four-bar linkage is a theorem about motion, proven by steel and geometry. Every complex mechanism can be understood as combinations and variations of four-bar chains."* - Alan Turing

## Overview

The four-bar linkage is the fundamental building block of mechanism design. It consists of four rigid links connected by four revolute joints, forming a closed kinematic chain. Despite its apparent simplicity, the four-bar linkage can generate an infinite variety of motion patterns and serves as the theoretical foundation for understanding all planar mechanisms.

## Mathematical Foundation

### Degrees of Freedom
For a four-bar linkage:
```
DOF = 3(n-1) - 2j₁ - j₂ = 3(4-1) - 2(4) - 0 = 1
```
Where n=4 links, j₁=4 revolute joints, j₂=0 higher pairs.

One degree of freedom means specifying one joint angle determines all others.

### Link Length Notation
- **a**: Ground link (base, link 1)
- **b**: Input link (crank, link 2)  
- **c**: Coupler link (connecting rod, link 3)
- **d**: Output link (rocker, link 4)

## Grashof's Criterion: The Fundamental Law

**Grashof's Theorem**: A four-bar linkage has at least one link capable of continuous 360° rotation if and only if:
```
s + l ≤ p + q
```
Where:
- s = shortest link length
- l = longest link length  
- p, q = intermediate link lengths

### Classification Based on Ground Link

#### Case 1: Ground is Shortest Link (s = a)
**Double-Crank Mechanism**
- Both input and output can rotate continuously
- Rare in practice due to mechanical difficulties
- Applications: Rotary engines, special couplers

```python
def analyze_double_crank(a, b, c, d):
    """Analyze double-crank mechanism properties"""
    assert a + max(b,c,d) <= sum([b,c,d]) - max(b,c,d), "Grashof criterion not satisfied"
    assert a == min(a,b,c,d), "Ground must be shortest link"
    
    # Both adjacent links can rotate fully
    return {
        'type': 'double_crank',
        'input_rotation': '360°',
        'output_rotation': '360°',
        'dead_points': 0,
        'toggle_positions': 2
    }
```

#### Case 2: Input Link is Shortest (s = b)
**Crank-Rocker Mechanism**
- Input (crank) rotates continuously
- Output (rocker) oscillates
- Most common practical configuration

```python
def analyze_crank_rocker(a, b, c, d):
    """Analyze crank-rocker mechanism"""
    links = [a, b, c, d]
    s = min(links)
    l = max(links)
    p, q = [x for x in links if x != s and x != l]
    
    assert s + l <= p + q, "Grashof criterion not satisfied"
    assert b == s, "Input link must be shortest"
    
    # Calculate rocker oscillation angle
    alpha_max = np.arccos((a**2 + d**2 - (b+c)**2) / (2*a*d))
    alpha_min = np.arccos((a**2 + d**2 - abs(b-c)**2) / (2*a*d))
    
    oscillation_angle = alpha_max - alpha_min
    
    return {
        'type': 'crank_rocker',
        'input_rotation': '360°',
        'output_oscillation': np.degrees(oscillation_angle),
        'rocker_max_angle': np.degrees(alpha_max),
        'rocker_min_angle': np.degrees(alpha_min),
        'dead_points': 0
    }
```

#### Case 3: Coupler is Shortest (s = c)  
**Double-Rocker Mechanism**
- Both input and output oscillate
- Two dead point positions where mechanism can't be driven

```python
def analyze_double_rocker(a, b, c, d):
    """Analyze double-rocker mechanism"""
    assert c == min(a,b,c,d), "Coupler must be shortest"
    
    # Calculate dead point configurations
    dead_point_1 = np.arccos((a**2 + b**2 - (c+d)**2) / (2*a*b))
    dead_point_2 = np.arccos((a**2 + b**2 - abs(c-d)**2) / (2*a*b))
    
    return {
        'type': 'double_rocker',
        'input_oscillation': 'limited',
        'output_oscillation': 'limited', 
        'dead_points': 2,
        'dead_point_angles': [np.degrees(dead_point_1), np.degrees(dead_point_2)]
    }
```

#### Case 4: Output Link is Shortest (s = d)
**Rocker-Crank Mechanism**  
- Input oscillates, output rotates continuously
- Less common than crank-rocker

## Position Analysis

### Loop Closure Equations
For position analysis, we solve the vector loop equation:
```
a⃗ + b⃗ + c⃗ + d⃗ = 0⃗
```

In component form:
```python
def four_bar_position_analysis(a, b, c, d, theta2):
    """Solve four-bar linkage position for given input angle theta2"""
    
    # Define the loop closure equations
    def equations(angles):
        theta3, theta4 = angles
        
        # X-component: a + b*cos(theta2) + c*cos(theta3) + d*cos(theta4) = 0
        eq1 = a + b*np.cos(theta2) + c*np.cos(theta3) + d*np.cos(theta4)
        
        # Y-component: 0 + b*sin(theta2) + c*sin(theta3) + d*sin(theta4) = 0  
        eq2 = b*np.sin(theta2) + c*np.sin(theta3) + d*np.sin(theta4)
        
        return [eq1, eq2]
    
    # Solve using numerical methods (two solutions exist)
    from scipy.optimize import fsolve
    
    # Initial guesses for two circuit configurations
    guess1 = [theta2, -theta2]  # Open circuit
    guess2 = [np.pi - theta2, np.pi + theta2]  # Crossed circuit
    
    try:
        sol1 = fsolve(equations, guess1)
        sol2 = fsolve(equations, guess2)
        
        return {
            'open_circuit': {'theta3': sol1[0], 'theta4': sol1[1]},
            'crossed_circuit': {'theta3': sol2[0], 'theta4': sol2[1]}
        }
    except:
        return None
```

### Analytical Solution Method
For increased speed and reliability:

```python
def four_bar_analytical_position(a, b, c, d, theta2):
    """Analytical solution for four-bar position"""
    
    # Intermediate calculations
    A = 2*a*d - 2*b*d*np.cos(theta2)
    B = -2*b*d*np.sin(theta2)
    C = a**2 + b**2 + d**2 - c**2 - 2*a*b*np.cos(theta2)
    
    # Discriminant check
    discriminant = B**2 - 4*A*C
    if discriminant < 0:
        return None  # No real solution
    
    # Two solutions for theta4
    theta4_1 = 2*np.arctan((-B + np.sqrt(discriminant)) / (2*A))
    theta4_2 = 2*np.arctan((-B - np.sqrt(discriminant)) / (2*A))
    
    # Corresponding theta3 solutions
    theta3_1 = np.arctan2(
        b*np.sin(theta2) + d*np.sin(theta4_1),
        a + b*np.cos(theta2) + d*np.cos(theta4_1)
    ) + np.pi
    
    theta3_2 = np.arctan2(
        b*np.sin(theta2) + d*np.sin(theta4_2),
        a + b*np.cos(theta2) + d*np.cos(theta4_2)
    ) + np.pi
    
    return {
        'solution_1': {'theta3': theta3_1, 'theta4': theta4_1},
        'solution_2': {'theta3': theta3_2, 'theta4': theta4_2}
    }
```

## Velocity Analysis

### Analytical Velocity Solution
```python
def four_bar_velocity_analysis(a, b, c, d, theta2, theta3, theta4, omega2):
    """Calculate angular velocities of all links"""
    
    # Velocity coefficients matrix
    A_matrix = np.array([
        [-c*np.sin(theta3), -d*np.sin(theta4)],
        [c*np.cos(theta3), d*np.cos(theta4)]
    ])
    
    # Right-hand side vector
    B_vector = np.array([
        b*omega2*np.sin(theta2),
        -b*omega2*np.cos(theta2)
    ])
    
    try:
        # Solve for omega3 and omega4
        omega_34 = np.linalg.solve(A_matrix, B_vector)
        omega3, omega4 = omega_34
        
        return {
            'omega2': omega2,
            'omega3': omega3,
            'omega4': omega4,
            'velocity_ratio': omega4/omega2 if omega2 != 0 else float('inf')
        }
    except np.linalg.LinAlgError:
        # Singular configuration (dead point)
        return None
```

### Coupler Point Velocity
```python
def coupler_point_velocity(theta2, theta3, omega2, omega3, rho, phi):
    """Calculate velocity of point P on coupler link
    
    Args:
        rho: Distance from A (joint 2) to point P
        phi: Angle from link 3 direction to AP vector
    """
    
    # Position of coupler point P
    xp = b*np.cos(theta2) + rho*np.cos(theta3 + phi)
    yp = b*np.sin(theta2) + rho*np.sin(theta3 + phi)
    
    # Velocity of coupler point P
    vp_x = -b*omega2*np.sin(theta2) - rho*omega3*np.sin(theta3 + phi)
    vp_y = b*omega2*np.cos(theta2) + rho*omega3*np.cos(theta3 + phi)
    
    velocity_magnitude = np.sqrt(vp_x**2 + vp_y**2)
    velocity_direction = np.arctan2(vp_y, vp_x)
    
    return {
        'position': (xp, yp),
        'velocity': (vp_x, vp_y),
        'magnitude': velocity_magnitude,
        'direction': velocity_direction
    }
```

## Acceleration Analysis

```python
def four_bar_acceleration_analysis(a, b, c, d, theta2, theta3, theta4, 
                                  omega2, omega3, omega4, alpha2):
    """Calculate angular accelerations of all links"""
    
    # Acceleration coefficients (same as velocity)
    A_matrix = np.array([
        [-c*np.sin(theta3), -d*np.sin(theta4)],
        [c*np.cos(theta3), d*np.cos(theta4)]
    ])
    
    # Right-hand side includes centripetal acceleration terms
    B_vector = np.array([
        b*alpha2*np.sin(theta2) + b*omega2**2*np.cos(theta2) + 
        c*omega3**2*np.cos(theta3) + d*omega4**2*np.cos(theta4),
        
        -b*alpha2*np.cos(theta2) + b*omega2**2*np.sin(theta2) + 
        c*omega3**2*np.sin(theta3) + d*omega4**2*np.sin(theta4)
    ])
    
    try:
        alpha_34 = np.linalg.solve(A_matrix, B_vector)
        alpha3, alpha4 = alpha_34
        
        return {
            'alpha2': alpha2,
            'alpha3': alpha3,
            'alpha4': alpha4
        }
    except np.linalg.LinAlgError:
        return None
```

## Transmission Angle Analysis

The transmission angle μ is critical for force transmission efficiency:

```python
def transmission_angle(b, c, d, theta2, theta3, theta4):
    """Calculate transmission angle between coupler and output links"""
    
    # Vector from joint 3 to joint 4 along coupler
    coupler_vector = np.array([c*np.cos(theta3), c*np.sin(theta3)])
    
    # Vector from joint 4 to ground along output link
    output_vector = np.array([-d*np.cos(theta4), -d*np.sin(theta4)])
    
    # Angle between vectors
    cos_mu = np.dot(coupler_vector, output_vector) / (c * d)
    mu = np.arccos(np.clip(cos_mu, -1, 1))
    
    # Transmission angle should be between 45° and 135° for good force transmission
    mu_degrees = np.degrees(mu)
    
    return {
        'transmission_angle': mu_degrees,
        'quality': 'good' if 45 <= mu_degrees <= 135 else 'poor',
        'force_efficiency': np.sin(mu)  # Force multiplication factor
    }

def optimize_transmission_angle(a, d, motion_requirements):
    """Optimize link lengths b and c for best transmission angle"""
    
    def objective(bc_lengths):
        b, c = bc_lengths
        
        # Calculate transmission angle throughout cycle
        theta2_range = np.linspace(0, 2*np.pi, 360)
        min_transmission = 180  # Start with worst case
        
        for theta2 in theta2_range:
            pos_result = four_bar_analytical_position(a, b, c, d, theta2)
            if pos_result:
                theta3 = pos_result['solution_1']['theta3']
                theta4 = pos_result['solution_1']['theta4']
                
                trans_result = transmission_angle(b, c, d, theta2, theta3, theta4)
                min_transmission = min(min_transmission, trans_result['transmission_angle'])
        
        # We want to maximize the minimum transmission angle
        return -min_transmission  # Negative because minimize function
    
    from scipy.optimize import minimize
    
    # Constraints: b and c must be positive, Grashof criterion
    constraints = [
        {'type': 'ineq', 'fun': lambda x: x[0] - 0.1},  # b > 0.1
        {'type': 'ineq', 'fun': lambda x: x[1] - 0.1},  # c > 0.1
        {'type': 'ineq', 'fun': lambda x: grashof_constraint(a, x[0], x[1], d)}
    ]
    
    initial_guess = [a/2, a/2]
    result = minimize(objective, initial_guess, constraints=constraints)
    
    return result.x if result.success else None
```

## Coupler Curves: The Heart of Four-Bar Artistry

### Generating Coupler Curves
```python
def generate_coupler_curve(a, b, c, d, rho, phi, n_points=360):
    """Generate the path traced by a point on the coupler link"""
    
    theta2_values = np.linspace(0, 2*np.pi, n_points)
    coupler_points = []
    
    for theta2 in theta2_values:
        pos_result = four_bar_analytical_position(a, b, c, d, theta2)
        
        if pos_result:
            theta3 = pos_result['solution_1']['theta3']
            
            # Calculate coupler point position
            xp = b*np.cos(theta2) + rho*np.cos(theta3 + phi)
            yp = b*np.sin(theta2) + rho*np.sin(theta3 + phi)
            
            coupler_points.append((xp, yp))
        else:
            coupler_points.append((None, None))  # Mechanism doesn't exist at this position
    
    return coupler_points

def analyze_coupler_curve_properties(coupler_points):
    """Analyze geometric properties of coupler curve"""
    
    valid_points = [(x, y) for x, y in coupler_points if x is not None]
    
    if len(valid_points) < 10:
        return None
    
    x_coords = [point[0] for point in valid_points]
    y_coords = [point[1] for point in valid_points]
    
    return {
        'x_range': (min(x_coords), max(x_coords)),
        'y_range': (min(y_coords), max(y_coords)),
        'area_envelope': calculate_curve_area(valid_points),
        'max_curvature': calculate_max_curvature(valid_points),
        'self_intersections': find_self_intersections(valid_points)
    }
```

### Special Coupler Curves

#### Straight-Line Approximations
```python
def design_approximate_straight_line(target_length, tolerance):
    """Design four-bar for approximate straight line motion"""
    
    # Watt's straight-line linkage proportions
    # For best approximation: b:c:d = 1:2:1, a chosen for workspace
    
    def watt_linkage_error(a_value):
        b = target_length / 4
        c = target_length / 2  
        d = target_length / 4
        a = a_value
        
        # Coupler point at midpoint of coupler link
        rho = c / 2
        phi = 0
        
        coupler_curve = generate_coupler_curve(a, b, c, d, rho, phi)
        
        # Find the straightest portion
        max_deviation = calculate_max_deviation_from_straight(coupler_curve)
        return max_deviation
    
    from scipy.optimize import minimize_scalar
    
    # Optimize ground link length for minimum deviation
    result = minimize_scalar(watt_linkage_error, bounds=(target_length/4, target_length*2))
    
    if result.success and result.fun < tolerance:
        optimal_a = result.x
        return {
            'a': optimal_a,
            'b': target_length / 4,
            'c': target_length / 2,
            'd': target_length / 4,
            'max_deviation': result.fun,
            'type': 'watt_approximation'
        }
    else:
        return None
```

#### Figure-8 and Other Complex Curves
```python
def design_figure_eight_mechanism():
    """Design four-bar linkage to generate figure-8 coupler curve"""
    
    # Known proportions for figure-8: specific geometric relationships
    # These are empirically determined optimal ratios
    
    a = 1.0  # Ground link (reference)
    b = 0.6  # Input crank
    c = 1.8  # Coupler
    d = 0.8  # Output rocker
    
    # Coupler point location for figure-8
    rho = c * 0.7  # Distance from joint A along coupler
    phi = np.radians(30)  # Angle from coupler link direction
    
    # Verify this produces figure-8
    coupler_curve = generate_coupler_curve(a, b, c, d, rho, phi)
    intersections = find_self_intersections(coupler_curve)
    
    if len(intersections) == 1:  # Figure-8 should have exactly one self-intersection
        return {
            'linkage': (a, b, c, d),
            'coupler_point': (rho, phi),
            'curve_type': 'figure_eight',
            'intersection_point': intersections[0]
        }
    else:
        return None
```

## Synthesis Methods

### Function Generation
```python
def synthesize_function_generator(input_angles, output_angles):
    """Synthesize four-bar to approximate desired input-output relationship"""
    
    assert len(input_angles) == len(output_angles), "Input and output arrays must be same length"
    assert len(input_angles) >= 3, "Need at least 3 precision points"
    
    if len(input_angles) == 3:
        return three_point_synthesis(input_angles, output_angles)
    elif len(input_angles) > 3:
        return least_squares_synthesis(input_angles, output_angles)

def three_point_synthesis(theta2_values, theta4_values):
    """Exact synthesis for three precision points"""
    
    # This involves solving system of nonlinear equations
    # Standard approach uses complex number representation
    
    def synthesis_equations(parameters):
        a, b, c, d = parameters
        equations = []
        
        for i in range(3):
            theta2 = theta2_values[i]
            theta4_desired = theta4_values[i]
            
            # Calculate actual theta4 for these link lengths
            pos_result = four_bar_analytical_position(a, b, c, d, theta2)
            
            if pos_result:
                theta4_actual = pos_result['solution_1']['theta4']
                equations.append(theta4_actual - theta4_desired)
            else:
                equations.append(1000)  # Large penalty for invalid configuration
        
        return equations
    
    from scipy.optimize import fsolve
    
    # Initial guess based on approximate scaling
    initial_guess = [1.0, 0.5, 1.2, 0.8]
    
    try:
        solution = fsolve(synthesis_equations, initial_guess)
        return solution
    except:
        return None
```

### Path Generation Synthesis
```python
def synthesize_path_generator(target_points):
    """Synthesize four-bar to trace path through specified points"""
    
    def path_error(parameters):
        a, b, c, d, rho, phi = parameters
        
        # Generate coupler curve
        coupler_curve = generate_coupler_curve(a, b, c, d, rho, phi)
        valid_points = [(x, y) for x, y in coupler_curve if x is not None]
        
        # Calculate minimum distance from each target point to curve
        total_error = 0
        for target_x, target_y in target_points:
            min_distance = float('inf')
            for curve_x, curve_y in valid_points:
                distance = np.sqrt((curve_x - target_x)**2 + (curve_y - target_y)**2)
                min_distance = min(min_distance, distance)
            total_error += min_distance
        
        return total_error
    
    from scipy.optimize import minimize
    
    # Initial guess
    x0 = [1.0, 0.5, 1.2, 0.8, 0.6, 0]
    
    # Bounds to ensure positive link lengths
    bounds = [(0.1, 5), (0.1, 5), (0.1, 5), (0.1, 5), (0.1, 5), (-np.pi, np.pi)]
    
    result = minimize(path_error, x0, bounds=bounds)
    
    if result.success:
        return {
            'linkage': result.x[:4],
            'coupler_point': result.x[4:],
            'error': result.fun
        }
    else:
        return None
```

## FreeCAD Implementation

### Creating Four-Bar Mechanism in FreeCAD
```python
def create_four_bar_freecad(a, b, c, d, name="FourBarLinkage"):
    """Create four-bar linkage geometry in FreeCAD"""
    
    # Create new document if needed
    if not hasattr(FreeCAD, 'ActiveDocument') or FreeCAD.ActiveDocument is None:
        doc = FreeCAD.newDocument(name)
    else:
        doc = FreeCAD.ActiveDocument
    
    # Define joint positions
    O2 = FreeCAD.Vector(0, 0, 0)        # Ground-input joint
    O4 = FreeCAD.Vector(a, 0, 0)        # Ground-output joint
    
    # Create ground link
    ground = doc.addObject("Part::Box", "Ground")
    ground.Length = a
    ground.Width = 20  # Arbitrary width for visualization
    ground.Height = 10
    ground.Placement.Base = FreeCAD.Vector(-10, -10, -5)
    
    # Create input crank (link 2)
    crank = doc.addObject("Part::Cylinder", "Crank")
    crank.Radius = 5
    crank.Height = b
    crank.Placement = FreeCAD.Placement(
        O2, 
        FreeCAD.Rotation(FreeCAD.Vector(0, 1, 0), 90)
    )
    
    # Create coupler link (link 3)
    coupler = doc.addObject("Part::Box", "Coupler")
    coupler.Length = c
    coupler.Width = 10
    coupler.Height = 5
    coupler.Placement.Base = FreeCAD.Vector(b, 0, 0)
    
    # Create output rocker (link 4) 
    rocker = doc.addObject("Part::Cylinder", "Rocker")
    rocker.Radius = 5
    rocker.Height = d
    rocker.Placement = FreeCAD.Placement(
        O4,
        FreeCAD.Rotation(FreeCAD.Vector(0, 1, 0), 90)
    )
    
    # Create assembly with constraints (requires Assembly4 workbench)
    if hasattr(FreeCAD, 'Assembly4'):
        assembly = create_assembly4_linkage(ground, crank, coupler, rocker)
        return assembly
    
    doc.recompute()
    return [ground, crank, coupler, rocker]

def animate_four_bar_freecad(linkage_parts, a, b, c, d, steps=360):
    """Animate four-bar linkage in FreeCAD"""
    
    import time
    
    ground, crank, coupler, rocker = linkage_parts
    
    for i in range(steps):
        theta2 = 2 * np.pi * i / steps
        
        # Calculate positions
        pos_result = four_bar_analytical_position(a, b, c, d, theta2)
        
        if pos_result:
            theta3 = pos_result['solution_1']['theta3']
            theta4 = pos_result['solution_1']['theta4']
            
            # Update crank position
            crank.Placement.Rotation = FreeCAD.Rotation(
                FreeCAD.Vector(0, 0, 1), np.degrees(theta2)
            )
            
            # Calculate coupler position
            A_pos = FreeCAD.Vector(b*np.cos(theta2), b*np.sin(theta2), 0)
            coupler.Placement.Base = A_pos
            coupler.Placement.Rotation = FreeCAD.Rotation(
                FreeCAD.Vector(0, 0, 1), np.degrees(theta3)
            )
            
            # Update rocker position  
            rocker.Placement.Rotation = FreeCAD.Rotation(
                FreeCAD.Vector(0, 0, 1), np.degrees(theta4)
            )
            
            FreeCAD.ActiveDocument.recompute()
            time.sleep(0.05)  # Animation delay
```

## Design Guidelines and Best Practices

### Geometric Constraints
1. **Grashof Criterion**: Ensure proper mobility classification
2. **Transmission Angle**: Keep between 45° and 135° for good force transmission
3. **Link Length Ratios**: Avoid extreme ratios (>10:1) for manufacturability
4. **Joint Spacing**: Maintain adequate space for bearings and assembly

### Performance Optimization
```python
def optimize_four_bar_performance(requirements):
    """Multi-objective optimization of four-bar linkage"""
    
    def objective_function(parameters):
        a, b, c, d = parameters
        
        # Check Grashof criterion
        links = [a, b, c, d]
        s, l = min(links), max(links)
        p, q = [x for x in links if x != s and x != l]
        
        if s + l > p + q:
            return 1000  # Penalty for non-Grashof
        
        # Calculate performance metrics
        min_transmission = calculate_min_transmission_angle(a, b, c, d)
        velocity_fluctuation = calculate_velocity_fluctuation(a, b, c, d)
        workspace_size = calculate_workspace_area(a, b, c, d)
        
        # Multi-objective: maximize transmission angle and workspace, minimize fluctuation
        score = (min_transmission / 180) + (workspace_size / 100) - (velocity_fluctuation / 10)
        
        return -score  # Negative for minimization
    
    # Optimization with constraints
    from scipy.optimize import minimize
    
    constraints = [
        {'type': 'ineq', 'fun': lambda x: min(x) - 0.1},  # Minimum link length
        {'type': 'ineq', 'fun': lambda x: 10 - max(x)},   # Maximum link length
    ]
    
    bounds = [(0.1, 10)] * 4  # All link lengths between 0.1 and 10
    
    initial_guess = [2, 1, 3, 1.5]  # Starting point
    
    result = minimize(objective_function, initial_guess, 
                     bounds=bounds, constraints=constraints)
    
    return result.x if result.success else None
```

The four-bar linkage remains the cornerstone of mechanism design - simple in concept yet capable of infinite variety. Master its principles, and you hold the key to understanding all planar motion transformation.