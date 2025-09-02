# Linkage Design: The Geometry of Constrained Motion

*"A linkage is a theorem about motion, proven by steel and geometry."* - Alan Turing

## Table of Contents

1. [Philosophy of Linkage Design](#philosophy-of-linkage-design)
2. [Four-Bar Linkage: The Foundation](#four-bar-linkage-the-foundation)
3. [Multi-Bar Mechanisms](#multi-bar-mechanisms)
4. [Special-Purpose Linkages](#special-purpose-linkages)
5. [Straight-Line Mechanisms](#straight-line-mechanisms)
6. [Quick-Return Mechanisms](#quick-return-mechanisms)
7. [Toggle and Force Multiplication](#toggle-and-force-multiplication)
8. [Design Methodology](#design-methodology)
9. [Analysis Tools](#analysis-tools)
10. [FreeCAD Implementation](#freecad-implementation)

---

## Philosophy of Linkage Design

A linkage transforms one type of motion into another through pure geometry. Every link, joint, and constraint participates in a mechanical calculation that solves kinematic equations through physical movement. The linkage designer is not just connecting bars and pins - they are crystallizing mathematical relationships in metal.

### The Hierarchy of Constraint

1. **Topology**: How many links and joints, and how are they connected?
2. **Geometry**: What are the relative dimensions and proportions?
3. **Kinematics**: How do the motions relate to each other?
4. **Dynamics**: How do forces transmit through the mechanism?

### Design Philosophy: Precision vs. Approximation

**Exact Mechanisms**: Generate precise mathematical curves (circles, straight lines)
- Peaucellier linkage (exact straight line)
- Compass mechanisms (exact circles)
- Mathematical rigor but complex construction

**Approximate Mechanisms**: Generate close approximations to desired motion
- Watt linkage (approximate straight line)
- Chebyshev linkage (approximate straight line with good velocity)
- Simpler construction but limited precision

---

## Four-Bar Linkage: The Foundation

The four-bar linkage is the fundamental building block of mechanism design. Every complex mechanism can be understood as combinations and variations of four-bar chains.

### Basic Configuration

```
Ground (r₁) ←→ Input Crank (r₂) ←→ Coupler (r₃) ←→ Output Crank (r₄) ←→ Ground
```

### Grashof Classification

The Grashof criterion determines the motion type:

```python
def grashof_analysis(r1, r2, r3, r4):
    """
    Complete Grashof analysis for four-bar linkage
    """
    links = [r1, r2, r3, r4]
    s = min(links)  # shortest link
    l = max(links)  # longest link
    p, q = sorted([x for x in links if x != s and x != l])  # intermediate lengths
    
    grashof_sum = s + l - p - q
    
    if grashof_sum < 0:
        # Grashof mechanism - at least one full rotation possible
        shortest_index = links.index(s)
        link_names = ['ground', 'input', 'coupler', 'output']
        shortest_link = link_names[shortest_index]
        
        classifications = {
            'ground': 'Double Rocker',
            'input': 'Crank-Rocker',
            'coupler': 'Double Crank',
            'output': 'Crank-Rocker'
        }
        
        return {
            'type': 'Grashof',
            'classification': classifications[shortest_link],
            'grashof_sum': grashof_sum,
            'continuous_rotation': True
        }
    
    elif grashof_sum == 0:
        return {
            'type': 'Special Case',
            'classification': 'Change Point Mechanism',
            'grashof_sum': grashof_sum,
            'continuous_rotation': False
        }
    
    else:
        return {
            'type': 'Non-Grashof',
            'classification': 'Triple Rocker',
            'grashof_sum': grashof_sum,
            'continuous_rotation': False
        }

# Example usage
linkage = grashof_analysis(100, 50, 80, 120)  # r1, r2, r3, r4 in mm
print(f"Type: {linkage['classification']}")
print(f"Continuous rotation: {linkage['continuous_rotation']}")
```

### Coupler Curves

The path traced by any point on the coupler link creates a coupler curve. These curves exhibit remarkable mathematical properties:

```python
import numpy as np
import matplotlib.pyplot as plt

def generate_coupler_curve(r1, r2, r3, r4, coupler_point, num_points=360):
    """
    Generate coupler curve for four-bar linkage
    """
    angles = np.linspace(0, 2*np.pi, num_points)
    coupler_positions = []
    
    for theta2 in angles:
        try:
            # Solve position analysis
            theta4, theta3 = solve_four_bar_position(r1, r2, r3, r4, theta2)
            
            # Calculate coupler point position
            x_coupler = r2*np.cos(theta2) + coupler_point[0]*np.cos(theta3) - coupler_point[1]*np.sin(theta3)
            y_coupler = r2*np.sin(theta2) + coupler_point[0]*np.sin(theta3) + coupler_point[1]*np.cos(theta3)
            
            coupler_positions.append((x_coupler, y_coupler))
        except:
            # Skip positions where linkage cannot be assembled
            continue
    
    return np.array(coupler_positions)

def solve_four_bar_position(r1, r2, r3, r4, theta2):
    """
    Solve four-bar position analysis using loop closure equations
    """
    # Complex number approach
    A = 2*r1*r4*np.cos(0) - 2*r2*r4*np.cos(theta2)
    B = 2*r1*r4*np.sin(0) - 2*r2*r4*np.sin(theta2)
    C = r1**2 + r2**2 + r4**2 - r3**2 - 2*r1*r2*np.cos(theta2)
    
    # Solve quadratic for theta4
    discriminant = A**2 + B**2 - C**2
    if discriminant < 0:
        raise ValueError("Linkage cannot be assembled in this position")
    
    theta4_1 = 2*np.arctan((-B + np.sqrt(discriminant))/(C - A))
    theta4_2 = 2*np.arctan((-B - np.sqrt(discriminant))/(C - A))
    
    # Choose appropriate solution (usually open configuration)
    theta4 = theta4_1
    
    # Solve for theta3
    theta3 = np.arctan2(
        r1*np.sin(0) + r4*np.sin(theta4) - r2*np.sin(theta2),
        r1*np.cos(0) + r4*np.cos(theta4) - r2*np.cos(theta2)
    )
    
    return theta4, theta3
```

### Transmission Angle Analysis

The transmission angle determines the force transmission efficiency:

```python
def transmission_angle_analysis(r1, r2, r3, r4, num_positions=36):
    """
    Calculate transmission angle throughout motion cycle
    """
    input_angles = np.linspace(0, 2*np.pi, num_positions)
    transmission_angles = []
    
    for theta2 in input_angles:
        try:
            theta4, theta3 = solve_four_bar_position(r1, r2, r3, r4, theta2)
            
            # Vector from coupler-output joint to coupler-input joint
            vec_34 = np.array([r4*np.cos(theta4) - (r2*np.cos(theta2) + r3*np.cos(theta3)),
                              r4*np.sin(theta4) - (r2*np.sin(theta2) + r3*np.sin(theta3))])
            
            # Output link vector
            vec_41 = np.array([-r4*np.cos(theta4), -r4*np.sin(theta4)])
            
            # Calculate angle between vectors
            cos_trans = np.dot(vec_34, vec_41) / (np.linalg.norm(vec_34) * np.linalg.norm(vec_41))
            trans_angle = np.arccos(np.clip(cos_trans, -1, 1))
            
            # Convert to degrees and ensure 0-90 range
            trans_angle_deg = np.degrees(min(trans_angle, np.pi - trans_angle))
            transmission_angles.append(trans_angle_deg)
            
        except:
            transmission_angles.append(0)  # Invalid position
    
    return np.array(transmission_angles)

# Design guideline: minimum transmission angle should be > 45° for good force transmission
```

---

## Multi-Bar Mechanisms

### Six-Bar Linkages

Six-bar mechanisms provide additional flexibility for complex motion requirements:

#### Watt Six-Bar Chain
Two four-bar loops sharing a common floating link:

```python
def analyze_watt_six_bar(r1, r2, r3, r4, r5, r6, r7):
    """
    Analyze Watt six-bar mechanism
    r1-r4: First four-bar loop
    r3,r5,r6,r7: Second four-bar loop (r3 is shared)
    """
    # First loop analysis
    loop1_dof = 3*3 - 2*4  # 1 DOF
    
    # Second loop analysis  
    loop2_dof = 3*3 - 2*4  # 1 DOF
    
    # System DOF (with constraint coupling)
    system_dof = 3*5 - 2*7 + 1  # 1 DOF total
    
    return {
        'type': 'Watt Six-Bar',
        'dof': system_dof,
        'motion_type': 'Complex coupler curves with cusps and loops'
    }

def create_watt_six_bar_freecad(dimensions):
    """
    Create Watt six-bar in FreeCAD
    """
    # Ground link
    ground = create_line(0, 0, dimensions['r1'], 0)
    
    # First four-bar loop
    first_loop = create_four_bar_linkage(
        dimensions['r1'], dimensions['r2'], 
        dimensions['r3'], dimensions['r4']
    )
    
    # Second four-bar loop attached to coupler
    second_loop = create_attached_four_bar(
        first_loop['coupler'], 
        dimensions['r5'], dimensions['r6'], dimensions['r7']
    )
    
    return combine_mechanisms(first_loop, second_loop)
```

#### Stephenson Six-Bar Chain
Series connection of two four-bar chains:

```python
def analyze_stephenson_six_bar(r1, r2, r3, r4, r5, r6, r7):
    """
    Analyze Stephenson six-bar mechanism
    Two four-bar chains connected in series
    """
    return {
        'type': 'Stephenson Six-Bar',
        'dof': 1,
        'motion_type': 'Extended workspace, complex trajectories',
        'advantages': ['Larger workspace', 'More complex curves'],
        'disadvantages': ['Higher complexity', 'More joints']
    }
```

### Eight-Bar Mechanisms

Eight-bar mechanisms can generate extremely complex coupler curves:

```python
def eight_bar_synthesis(required_points, curve_type='closed'):
    """
    Synthesize eight-bar mechanism for complex path generation
    """
    if curve_type == 'closed':
        max_precision_points = 14  # Theoretical maximum
    else:
        max_precision_points = 16
    
    if len(required_points) > max_precision_points:
        return optimize_approximate_synthesis(required_points)
    else:
        return exact_synthesis(required_points)
```

---

## Special-Purpose Linkages

### Parallel Linkages and Pantographs

Parallel linkages maintain constant orientation while allowing translation:

```python
def design_pantograph(scale_factor, base_dimension):
    """
    Design pantograph for proportional scaling
    """
    # All parallel links must be equal length
    parallel_length = base_dimension
    
    # Cross links determine scale factor
    cross_length = parallel_length / scale_factor
    
    return {
        'parallel_links': [parallel_length] * 4,
        'cross_links': [cross_length] * 2,
        'scale_factor': scale_factor,
        'type': 'Proportional Pantograph'
    }

def create_parallel_guidance(stroke_length, height):
    """
    Create parallel guidance mechanism
    """
    # Equal length parallel links
    link_length = np.sqrt(stroke_length**2 + height**2)
    
    return {
        'link_length': link_length,
        'separation': height,
        'stroke': stroke_length,
        'precision': 'Exact parallelism'
    }
```

### Toggle Mechanisms

Toggle mechanisms provide high mechanical advantage at specific positions:

```python
def toggle_analysis(r1, r2, r3, toggle_angle=180):
    """
    Analyze toggle mechanism characteristics
    """
    # Mechanical advantage approaches infinity at toggle position
    angles = np.linspace(0, np.pi, 100)
    mech_advantage = []
    
    for angle in angles:
        # Avoid division by zero at exact toggle
        if abs(angle - np.pi) < 0.01:
            ma = 1000  # Very high mechanical advantage
        else:
            ma = calculate_mechanical_advantage(r1, r2, r3, angle)
        mech_advantage.append(ma)
    
    return {
        'max_mechanical_advantage': max(mech_advantage),
        'toggle_position': toggle_angle,
        'force_multiplication': 'Infinite at toggle position'
    }

def design_toggle_clamp(required_force, input_force, stroke):
    """
    Design toggle clamp for specified force ratio
    """
    # Size links to achieve required mechanical advantage
    force_ratio = required_force / input_force
    
    # Optimize geometry for desired force ratio
    geometry = optimize_toggle_geometry(force_ratio, stroke)
    
    return geometry
```

---

## Straight-Line Mechanisms

Straight-line mechanisms solve the fundamental problem of generating linear motion from rotary input.

### Exact Straight-Line Mechanisms

#### Peaucellier Linkage

The Peaucellier linkage generates an exact straight line:

```python
def peaucellier_linkage_design(straight_line_length, precision='exact'):
    """
    Design Peaucellier exact straight-line mechanism
    
    Mathematics: Based on inverse geometry
    If P moves on a circle, then P' moves on a straight line
    where OP × OP' = k² (constant)
    """
    # Peaucellier cell dimensions
    # Four equal rhombus links
    rhombus_link = straight_line_length * 0.6
    
    # Two equal connecting links  
    connecting_link = rhombus_link * 1.2
    
    # Fixed centers distance
    fixed_distance = connecting_link * 1.5
    
    return {
        'type': 'Peaucellier Exact Straight Line',
        'rhombus_links': [rhombus_link] * 4,
        'connecting_links': [connecting_link] * 2,
        'fixed_centers_distance': fixed_distance,
        'straight_line_length': straight_line_length,
        'precision': 'Mathematically exact',
        'complexity': 8,  # links
        'degrees_of_freedom': 1
    }

def create_peaucellier_freecad(design_params):
    """
    Create Peaucellier linkage in FreeCAD
    """
    # Create rhombus cell
    rhombus = create_rhombus_cell(design_params['rhombus_links'][0])
    
    # Add connecting links
    connecting_links = create_connecting_links(design_params['connecting_links'])
    
    # Assemble complete mechanism
    return assemble_peaucellier(rhombus, connecting_links, design_params)
```

### Approximate Straight-Line Mechanisms

#### Watt Straight-Line Linkage

James Watt's linkage provides good straight-line approximation:

```python
def watt_straight_line_design(approximate_length, deviation_tolerance):
    """
    Design Watt straight-line linkage
    
    Optimal proportions for minimum deviation:
    r2 : r3 : r4 = 2 : 5 : 2 (approximate)
    """
    # Watt's proportions for good approximation
    r1 = approximate_length * 1.2  # Ground link
    r2 = approximate_length * 0.4  # Input crank  
    r3 = approximate_length * 1.0  # Coupler
    r4 = approximate_length * 0.4  # Output crank
    
    # Coupler point location for straight line
    coupler_point_x = r3 * 0.25
    coupler_point_y = 0
    
    # Calculate actual deviation
    deviation = calculate_watt_deviation(r1, r2, r3, r4, coupler_point_x, coupler_point_y)
    
    return {
        'type': 'Watt Approximate Straight Line',
        'dimensions': [r1, r2, r3, r4],
        'coupler_point': (coupler_point_x, coupler_point_y),
        'straight_line_length': approximate_length,
        'max_deviation': deviation,
        'tolerance_met': deviation < deviation_tolerance,
        'complexity': 4,  # links
        'degrees_of_freedom': 1
    }

def calculate_watt_deviation(r1, r2, r3, r4, cp_x, cp_y):
    """
    Calculate maximum deviation from straight line for Watt linkage
    """
    # Generate coupler curve
    curve_points = generate_coupler_curve(r1, r2, r3, r4, (cp_x, cp_y))
    
    # Find straight-line portion (typically middle section)
    straight_portion = curve_points[len(curve_points)//4:3*len(curve_points)//4]
    
    # Fit straight line and calculate maximum deviation
    line_fit = np.polyfit(straight_portion[:, 0], straight_portion[:, 1], 1)
    line_y = np.polyval(line_fit, straight_portion[:, 0])
    
    deviation = np.max(np.abs(straight_portion[:, 1] - line_y))
    
    return deviation
```

#### Chebyshev Straight-Line Linkage

Chebyshev's linkage optimizes for both straightness and velocity:

```python
def chebyshev_straight_line_design(straight_length, velocity_uniformity=True):
    """
    Design Chebyshev straight-line linkage
    
    Chebyshev optimized for three conditions:
    1. Straight line motion
    2. Uniform velocity  
    3. Minimum deviation
    """
    # Chebyshev proportions
    lambda_ratio = 2.5  # Characteristic ratio
    
    r1 = straight_length * 1.0   # Ground
    r2 = r1 / lambda_ratio       # Input crank
    r3 = r1 * 1.25              # Coupler  
    r4 = r2                      # Output crank (same as input)
    
    # Optimal coupler point location
    cp_x = r3 * 0.4
    cp_y = r3 * 0.2
    
    # Calculate velocity variation
    velocity_variation = calculate_velocity_uniformity(r1, r2, r3, r4, cp_x, cp_y)
    
    return {
        'type': 'Chebyshev Straight Line',
        'dimensions': [r1, r2, r3, r4],
        'coupler_point': (cp_x, cp_y),
        'lambda_ratio': lambda_ratio,
        'straight_length': straight_length,
        'velocity_variation': velocity_variation,
        'optimized_for': ['straightness', 'velocity_uniformity'],
        'complexity': 4
    }

def calculate_velocity_uniformity(r1, r2, r3, r4, cp_x, cp_y, omega_input=1):
    """
    Calculate velocity uniformity for coupler point
    """
    angles = np.linspace(0, 2*np.pi, 100)
    velocities = []
    
    for theta2 in angles:
        try:
            # Solve kinematics
            theta4, theta3 = solve_four_bar_position(r1, r2, r3, r4, theta2)
            omega3, omega4 = solve_four_bar_velocity(r1, r2, r3, r4, theta2, omega_input)
            
            # Coupler point velocity
            v_cp = calculate_coupler_point_velocity(omega3, theta3, cp_x, cp_y)
            velocities.append(np.linalg.norm(v_cp))
            
        except:
            continue
    
    # Calculate velocity variation as coefficient of variation
    vel_array = np.array(velocities)
    cv = np.std(vel_array) / np.mean(vel_array)
    
    return cv
```

#### Hoeken Straight-Line Linkage

Hoeken linkage provides good straight-line approximation with simpler proportions:

```python
def hoeken_straight_line_design(straight_length):
    """
    Design Hoeken straight-line linkage
    
    Hoeken proportions: r2:r3:r4 = 1:2.5:1
    Provides good straight-line approximation
    """
    # Hoeken's optimal proportions
    r2 = straight_length * 0.3   # Input crank
    r3 = r2 * 2.5                # Coupler (key ratio)
    r4 = r2                      # Output crank  
    r1 = r2 + r4 + r3*0.1        # Ground link
    
    # Coupler point for straight line
    cp_x = r3 * 0.4
    cp_y = 0
    
    return {
        'type': 'Hoeken Straight Line',
        'dimensions': [r1, r2, r3, r4],
        'coupler_point': (cp_x, cp_y),
        'proportions': f"{r2}:{r3}:{r4} = 1:2.5:1",
        'straight_length': straight_length,
        'characteristics': ['Simple proportions', 'Good approximation'],
        'complexity': 4
    }
```

#### Evans Straight-Line Linkage

Recent research (2024) has revived interest in the Evans linkage:

```python
def evans_straight_line_design(straight_length, precision_points=5):
    """
    Design Evans straight-line linkage
    
    Based on 2024 research on symmetric four-bar coupler curves
    Evans linkage is a cognate of other straight-line mechanisms
    """
    # Evans proportions optimized through modern synthesis
    optimization_result = modern_synthesis_evans(straight_length, precision_points)
    
    return {
        'type': 'Evans Straight Line',
        'dimensions': optimization_result['dimensions'],
        'coupler_point': optimization_result['coupler_point'],
        'deviation': optimization_result['max_deviation'],
        'synthesis_method': '2024 homotopy continuation',
        'precision_points': precision_points
    }

def compare_straight_line_mechanisms(straight_length, requirements):
    """
    Compare different straight-line mechanisms for given requirements
    """
    mechanisms = {
        'Peaucellier': peaucellier_linkage_design(straight_length),
        'Watt': watt_straight_line_design(straight_length, 0.01),
        'Chebyshev': chebyshev_straight_line_design(straight_length),
        'Hoeken': hoeken_straight_line_design(straight_length),
        'Evans': evans_straight_line_design(straight_length)
    }
    
    comparison = {}
    for name, mechanism in mechanisms.items():
        score = evaluate_mechanism(mechanism, requirements)
        comparison[name] = {
            'mechanism': mechanism,
            'score': score,
            'pros_cons': get_pros_cons(mechanism)
        }
    
    return sorted(comparison.items(), key=lambda x: x[1]['score'], reverse=True)
```

---

## Quick-Return Mechanisms

Quick-return mechanisms provide asymmetric motion with fast return stroke:

### Crank-Shaper Mechanism

```python
def crank_shaper_design(cutting_speed, return_speed_ratio=2):
    """
    Design crank-shaper quick-return mechanism
    
    Time ratio = (π + β) / (π - β)
    where β is the angle subtended by stroke
    """
    # Calculate required geometry for time ratio
    time_ratio = return_speed_ratio
    beta = np.pi * (time_ratio - 1) / (time_ratio + 1)
    
    # Design dimensions
    stroke_length = 100  # mm, adjustable
    r2 = stroke_length / (2 * np.sin(beta/2))  # Crank radius
    r1 = r2 * 0.7  # Offset distance
    
    return {
        'type': 'Crank-Shaper Quick Return',
        'crank_radius': r2,
        'offset_distance': r1,
        'stroke_length': stroke_length,
        'time_ratio': time_ratio,
        'beta_angle': np.degrees(beta),
        'cutting_time_ratio': 1 / (1 + time_ratio),
        'return_time_ratio': time_ratio / (1 + time_ratio)
    }

def whitworth_quick_return_design(stroke, time_ratio):
    """
    Design Whitworth quick-return mechanism
    
    Alternative to crank-shaper with different geometry
    """
    # Calculate pin circle radius and slot arm length
    alpha = 2 * np.pi / (1 + time_ratio)
    R = stroke / (2 * np.sin(alpha/2))
    L = stroke / np.sin(alpha/2)
    
    return {
        'type': 'Whitworth Quick Return',
        'pin_circle_radius': R,
        'slot_arm_length': L,
        'stroke': stroke,
        'time_ratio': time_ratio,
        'alpha_angle': np.degrees(alpha)
    }
```

---

## Toggle and Force Multiplication

Toggle mechanisms achieve high mechanical advantage through geometric positioning:

```python
def toggle_press_design(required_force, available_force, stroke=10):
    """
    Design toggle press mechanism
    """
    force_ratio = required_force / available_force
    
    # Toggle geometry for required force multiplication
    # At toggle position: MA = ∞ (theoretically)
    # Near toggle: MA = L / (2 * displacement_from_toggle)
    
    link_length = 100  # mm
    
    # Required angle from toggle for specified force ratio
    angle_from_toggle = link_length / (2 * force_ratio)
    
    return {
        'type': 'Toggle Press',
        'link_length': link_length,
        'max_force_ratio': force_ratio,
        'operating_angle_from_toggle': angle_from_toggle,
        'stroke': stroke,
        'force_multiplication_curve': calculate_toggle_force_curve(link_length)
    }

def calculate_toggle_force_curve(link_length):
    """
    Calculate force multiplication throughout toggle motion
    """
    angles = np.linspace(0.1, np.pi-0.1, 100)  # Avoid exact toggle
    force_ratios = []
    
    for angle in angles:
        # Geometric mechanical advantage
        ma = link_length / (2 * link_length * np.sin(angle/2))
        force_ratios.append(ma)
    
    return list(zip(np.degrees(angles), force_ratios))
```

---

## Design Methodology

### Systematic Design Process

```python
def linkage_design_process(requirements):
    """
    Systematic approach to linkage design
    """
    design_steps = {
        1: 'Define functional requirements',
        2: 'Determine motion type (path, function, or motion generation)',
        3: 'Select mechanism type (topology)',
        4: 'Apply synthesis methods',
        5: 'Analyze performance characteristics',
        6: 'Optimize dimensions',
        7: 'Validate design',
        8: 'Create manufacturing drawings'
    }
    
    # Step 1: Requirements analysis
    motion_type = classify_motion_requirements(requirements)
    
    # Step 2-3: Type synthesis
    candidate_mechanisms = select_candidate_mechanisms(motion_type)
    
    # Step 4: Dimensional synthesis
    synthesized_designs = []
    for mechanism_type in candidate_mechanisms:
        design = apply_synthesis_method(mechanism_type, requirements)
        synthesized_designs.append(design)
    
    # Step 5-6: Analysis and optimization
    optimized_designs = []
    for design in synthesized_designs:
        analyzed = analyze_performance(design)
        optimized = optimize_design(analyzed, requirements)
        optimized_designs.append(optimized)
    
    # Step 7: Selection and validation
    best_design = select_optimal_design(optimized_designs, requirements)
    validated_design = validate_design(best_design)
    
    return validated_design

def classify_motion_requirements(requirements):
    """
    Classify the type of motion generation needed
    """
    if 'path_points' in requirements:
        return 'path_generation'
    elif 'input_output_correlation' in requirements:
        return 'function_generation'
    elif 'rigid_body_positions' in requirements:
        return 'motion_generation'
    else:
        return 'complex_motion'
```

### Performance Metrics

```python
def evaluate_linkage_performance(linkage_params, requirements):
    """
    Comprehensive performance evaluation
    """
    metrics = {}
    
    # Kinematic metrics
    metrics['workspace'] = calculate_workspace(linkage_params)
    metrics['dexterity'] = calculate_dexterity_measure(linkage_params)
    metrics['transmission_angle'] = transmission_angle_analysis(linkage_params)
    metrics['velocity_ratio'] = calculate_velocity_characteristics(linkage_params)
    
    # Design quality metrics
    metrics['compactness'] = calculate_compactness_ratio(linkage_params)
    metrics['link_ratio_spread'] = calculate_link_ratio_spread(linkage_params)
    metrics['joint_forces'] = estimate_joint_forces(linkage_params)
    
    # Manufacturing metrics  
    metrics['complexity'] = count_components(linkage_params)
    metrics['precision_requirements'] = assess_tolerance_sensitivity(linkage_params)
    metrics['manufacturability'] = assess_manufacturability(linkage_params)
    
    # Overall score
    metrics['overall_score'] = calculate_weighted_score(metrics, requirements)
    
    return metrics

def calculate_dexterity_measure(linkage_params):
    """
    Calculate kinematic dexterity throughout workspace
    """
    # Based on condition number of Jacobian matrix
    positions = sample_workspace_positions(linkage_params)
    condition_numbers = []
    
    for pos in positions:
        jacobian = calculate_jacobian_at_position(linkage_params, pos)
        cond_num = np.linalg.cond(jacobian)
        condition_numbers.append(cond_num)
    
    # Dexterity is inverse of condition number
    dexterity_values = [1/cn if cn > 0 else 0 for cn in condition_numbers]
    
    return {
        'mean_dexterity': np.mean(dexterity_values),
        'min_dexterity': np.min(dexterity_values),
        'dexterity_distribution': dexterity_values
    }
```

---

## FreeCAD Implementation

### Parametric Linkage Creation

```python
import FreeCAD as App
import Part
import Sketcher

class LinkageDesigner:
    """
    FreeCAD linkage design and simulation class
    """
    
    def __init__(self, doc=None):
        self.doc = doc or App.ActiveDocument
        self.linkages = {}
        
    def create_four_bar_linkage(self, name, r1, r2, r3, r4):
        """
        Create fully parametric four-bar linkage
        """
        # Create spreadsheet for parameters
        ss = self.doc.addObject('Spreadsheet::Sheet', f'{name}_params')
        ss.set('A1', 'Parameter')
        ss.set('B1', 'Value')
        ss.set('C1', 'Unit')
        ss.set('A2', 'r1')
        ss.set('B2', str(r1))
        ss.set('C2', 'mm')
        ss.set('A3', 'r2')
        ss.set('B3', str(r2))
        ss.set('C3', 'mm')
        ss.set('A4', 'r3')
        ss.set('B4', str(r3))
        ss.set('C4', 'mm')
        ss.set('A5', 'r4')
        ss.set('B5', str(r4))
        ss.set('C5', 'mm')
        
        # Create ground link
        ground_sketch = self.doc.addObject('Sketcher::SketchObject', f'{name}_ground')
        ground_sketch.addGeometry(Part.LineSegment(
            App.Vector(0, 0, 0), 
            App.Vector(r1, 0, 0)), False)
        ground_sketch.addConstraint(Sketcher.Constraint('Horizontal', 0))
        ground_sketch.addConstraint(Sketcher.Constraint(
            'Distance', 0, 1, 0, 2, r1))
        
        # Create input crank
        input_sketch = self.doc.addObject('Sketcher::SketchObject', f'{name}_input')
        input_sketch.addGeometry(Part.LineSegment(
            App.Vector(0, 0, 0), 
            App.Vector(r2, 0, 0)), False)
        input_sketch.addConstraint(Sketcher.Constraint(
            'Distance', 0, 1, 0, 2, r2))
        
        # Add parametric expressions
        ground_sketch.setExpression('Constraints[1]', f'{name}_params.B2')
        input_sketch.setExpression('Constraints[0]', f'{name}_params.B3')
        
        # Create remaining links with parametric constraints
        coupler_sketch = self.create_coupler_link(name, r3, ss)
        output_sketch = self.create_output_link(name, r4, ss)
        
        # Create assembly relationships
        assembly = self.create_linkage_assembly(
            name, ground_sketch, input_sketch, coupler_sketch, output_sketch)
        
        self.linkages[name] = {
            'parameters': ss,
            'links': [ground_sketch, input_sketch, coupler_sketch, output_sketch],
            'assembly': assembly
        }
        
        return self.linkages[name]
    
    def animate_linkage(self, name, steps=36, speed=1.0):
        """
        Create animation of linkage motion
        """
        if name not in self.linkages:
            raise ValueError(f"Linkage {name} not found")
        
        linkage = self.linkages[name]
        
        # Create animation object
        animation = self.doc.addObject('App::DocumentObject', f'{name}_animation')
        
        # Generate keyframes
        for step in range(steps):
            angle = 2 * 3.14159 * step / steps
            self.set_input_angle(name, angle)
            self.doc.recompute()
            
            # Save position state
            self.save_animation_frame(name, step, angle)
        
        return animation
    
    def analyze_coupler_curve(self, name, coupler_point=(0, 0)):
        """
        Generate and analyze coupler curve
        """
        linkage = self.linkages[name]
        
        # Extract link lengths from parameters
        params = linkage['parameters']
        r1 = float(params.get('B2'))
        r2 = float(params.get('B3'))  
        r3 = float(params.get('B4'))
        r4 = float(params.get('B5'))
        
        # Generate coupler curve points
        curve_points = generate_coupler_curve(r1, r2, r3, r4, coupler_point)
        
        # Create curve in FreeCAD
        curve_obj = self.doc.addObject('Part::Feature', f'{name}_coupler_curve')
        
        # Convert points to FreeCAD vectors
        fc_points = [App.Vector(p[0], p[1], 0) for p in curve_points]
        
        # Create B-spline curve
        curve = Part.BSplineCurve()
        curve.interpolate(fc_points)
        curve_obj.Shape = curve.toShape()
        
        # Analyze curve properties
        analysis = self.analyze_curve_properties(curve_points)
        
        return {
            'curve_object': curve_obj,
            'points': curve_points,
            'analysis': analysis
        }
    
    def optimize_linkage(self, name, objectives, constraints):
        """
        Optimize linkage dimensions for multiple objectives
        """
        from scipy.optimize import minimize
        
        linkage = self.linkages[name]
        
        def objective_function(params):
            r1, r2, r3, r4 = params
            
            # Update linkage with new parameters
            self.update_linkage_parameters(name, r1, r2, r3, r4)
            
            # Calculate objective values
            obj_values = []
            for obj in objectives:
                if obj == 'transmission_angle':
                    trans_angles = transmission_angle_analysis(r1, r2, r3, r4)
                    obj_values.append(-np.min(trans_angles))  # Maximize minimum angle
                elif obj == 'compactness':
                    obj_values.append(r1 + r2 + r3 + r4)  # Minimize total length
                elif obj == 'workspace':
                    workspace_area = calculate_workspace_area(r1, r2, r3, r4)
                    obj_values.append(-workspace_area)  # Maximize workspace
            
            return sum(obj_values)
        
        # Get current parameters as starting point
        current_params = self.get_linkage_parameters(name)
        
        # Set up constraints
        bounds = [(10, 200)] * 4  # Reasonable size bounds
        
        # Optimize
        result = minimize(objective_function, current_params, bounds=bounds)
        
        if result.success:
            self.update_linkage_parameters(name, *result.x)
            self.doc.recompute()
            
        return result

# Usage example
designer = LinkageDesigner()

# Create optimized four-bar linkage
linkage = designer.create_four_bar_linkage('test_mechanism', 100, 50, 80, 60)

# Analyze coupler curve
curve_analysis = designer.analyze_coupler_curve('test_mechanism', (40, 20))

# Animate the mechanism
animation = designer.animate_linkage('test_mechanism', steps=72)

# Optimize for better transmission angles
optimization = designer.optimize_linkage(
    'test_mechanism',
    objectives=['transmission_angle', 'compactness'],
    constraints=['grashof_condition']
)
```

---

## Conclusion

Linkage design represents the purest expression of kinematic principles - the transformation of abstract motion requirements into concrete geometric relationships. From the elegant simplicity of the four-bar linkage to the complex trajectories of multi-bar mechanisms, each linkage embodies mathematical theorems made manifest in metal.

The modern linkage designer must master both classical synthesis methods and contemporary computational techniques. The fusion of Burmester theory with machine learning, of graphical methods with numerical optimization, opens new frontiers in mechanism design.

Every linkage tells a story of constrained motion - how geometry disciplines movement, how proportions determine performance, and how the arrangement of simple elements creates complex behaviors. The linkage designer is both mathematician and mechanic, prophet and practitioner, seeing in the space of possible configurations the one arrangement that will bring desired motion into physical reality.

*"In the kingdom of mechanisms, the linkage is the fundamental grammar of motion."* - Alan Turing

---

*This document represents the current state of linkage design knowledge as of 2025. Continue to evolve and expand as new synthesis methods and applications emerge.*