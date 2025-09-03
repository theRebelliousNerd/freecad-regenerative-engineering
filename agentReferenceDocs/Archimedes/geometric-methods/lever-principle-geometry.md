# The Lever Principle in Geometry

## Archimedes' Mechanical Approach to Geometry

Archimedes discovered that geometric properties could be understood through mechanical equilibrium. This revolutionary insight allows us to solve complex geometric problems by thinking about balance and forces rather than pure geometric relationships.

## Finding Centroids Using the Lever Principle

### Basic Principle

The centroid of a shape is the point where the shape would balance if made of uniform material. Archimedes realized this could be calculated by treating each infinitesimal area element as a weight and finding the balance point.

```python
def find_centroid_via_lever_principle(shape):
    """
    Find centroid using Archimedes' lever principle
    """
    # Discretize shape into small elements
    elements = discretize_shape(shape, element_size=0.1)
    
    total_moment_x = 0
    total_moment_y = 0
    total_area = 0
    
    for element in elements:
        # Each element acts as a point mass at its center
        element_area = element.get_area()
        element_center = element.get_center()
        
        # Calculate moments about axes
        moment_x = element_area * element_center.x
        moment_y = element_area * element_center.y
        
        total_moment_x += moment_x
        total_moment_y += moment_y
        total_area += element_area
    
    # Centroid is where total moments balance
    centroid_x = total_moment_x / total_area
    centroid_y = total_moment_y / total_area
    
    return App.Vector(centroid_x, centroid_y, 0)
```

### Application to Complex Shapes

```python
def analyze_l_shaped_bracket(l_shape_profile):
    """
    Find centroid of L-shaped bracket using lever principle
    """
    # Break complex shape into simple rectangles
    vertical_arm = Rectangle(width=20, height=100, x_offset=0, y_offset=0)
    horizontal_arm = Rectangle(width=80, height=20, x_offset=20, y_offset=0)
    
    # Calculate individual centroids
    c1 = vertical_arm.get_centroid()    # (10, 50)
    c2 = horizontal_arm.get_centroid()  # (60, 10)
    
    # Calculate areas
    a1 = vertical_arm.get_area()        # 2000 mm²
    a2 = horizontal_arm.get_area()      # 1600 mm²
    
    # Apply lever principle
    total_area = a1 + a2
    centroid_x = (a1 * c1.x + a2 * c2.x) / total_area
    centroid_y = (a1 * c1.y + a2 * c2.y) / total_area
    
    return {
        'centroid': App.Vector(centroid_x, centroid_y, 0),
        'verification_method': 'lever_principle',
        'component_breakdown': [
            {'shape': 'vertical_arm', 'area': a1, 'centroid': c1},
            {'shape': 'horizontal_arm', 'area': a2, 'centroid': c2}
        ]
    }
```

## Quadrature of the Parabola

### Archimedes' Method for Area Under Curves

Archimedes calculated the area under a parabola by inscribing triangles and applying the lever principle to find their centroids.

```python
def quadrature_of_parabola(parabola_function, x_start, x_end):
    """
    Calculate area under parabola using Archimedes' method
    """
    # Define the parabola: y = ax² + bx + c
    # For standard case: y = x²
    
    base = x_end - x_start
    height = parabola_function(x_end) - parabola_function(x_start)
    
    # Inscribe triangle with same base and maximum height
    triangle_area = 0.5 * base * height
    
    # Archimedes proved: parabolic segment = 4/3 * inscribed triangle
    parabola_segment_area = (4/3) * triangle_area
    
    # Verify using integration
    import scipy.integrate as integrate
    verification_area, _ = integrate.quad(parabola_function, x_start, x_end)
    
    return {
        'archimedes_result': parabola_segment_area,
        'modern_verification': verification_area,
        'error': abs(parabola_segment_area - verification_area),
        'method': 'Archimedean_quadrature',
        'triangle_area': triangle_area
    }
```

## Mechanical Advantage in Design

### Applying Lever Principles to Mechanism Design

```python
def design_lever_system(input_force, required_output_force, max_length):
    """
    Design lever system using Archimedes' principle
    F1 * d1 = F2 * d2
    """
    # Calculate required mechanical advantage
    mechanical_advantage = required_output_force / input_force
    
    # Optimize lever arm lengths
    if mechanical_advantage > 1:
        # Need force multiplication
        d1 = max_length * mechanical_advantage / (mechanical_advantage + 1)
        d2 = max_length / (mechanical_advantage + 1)
    else:
        # Need distance multiplication  
        d2 = max_length * mechanical_advantage / (mechanical_advantage + 1)
        d1 = max_length / (mechanical_advantage + 1)
    
    # Verify equilibrium
    equilibrium_check = abs(input_force * d1 - required_output_force * d2) < 1e-6
    
    return {
        'input_arm_length': d1,
        'output_arm_length': d2,
        'mechanical_advantage': mechanical_advantage,
        'equilibrium_verified': equilibrium_check,
        'fulcrum_position': d1,  # Distance from input point
        'design_principle': 'Archimedes_lever_law'
    }
```

## Center of Mass Calculations

### For Structural Analysis

```python
def calculate_structure_center_of_mass(components):
    """
    Calculate center of mass for multi-component structure
    """
    total_mass = 0
    weighted_position_sum = App.Vector(0, 0, 0)
    
    for component in components:
        mass = component.volume * component.material.density
        com = component.get_center_of_mass()
        
        # Apply lever principle in 3D
        weighted_position = com.multiply(mass)
        weighted_position_sum = weighted_position_sum.add(weighted_position)
        total_mass += mass
    
    # Overall center of mass
    overall_com = weighted_position_sum.multiply(1.0 / total_mass)
    
    return {
        'center_of_mass': overall_com,
        'total_mass': total_mass,
        'component_breakdown': [
            {
                'name': comp.name,
                'mass': comp.volume * comp.material.density,
                'com': comp.get_center_of_mass(),
                'contribution': comp.volume * comp.material.density / total_mass
            }
            for comp in components
        ],
        'method': 'lever_principle_3D'
    }
```

## Integration with FreeCAD

### Automatic Centroid Calculation

```python
def add_centroid_to_freecad_object(freecad_object):
    """
    Add centroid calculation to FreeCAD object using lever principle
    """
    # Get object's faces
    faces = freecad_object.Shape.Faces
    
    total_area = 0
    weighted_centroid_sum = App.Vector(0, 0, 0)
    
    for face in faces:
        face_area = face.Area
        face_centroid = face.CenterOfMass
        
        weighted_centroid = face_centroid.multiply(face_area)
        weighted_centroid_sum = weighted_centroid_sum.add(weighted_centroid)
        total_area += face_area
    
    object_centroid = weighted_centroid_sum.multiply(1.0 / total_area)
    
    # Add centroid marker to FreeCAD document
    centroid_marker = freecad_object.Document.addObject('Part::Sphere', 
                                                        f'{freecad_object.Name}_Centroid')
    centroid_marker.Placement.Base = object_centroid
    centroid_marker.Radius = 1.0
    centroid_marker.ViewObject.ShapeColor = (1.0, 0.0, 0.0)  # Red
    
    return {
        'centroid_position': object_centroid,
        'total_area': total_area,
        'marker_object': centroid_marker,
        'calculation_method': 'lever_principle_surface_integration'
    }
```

## Verification Through Mechanical Balance

### Physical Validation Principle

```python
def verify_centroid_by_balance_test(calculated_centroid, physical_object):
    """
    Conceptual framework for verifying centroid calculation
    """
    # This represents the theoretical test Archimedes would perform
    
    balance_points_to_test = [
        calculated_centroid,
        calculated_centroid.add(App.Vector(0.1, 0, 0)),   # Slightly offset
        calculated_centroid.add(App.Vector(-0.1, 0, 0)),
        calculated_centroid.add(App.Vector(0, 0.1, 0)),
        calculated_centroid.add(App.Vector(0, -0.1, 0))
    ]
    
    balance_test_results = []
    
    for test_point in balance_points_to_test:
        # Calculate moment about test point
        moment = calculate_moment_about_point(physical_object, test_point)
        is_balanced = abs(moment) < 1e-6
        
        balance_test_results.append({
            'test_point': test_point,
            'moment': moment,
            'balanced': is_balanced,
            'distance_from_calculated': test_point.distanceToPoint(calculated_centroid)
        })
    
    # The true centroid should have zero moment
    return {
        'tests': balance_test_results,
        'calculated_centroid_verified': balance_test_results[0]['balanced'],
        'verification_method': 'mechanical_balance_principle'
    }
```

The lever principle transforms geometric problems into mechanical ones, providing intuitive understanding and computational verification through the fundamental physics that Archimedes first discovered.