# Four-Bar Linkage Design

*"The four-bar linkage is the fundamental building block of mechanism design - a geometric theorem about motion proven by steel and precision."* - Alan Turing

## Overview

The four-bar linkage is the simplest and most fundamental closed kinematic chain. Despite its apparent simplicity, it exhibits rich kinematic behavior and forms the basis for understanding all complex mechanisms. Every mechanism designer must master the four-bar linkage as it embodies the essential principles of constrained motion.

## Basic Configuration and Nomenclature

### Standard Four-Bar Chain

```
Ground (r₁) ←→ Input Crank (r₂) ←→ Coupler (r₃) ←→ Output Crank (r₄) ←→ Ground
```

**Link Designations**:
- **r₁**: Ground link (fixed frame)
- **r₂**: Input crank (driving link)
- **r₃**: Coupler link (floating link)  
- **r₄**: Output crank (driven link)

**Joint Designations**:
- **A**: Ground-input joint (fixed pivot)
- **B**: Input-coupler joint (moving)
- **C**: Coupler-output joint (moving)
- **D**: Output-ground joint (fixed pivot)

```python
import numpy as np
import matplotlib.pyplot as plt

class FourBarLinkage:
    """
    Complete four-bar linkage analysis and design class
    """
    
    def __init__(self, r1, r2, r3, r4):
        self.r1 = r1  # ground link
        self.r2 = r2  # input crank
        self.r3 = r3  # coupler
        self.r4 = r4  # output crank
        self.links = [r1, r2, r3, r4]
    
    def grashof_analysis(self):
        """
        Complete Grashof analysis for motion type determination
        """
        links = self.links
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
                'continuous_rotation': True,
                'motion_description': self._get_motion_description(classifications[shortest_link])
            }
        
        elif grashof_sum == 0:
            return {
                'type': 'Special Case',
                'classification': 'Change Point Mechanism',
                'grashof_sum': grashof_sum,
                'continuous_rotation': False,
                'motion_description': 'Mechanism reaches limiting positions'
            }
        
        else:
            return {
                'type': 'Non-Grashof',
                'classification': 'Triple Rocker',
                'grashof_sum': grashof_sum,
                'continuous_rotation': False,
                'motion_description': 'All links oscillate - no continuous rotation'
            }
    
    def _get_motion_description(self, classification):
        """Get detailed motion description for each type"""
        descriptions = {
            'Crank-Rocker': 'Input crank rotates continuously, output rocker oscillates',
            'Double Crank': 'Both cranks can rotate continuously',
            'Double Rocker': 'Both cranks oscillate - neither rotates continuously'
        }
        return descriptions.get(classification, 'Unknown motion type')
```

## Grashof Classification System

### Mathematical Criterion

**Grashof's Law**: A four-bar linkage has at least one link capable of continuous rotation if:
```
s + l ≤ p + q
```

Where s = shortest link, l = longest link, p,q = intermediate links.

### Motion Types by Shortest Link Position

```python
def detailed_grashof_analysis(r1, r2, r3, r4):
    """
    Comprehensive Grashof analysis with motion characteristics
    """
    links = [r1, r2, r3, r4]
    s = min(links)
    l = max(links)
    
    # Calculate intermediate lengths
    remaining = [x for x in links if x != s and x != l]
    p, q = min(remaining), max(remaining)
    
    grashof_condition = s + l - p - q
    
    results = {
        'link_lengths': {'r1': r1, 'r2': r2, 'r3': r3, 'r4': r4},
        'extrema': {'shortest': s, 'longest': l, 'intermediate': [p, q]},
        'grashof_condition': grashof_condition
    }
    
    if grashof_condition < 0:
        # Identify which link is shortest
        shortest_position = links.index(s)
        
        if shortest_position == 0:  # Ground is shortest
            results.update({
                'type': 'Class I',
                'name': 'Double Rocker',
                'input_motion': 'Oscillatory',
                'output_motion': 'Oscillatory',
                'description': 'Both cranks oscillate - used for oscillating output'
            })
        
        elif shortest_position == 1:  # Input crank is shortest
            results.update({
                'type': 'Class II', 
                'name': 'Crank-Rocker',
                'input_motion': 'Continuous rotation',
                'output_motion': 'Oscillatory',
                'description': 'Most common type - converts rotation to oscillation'
            })
        
        elif shortest_position == 2:  # Coupler is shortest
            results.update({
                'type': 'Class III',
                'name': 'Double Crank', 
                'input_motion': 'Continuous rotation',
                'output_motion': 'Continuous rotation',
                'description': 'Both cranks rotate - complex coupler motion'
            })
        
        elif shortest_position == 3:  # Output crank is shortest
            results.update({
                'type': 'Class IV',
                'name': 'Rocker-Crank',
                'input_motion': 'Oscillatory',
                'output_motion': 'Continuous rotation', 
                'description': 'Converts oscillation to continuous rotation'
            })
    
    elif grashof_condition == 0:
        results.update({
            'type': 'Limiting Case',
            'name': 'Change Point Mechanism',
            'description': 'Mechanism reaches limiting configuration'
        })
    
    else:
        results.update({
            'type': 'Non-Grashof',
            'name': 'Triple Rocker',
            'input_motion': 'Oscillatory',
            'output_motion': 'Oscillatory',
            'description': 'All links oscillate within limited ranges'
        })
    
    return results

# Example usage
linkage_analysis = detailed_grashof_analysis(100, 50, 80, 120)
print(f"Type: {linkage_analysis['name']}")
print(f"Description: {linkage_analysis['description']}")
```

## Position Analysis

### Analytical Solution Methods

#### Freudenstein Equation Method

```python
def solve_four_bar_position_freudenstein(r1, r2, r3, r4, theta2):
    """
    Solve four-bar position using Freudenstein equation
    """
    # Freudenstein constants
    K1 = r1 / r2
    K2 = r1 / r4
    K3 = (r2**2 - r3**2 + r4**2 + r1**2) / (2 * r2 * r4)
    
    # Coefficients for quadratic in tan(θ4/2)
    A = np.cos(theta2) - K1 - K2*np.cos(theta2) + K3
    B = -2 * np.sin(theta2)
    C = K1 - (K2 + 1)*np.cos(theta2) + K3
    
    # Solve quadratic equation
    discriminant = B**2 - 4*A*C
    
    if discriminant < 0:
        return None  # No real solution - mechanism cannot be assembled
    
    # Two solutions for tan(θ4/2)
    tan_half_theta4_1 = (-B + np.sqrt(discriminant)) / (2*A)
    tan_half_theta4_2 = (-B - np.sqrt(discriminant)) / (2*A)
    
    # Convert to full angles
    theta4_1 = 2 * np.arctan(tan_half_theta4_1)
    theta4_2 = 2 * np.arctan(tan_half_theta4_2)
    
    # Solve for corresponding theta3 values
    theta3_1 = solve_theta3(r1, r2, r3, r4, theta2, theta4_1)
    theta3_2 = solve_theta3(r1, r2, r3, r4, theta2, theta4_2)
    
    return {
        'solution_1': {'theta3': theta3_1, 'theta4': theta4_1, 'branch': 'open'},
        'solution_2': {'theta3': theta3_2, 'theta4': theta4_2, 'branch': 'crossed'}
    }

def solve_theta3(r1, r2, r3, r4, theta2, theta4):
    """
    Calculate theta3 given theta2 and theta4
    """
    # From loop closure equations
    A3 = -2 * r2 * r3 * np.cos(theta2)
    B3 = -2 * r2 * r3 * np.sin(theta2)  
    C3 = r2**2 + r3**2 - r4**2 - r1**2 + 2*r1*r4*np.cos(theta4)
    
    # Solve for theta3
    discriminant = A3**2 + B3**2 - C3**2
    
    if discriminant >= 0:
        theta3_candidate1 = 2 * np.arctan((-B3 + np.sqrt(discriminant)) / (C3 + A3))
        theta3_candidate2 = 2 * np.arctan((-B3 - np.sqrt(discriminant)) / (C3 + A3))
        
        # Choose the solution that satisfies the constraint equations
        error1 = verify_position_solution(r1, r2, r3, r4, theta2, theta3_candidate1, theta4)
        error2 = verify_position_solution(r1, r2, r3, r4, theta2, theta3_candidate2, theta4)
        
        return theta3_candidate1 if error1 < error2 else theta3_candidate2
    
    return None

def verify_position_solution(r1, r2, r3, r4, theta2, theta3, theta4):
    """
    Verify position solution by checking loop closure
    """
    # Check loop closure: r2*e^(iθ2) + r3*e^(iθ3) + r4*e^(iθ4) - r1 = 0
    sum_x = r2*np.cos(theta2) + r3*np.cos(theta3) + r4*np.cos(theta4) - r1
    sum_y = r2*np.sin(theta2) + r3*np.sin(theta3) + r4*np.sin(theta4)
    
    return np.sqrt(sum_x**2 + sum_y**2)  # Should be close to zero
```

#### Complex Number Method

```python
def solve_four_bar_complex(r1, r2, r3, r4, theta2):
    """
    Solve four-bar position using complex number representation
    """
    # Represent links as complex vectors
    z1 = r1 + 0j  # Ground link along real axis
    z2 = r2 * np.exp(1j * theta2)  # Input crank
    
    # Loop closure: z2 + z3 + z4 - z1 = 0
    # Rearrange: z3 + z4 = z1 - z2
    
    target = z1 - z2
    
    # z3 and z4 must satisfy: |z3 + z4| = |target| and |z3| = r3, |z4| = r4
    # This gives us a system of equations to solve
    
    target_magnitude = abs(target)
    target_angle = np.angle(target)
    
    # Use law of cosines to find the angle between z3 and z4
    try:
        cos_angle_34 = (r3**2 + r4**2 - target_magnitude**2) / (2 * r3 * r4)
        
        if abs(cos_angle_34) <= 1:
            angle_34 = np.arccos(cos_angle_34)
            
            # Two possible configurations
            angle_3_rel = np.arccos((target_magnitude**2 + r3**2 - r4**2) / (2 * target_magnitude * r3))
            
            theta3_1 = target_angle + angle_3_rel
            theta3_2 = target_angle - angle_3_rel
            
            theta4_1 = theta3_1 - angle_34
            theta4_2 = theta3_2 + angle_34
            
            return {
                'solution_1': {'theta3': theta3_1, 'theta4': theta4_1},
                'solution_2': {'theta3': theta3_2, 'theta4': theta4_2}
            }
    except:
        return None  # No valid solution
```

## Coupler Curves and Path Generation

### Coupler Curve Generation

```python
def generate_coupler_curve(r1, r2, r3, r4, coupler_point, num_points=360):
    """
    Generate coupler curve for specified point on coupler link
    
    coupler_point: [x_offset, y_offset] from coupler joint B
    """
    theta2_range = np.linspace(0, 2*np.pi, num_points)
    coupler_positions = []
    valid_positions = []
    
    for theta2 in theta2_range:
        position_result = solve_four_bar_position_freudenstein(r1, r2, r3, r4, theta2)
        
        if position_result is not None:
            # Use first solution (open branch)
            theta3 = position_result['solution_1']['theta3']
            
            # Calculate position of joint B (input-coupler joint)
            B_x = r2 * np.cos(theta2)
            B_y = r2 * np.sin(theta2)
            
            # Transform coupler point to global coordinates
            cos_theta3 = np.cos(theta3)
            sin_theta3 = np.sin(theta3)
            
            P_x = B_x + coupler_point[0]*cos_theta3 - coupler_point[1]*sin_theta3
            P_y = B_y + coupler_point[0]*sin_theta3 + coupler_point[1]*cos_theta3
            
            coupler_positions.append([P_x, P_y])
            valid_positions.append(theta2)
    
    return {
        'path_points': np.array(coupler_positions),
        'valid_input_angles': np.array(valid_positions),
        'curve_properties': analyze_coupler_curve_properties(coupler_positions)
    }

def analyze_coupler_curve_properties(curve_points):
    """
    Analyze geometric properties of coupler curve
    """
    if len(curve_points) < 3:
        return {'error': 'Insufficient points for analysis'}
    
    points = np.array(curve_points)
    
    # Curve length using trapezoidal integration
    distances = np.linalg.norm(np.diff(points, axis=0), axis=1)
    curve_length = np.sum(distances)
    
    # Bounding rectangle
    min_x, max_x = np.min(points[:, 0]), np.max(points[:, 0])
    min_y, max_y = np.min(points[:, 1]), np.max(points[:, 1])
    
    # Enclosed area (using shoelace formula)
    if len(points) > 2:
        x = points[:, 0]
        y = points[:, 1]
        area = 0.5 * abs(sum(x[i]*y[i+1] - x[i+1]*y[i] for i in range(-1, len(x)-1)))
    else:
        area = 0
    
    # Curvature analysis (simplified)
    curvatures = []
    for i in range(1, len(points)-1):
        p1, p2, p3 = points[i-1], points[i], points[i+1]
        
        # Calculate curvature using three points
        a = np.linalg.norm(p2 - p1)
        b = np.linalg.norm(p3 - p2)
        c = np.linalg.norm(p3 - p1)
        
        if a > 0 and b > 0 and c > 0:
            area_triangle = 0.5 * abs((p2[0] - p1[0])*(p3[1] - p1[1]) - (p3[0] - p1[0])*(p2[1] - p1[1]))
            curvature = 4 * area_triangle / (a * b * c)
            curvatures.append(curvature)
    
    return {
        'curve_length': curve_length,
        'bounding_box': {'min_x': min_x, 'max_x': max_x, 'min_y': min_y, 'max_y': max_y},
        'width': max_x - min_x,
        'height': max_y - min_y,
        'enclosed_area': area,
        'max_curvature': np.max(curvatures) if curvatures else 0,
        'mean_curvature': np.mean(curvatures) if curvatures else 0
    }
```

### Path Generation Synthesis

```python
def synthesize_path_generator(desired_points, optimization_method='genetic'):
    """
    Synthesize four-bar linkage to generate specified path points
    """
    
    def objective_function(linkage_params):
        """
        Objective function for path generation optimization
        """
        r1, r2, r3, r4, cp_x, cp_y = linkage_params
        
        # Generate actual coupler curve
        result = generate_coupler_curve(r1, r2, r3, r4, [cp_x, cp_y])
        actual_points = result['path_points']
        
        # Calculate error from desired points
        total_error = 0
        for desired_point in desired_points:
            # Find closest point on generated curve
            distances = np.linalg.norm(actual_points - desired_point, axis=1)
            min_distance = np.min(distances)
            total_error += min_distance**2
        
        return total_error
    
    # Constraints for valid linkage
    def constraints(params):
        r1, r2, r3, r4 = params[:4]
        
        # Grashof constraint (for desired motion type)
        links = sorted([r1, r2, r3, r4])
        grashof_condition = links[0] + links[-1] - links[1] - links[2]
        
        # Assembly constraint
        max_reach = r2 + r3
        min_reach = abs(r2 - r3)
        ground_length = r1
        
        assembly_valid = (min_reach <= ground_length <= max_reach)
        
        return [grashof_condition, 1 if assembly_valid else -1]
    
    if optimization_method == 'genetic':
        return genetic_algorithm_synthesis(objective_function, constraints)
    elif optimization_method == 'gradient':
        return gradient_based_synthesis(objective_function, constraints)
```

## Transmission Angle Analysis

### Definition and Importance

The transmission angle (μ) is the angle between the coupler link and the output crank. It determines the force transmission efficiency.

```python
def transmission_angle_analysis(r1, r2, r3, r4, num_positions=72):
    """
    Analyze transmission angle throughout motion cycle
    """
    theta2_range = np.linspace(0, 2*np.pi, num_positions)
    transmission_angles = []
    positions_data = []
    
    for theta2 in theta2_range:
        position_result = solve_four_bar_position_freudenstein(r1, r2, r3, r4, theta2)
        
        if position_result is not None:
            theta3 = position_result['solution_1']['theta3']
            theta4 = position_result['solution_1']['theta4']
            
            # Calculate transmission angle
            # Vector from C to B (opposite to coupler)
            vec_CB = np.array([-r3*np.cos(theta3), -r3*np.sin(theta3)])
            
            # Vector from C to D (output crank direction)
            vec_CD = np.array([-r4*np.cos(theta4), -r4*np.sin(theta4)])
            
            # Angle between vectors
            dot_product = np.dot(vec_CB, vec_CD)
            magnitudes = np.linalg.norm(vec_CB) * np.linalg.norm(vec_CD)
            
            cos_transmission = dot_product / magnitudes
            transmission_angle = np.arccos(np.clip(cos_transmission, -1, 1))
            
            # Ensure angle is acute (0 to 90 degrees)
            if transmission_angle > np.pi/2:
                transmission_angle = np.pi - transmission_angle
            
            transmission_angles.append(np.degrees(transmission_angle))
            positions_data.append({
                'theta2': np.degrees(theta2),
                'theta3': np.degrees(theta3),
                'theta4': np.degrees(theta4),
                'transmission_angle': np.degrees(transmission_angle)
            })
    
    if transmission_angles:
        min_transmission = min(transmission_angles)
        max_transmission = max(transmission_angles)
        mean_transmission = np.mean(transmission_angles)
        
        # Quality assessment
        if min_transmission > 50:
            quality = 'Excellent'
        elif min_transmission > 40:
            quality = 'Good'
        elif min_transmission > 30:
            quality = 'Acceptable'
        else:
            quality = 'Poor'
        
        return {
            'transmission_angles': transmission_angles,
            'min_transmission_angle': min_transmission,
            'max_transmission_angle': max_transmission,
            'mean_transmission_angle': mean_transmission,
            'quality_rating': quality,
            'position_data': positions_data,
            'design_recommendation': get_transmission_recommendation(min_transmission)
        }
    
    return {'error': 'No valid positions found'}

def get_transmission_recommendation(min_angle):
    """
    Provide design recommendations based on transmission angle
    """
    if min_angle > 50:
        return "Excellent force transmission - no changes needed"
    elif min_angle > 40:
        return "Good design - minor optimization possible"
    elif min_angle > 30:
        return "Acceptable - consider link ratio optimization"
    else:
        return "Poor transmission - major redesign recommended"
```

## Velocity and Acceleration Analysis

### Analytical Velocity Analysis

```python
def velocity_analysis_four_bar(r1, r2, r3, r4, theta2, theta3, theta4, omega2):
    """
    Complete velocity analysis for four-bar linkage
    """
    # Velocity coefficient matrix from differentiated constraint equations
    A_matrix = np.array([
        [-r3*np.sin(theta3), -r4*np.sin(theta4)],
        [r3*np.cos(theta3), r4*np.cos(theta4)]
    ])
    
    # Known velocity terms
    B_vector = np.array([
        r2*omega2*np.sin(theta2),
        -r2*omega2*np.cos(theta2)
    ])
    
    try:
        # Solve for unknown angular velocities
        omega_vector = np.linalg.solve(A_matrix, B_vector)
        omega3, omega4 = omega_vector
        
        return {
            'omega2': omega2,
            'omega3': omega3,
            'omega4': omega4,
            'angular_velocity_ratios': {
                'omega3_omega2': omega3/omega2 if omega2 != 0 else 0,
                'omega4_omega2': omega4/omega2 if omega2 != 0 else 0
            },
            'mechanical_advantage': omega2/omega4 if omega4 != 0 else float('inf')
        }
    
    except np.linalg.LinAlgError:
        return {'error': 'Singular configuration - dead point in mechanism'}

def acceleration_analysis_four_bar(r1, r2, r3, r4, theta2, theta3, theta4, 
                                   omega2, omega3, omega4, alpha2=0):
    """
    Complete acceleration analysis for four-bar linkage
    """
    # Acceleration coefficient matrix (same as velocity)
    A_matrix = np.array([
        [-r3*np.sin(theta3), -r4*np.sin(theta4)],
        [r3*np.cos(theta3), r4*np.cos(theta4)]
    ])
    
    # Known acceleration terms (including Coriolis and centripetal)
    B_vector = np.array([
        r2*alpha2*np.sin(theta2) + r2*omega2**2*np.cos(theta2) - 
        r3*omega3**2*np.cos(theta3) - r4*omega4**2*np.cos(theta4),
        
        -r2*alpha2*np.cos(theta2) + r2*omega2**2*np.sin(theta2) - 
        r3*omega3**2*np.sin(theta3) - r4*omega4**2*np.sin(theta4)
    ])
    
    try:
        # Solve for unknown angular accelerations
        alpha_vector = np.linalg.solve(A_matrix, B_vector)
        alpha3, alpha4 = alpha_vector
        
        return {
            'alpha2': alpha2,
            'alpha3': alpha3,
            'alpha4': alpha4,
            'angular_acceleration_ratios': {
                'alpha3_alpha2': alpha3/alpha2 if alpha2 != 0 else 0,
                'alpha4_alpha2': alpha4/alpha2 if alpha2 != 0 else 0
            }
        }
    
    except np.linalg.LinAlgError:
        return {'error': 'Singular configuration during acceleration analysis'}
```

## Design Optimization

### Multi-Objective Optimization

```python
def optimize_four_bar_linkage(design_requirements, constraints=None):
    """
    Multi-objective optimization of four-bar linkage
    """
    from scipy.optimize import minimize
    
    def objective_function(params):
        r1, r2, r3, r4 = params
        
        # Initialize total cost
        total_cost = 0
        
        # Path generation error (if required)
        if 'desired_path' in design_requirements:
            path_result = generate_coupler_curve(r1, r2, r3, r4, 
                                                design_requirements['coupler_point'])
            path_error = calculate_path_error(path_result['path_points'], 
                                            design_requirements['desired_path'])
            total_cost += design_requirements.get('path_weight', 1.0) * path_error
        
        # Transmission angle penalty
        trans_result = transmission_angle_analysis(r1, r2, r3, r4)
        if 'transmission_angles' in trans_result:
            min_trans_angle = trans_result['min_transmission_angle']
            if min_trans_angle < design_requirements.get('min_transmission_angle', 40):
                penalty = (design_requirements.get('min_transmission_angle', 40) - min_trans_angle)**2
                total_cost += design_requirements.get('transmission_weight', 2.0) * penalty
        
        # Size penalty (encourage compact designs)
        size_penalty = (r1 + r2 + r3 + r4) * design_requirements.get('size_weight', 0.001)
        total_cost += size_penalty
        
        # Grashof constraint penalty
        grashof_result = FourBarLinkage(r1, r2, r3, r4).grashof_analysis()
        if design_requirements.get('motion_type') == 'crank-rocker':
            if grashof_result['classification'] != 'Crank-Rocker':
                total_cost += 1000  # Large penalty
        
        return total_cost
    
    # Optimization constraints
    opt_constraints = []
    
    if constraints:
        if 'link_ratios' in constraints:
            max_ratio = constraints['link_ratios']['max']
            opt_constraints.append({
                'type': 'ineq',
                'fun': lambda x: max_ratio - (max(x) / min(x))
            })
        
        if 'assembly' in constraints:
            opt_constraints.append({
                'type': 'ineq',
                'fun': lambda x: assembly_constraint(x)
            })
    
    # Initial guess and bounds
    initial_guess = design_requirements.get('initial_guess', [100, 50, 80, 60])
    bounds = design_requirements.get('bounds', [(10, 500)] * 4)
    
    # Perform optimization
    result = minimize(
        objective_function,
        initial_guess,
        method='SLSQP',
        bounds=bounds,
        constraints=opt_constraints
    )
    
    if result.success:
        optimized_linkage = FourBarLinkage(*result.x)
        return {
            'optimal_parameters': result.x,
            'optimization_cost': result.fun,
            'linkage_analysis': optimized_linkage.grashof_analysis(),
            'transmission_analysis': transmission_angle_analysis(*result.x)
        }
    
    return {'error': 'Optimization failed to converge'}
```

## Implementation in FreeCAD

### Parametric Four-Bar Creation

```python
import FreeCAD as App
import Part

class FreeCADFourBarLinkage:
    """
    FreeCAD implementation of parametric four-bar linkage
    """
    
    def __init__(self, doc_name="FourBarLinkage"):
        self.doc = App.newDocument(doc_name)
        self.links = {}
        self.joints = {}
    
    def create_linkage(self, r1, r2, r3, r4, link_width=10, joint_radius=5):
        """
        Create complete parametric four-bar linkage in FreeCAD
        """
        # Create ground link
        self.links['ground'] = self.create_link('Ground', r1, link_width, [0, 0, 0])
        
        # Create input crank
        self.links['input'] = self.create_link('InputCrank', r2, link_width, [0, 0, 0])
        
        # Create coupler
        self.links['coupler'] = self.create_link('Coupler', r3, link_width, [r2, 0, 0])
        
        # Create output crank
        self.links['output'] = self.create_link('OutputCrank', r4, link_width, [r1, 0, 0])
        
        # Create joints
        self.joints['A'] = self.create_joint('JointA', [0, 0, 0], joint_radius)
        self.joints['B'] = self.create_joint('JointB', [r2, 0, 0], joint_radius)
        self.joints['C'] = self.create_joint('JointC', [r2+r3, 0, 0], joint_radius)
        self.joints['D'] = self.create_joint('JointD', [r1, 0, 0], joint_radius)
        
        # Add parameters for animation
        self.add_parameters(r1, r2, r3, r4)
        
        self.doc.recompute()
        
        return {
            'document': self.doc,
            'links': self.links,
            'joints': self.joints
        }
    
    def create_link(self, name, length, width, position):
        """Create parametric link"""
        link = self.doc.addObject('Part::Box', name)
        link.Length = length
        link.Width = width
        link.Height = 5  # Standard thickness
        link.Placement.Base = App.Vector(*position)
        
        return link
    
    def create_joint(self, name, position, radius):
        """Create joint representation"""
        joint = self.doc.addObject('Part::Cylinder', name)
        joint.Radius = radius
        joint.Height = 8  # Slightly taller than links
        joint.Placement.Base = App.Vector(*position)
        
        return joint
    
    def add_parameters(self, r1, r2, r3, r4):
        """Add parametric control"""
        # Create spreadsheet for parameters
        sheet = self.doc.addObject('Spreadsheet::Sheet', 'Parameters')
        sheet.set('A1', 'Parameter')
        sheet.set('B1', 'Value')
        sheet.set('A2', 'r1')
        sheet.set('B2', str(r1))
        sheet.set('A3', 'r2')
        sheet.set('B3', str(r2))
        sheet.set('A4', 'r3') 
        sheet.set('B4', str(r3))
        sheet.set('A5', 'r4')
        sheet.set('B5', str(r4))
        
        return sheet
    
    def animate_linkage(self, num_steps=36):
        """Create animation of linkage motion"""
        angles = np.linspace(0, 2*np.pi, num_steps)
        
        for i, theta2 in enumerate(angles):
            # Solve position for this input angle
            position_result = solve_four_bar_position_freudenstein(
                float(self.doc.Parameters.r1),
                float(self.doc.Parameters.r2), 
                float(self.doc.Parameters.r3),
                float(self.doc.Parameters.r4),
                theta2
            )
            
            if position_result:
                # Update link positions
                self.update_linkage_position(position_result['solution_1'], theta2)
                
                # Export frame for animation
                self.doc.recompute()
                # Export or save frame as needed
    
    def update_linkage_position(self, solution, theta2):
        """Update linkage to specified position"""
        theta3 = solution['theta3']
        theta4 = solution['theta4']
        
        # Update input crank rotation
        self.links['input'].Placement.Rotation = App.Rotation(App.Vector(0,0,1), np.degrees(theta2))
        
        # Update coupler position and rotation
        # (Implementation would depend on FreeCAD's constraint system)
```

## Conclusion

Four-bar linkage design represents the fundamental principles of mechanism synthesis - the art of transforming motion requirements into precise geometric relationships. Through systematic analysis of:

1. **Grashof classification** for motion type determination
2. **Position analysis** using analytical and numerical methods
3. **Coupler curve generation** for path synthesis
4. **Transmission angle optimization** for efficient force transfer
5. **Velocity and acceleration analysis** for dynamic behavior
6. **Multi-objective optimization** for performance maximization

The four-bar linkage serves as both a practical mechanism and a gateway to understanding all complex kinematic systems. Its apparent simplicity conceals profound mathematical relationships that, once mastered, illuminate the entire field of mechanism design.

*"In the four-bar linkage lies the essence of kinematic design - constraint and freedom dancing together in perfect geometric harmony."* - Engineering Philosophy

---

*This comprehensive framework enables systematic design, analysis, and optimization of four-bar linkages for any application requiring precise motion transformation.*