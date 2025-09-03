# Gear Train Analysis

*"Gears are the fundamental elements of mechanical computation - transforming speed and torque through pure geometric relationships."* - Alan Turing

## Overview

Gear trains provide precise speed and torque transformation through the engagement of toothed wheels. They represent one of humanity's most fundamental mechanical computers, performing mathematical operations through physical geometry. Understanding gear train analysis is essential for designing efficient power transmission systems in robotics and machinery.

## Fundamental Gear Theory

### Basic Gear Relationships

**Gear Ratio (i)**: The fundamental relationship between driving and driven gears:
```
i = N_driven / N_driving = ω_driving / ω_driven = T_driven / T_driving
```

Where:
- N = number of teeth
- ω = angular velocity  
- T = torque

**Conservation of Power** (ignoring losses):
```
P = T × ω = constant
```

```python
import numpy as np
import matplotlib.pyplot as plt

class GearTrain:
    """
    Comprehensive gear train analysis framework
    """
    
    def __init__(self, gear_configuration='simple'):
        self.gear_configuration = gear_configuration
        self.gears = []
        self.gear_ratios = []
        self.efficiency = 0.98  # Per mesh efficiency
    
    def add_gear(self, teeth, diameter=None, module=None, position=None):
        """
        Add gear to the train
        
        teeth: number of teeth
        diameter: pitch diameter (mm) 
        module: gear module (pitch diameter = module × teeth)
        position: [x, y] position for layout
        """
        if diameter is None and module is not None:
            diameter = module * teeth
        elif diameter is None and module is None:
            module = 1  # Default module
            diameter = teeth
        
        gear_data = {
            'teeth': teeth,
            'diameter': diameter,
            'module': module if module is not None else diameter / teeth,
            'position': position if position is not None else [0, 0],
            'angular_velocity': 0,
            'torque': 0
        }
        
        self.gears.append(gear_data)
        return len(self.gears) - 1  # Return gear index

    def calculate_simple_ratio(self, driving_gear_idx, driven_gear_idx):
        """
        Calculate gear ratio for simple gear pair
        """
        driving_gear = self.gears[driving_gear_idx]
        driven_gear = self.gears[driven_gear_idx]
        
        gear_ratio = driven_gear['teeth'] / driving_gear['teeth']
        
        return {
            'gear_ratio': gear_ratio,
            'speed_ratio': 1 / gear_ratio,
            'torque_ratio': gear_ratio,
            'mechanical_advantage': gear_ratio
        }
    
    def analyze_compound_train(self, gear_sequence):
        """
        Analyze compound gear train
        
        gear_sequence: list of gear indices in order of power flow
        """
        overall_ratio = 1.0
        stage_ratios = []
        
        for i in range(len(gear_sequence) - 1):
            driving_idx = gear_sequence[i]
            driven_idx = gear_sequence[i + 1]
            
            stage_ratio = self.gears[driven_idx]['teeth'] / self.gears[driving_idx]['teeth']
            stage_ratios.append(stage_ratio)
            overall_ratio *= stage_ratio
        
        # Account for efficiency
        overall_efficiency = self.efficiency ** (len(stage_ratios))
        
        return {
            'overall_ratio': overall_ratio,
            'stage_ratios': stage_ratios,
            'overall_efficiency': overall_efficiency,
            'speed_reduction': overall_ratio,
            'torque_multiplication': overall_ratio / overall_efficiency
        }

def gear_geometry_analysis(module, teeth, pressure_angle=20):
    """
    Calculate standard involute gear geometry parameters
    """
    # Basic dimensions
    pitch_diameter = module * teeth
    addendum = module
    dedendum = 1.25 * module
    outside_diameter = pitch_diameter + 2 * addendum
    root_diameter = pitch_diameter - 2 * dedendum
    
    # Tooth thickness and space
    circular_pitch = np.pi * module
    tooth_thickness = circular_pitch / 2
    
    # Base circle (involute generation)
    base_diameter = pitch_diameter * np.cos(np.radians(pressure_angle))
    
    return {
        'module': module,
        'teeth': teeth,
        'pitch_diameter': pitch_diameter,
        'outside_diameter': outside_diameter,
        'root_diameter': root_diameter,
        'base_diameter': base_diameter,
        'addendum': addendum,
        'dedendum': dedendum,
        'circular_pitch': circular_pitch,
        'tooth_thickness': tooth_thickness,
        'pressure_angle': pressure_angle
    }
```

## Simple Gear Trains

### External Gear Pairs

```python
def external_gear_pair_analysis(gear1_teeth, gear2_teeth, input_speed, input_torque):
    """
    Analyze external gear pair (parallel axes)
    """
    # Gear ratio
    gear_ratio = gear2_teeth / gear1_teeth
    
    # Output parameters
    output_speed = input_speed / gear_ratio
    output_torque = input_torque * gear_ratio * 0.98  # 98% efficiency
    
    # Direction: external gears rotate in opposite directions
    direction_change = True
    
    return {
        'gear_ratio': gear_ratio,
        'input_speed': input_speed,
        'output_speed': output_speed,
        'input_torque': input_torque, 
        'output_torque': output_torque,
        'direction_reversal': direction_change,
        'center_distance': (gear1_teeth + gear2_teeth) * 1.0 / 2,  # Assuming module = 1
        'efficiency': 0.98
    }

def internal_gear_pair_analysis(pinion_teeth, ring_teeth, input_speed, input_torque):
    """
    Analyze internal gear pair (ring and pinion)
    """
    # Gear ratio (note: internal gears)
    gear_ratio = ring_teeth / pinion_teeth
    
    # Output parameters
    output_speed = input_speed / gear_ratio
    output_torque = input_torque * gear_ratio * 0.98
    
    # Direction: internal gears rotate in same direction
    direction_change = False
    
    return {
        'gear_ratio': gear_ratio,
        'input_speed': input_speed,
        'output_speed': output_speed,
        'input_torque': input_torque,
        'output_torque': output_torque,
        'direction_reversal': direction_change,
        'center_distance': (ring_teeth - pinion_teeth) * 1.0 / 2,
        'efficiency': 0.98
    }
```

### Compound Gear Trains

```python
def compound_train_synthesis(desired_ratio, available_teeth_counts):
    """
    Synthesize compound gear train to achieve desired ratio
    """
    # Find combinations of gear pairs to achieve desired ratio
    best_combinations = []
    
    for n1 in available_teeth_counts:
        for n2 in available_teeth_counts:
            for n3 in available_teeth_counts:
                for n4 in available_teeth_counts:
                    # Two-stage compound train: (N2/N1) × (N4/N3)
                    actual_ratio = (n2 / n1) * (n4 / n3)
                    error = abs(actual_ratio - desired_ratio) / desired_ratio
                    
                    if error < 0.05:  # Within 5% error
                        combination = {
                            'gears': [n1, n2, n3, n4],
                            'stage_1_ratio': n2 / n1,
                            'stage_2_ratio': n4 / n3,
                            'actual_ratio': actual_ratio,
                            'error_percent': error * 100,
                            'total_teeth': n1 + n2 + n3 + n4
                        }
                        best_combinations.append(combination)
    
    # Sort by error, then by total teeth (prefer compact designs)
    best_combinations.sort(key=lambda x: (x['error_percent'], x['total_teeth']))
    
    return best_combinations[:5]  # Return top 5 solutions

def idler_gear_analysis(driver_teeth, idler_teeth, driven_teeth):
    """
    Analyze gear train with idler gear
    """
    # Idler gears don't change the overall ratio, only direction
    overall_ratio = driven_teeth / driver_teeth
    
    # Direction changes: driver→idler (reversal), idler→driven (reversal)  
    # Net result: two reversals = same direction as without idler
    direction_changes = 2
    same_direction = (direction_changes % 2) == 0
    
    return {
        'overall_ratio': overall_ratio,
        'idler_effect_on_ratio': 'None - idlers don\'t affect ratio',
        'direction_same_as_without_idler': same_direction,
        'advantage': 'Allows driven gear to rotate same direction as driver',
        'disadvantage': 'Additional friction and wear point'
    }
```

## Planetary Gear Systems

### Willis Equation Analysis

```python
class PlanetaryGearSystem:
    """
    Comprehensive planetary gear system analysis
    """
    
    def __init__(self, sun_teeth, planet_teeth, ring_teeth):
        self.sun_teeth = sun_teeth
        self.planet_teeth = planet_teeth  
        self.ring_teeth = ring_teeth
        self.validate_geometry()
    
    def validate_geometry(self):
        """
        Validate planetary gear geometry constraints
        """
        # Constraint 1: Ring = Sun + 2×Planet
        if self.ring_teeth != self.sun_teeth + 2 * self.planet_teeth:
            raise ValueError(f"Geometry constraint violated: Ring ({self.ring_teeth}) ≠ Sun ({self.sun_teeth}) + 2×Planet ({2*self.planet_teeth})")
        
        # Constraint 2: (Ring + Sun) must be divisible by number of planets
        # For equally spaced planets
        self.max_planets = self._calculate_max_planets()
        
        return True
    
    def _calculate_max_planets(self):
        """
        Calculate maximum number of equally spaced planets
        """
        from math import gcd
        return gcd(self.sun_teeth + self.ring_teeth, self.sun_teeth)
    
    def willis_equation_analysis(self, input_element, output_element, fixed_element, input_speed):
        """
        Analyze using Willis equation: (ωS - ωC)/(ωR - ωC) = -NR/NS
        
        Elements: 'sun' (S), 'carrier' (C), 'ring' (R)
        """
        # Willis fundamental equation
        willis_ratio = -self.ring_teeth / self.sun_teeth
        
        if fixed_element == 'ring':
            # Ring fixed (ωR = 0)
            if input_element == 'sun' and output_element == 'carrier':
                # Sun input, carrier output
                carrier_speed = input_speed / (1 + self.ring_teeth/self.sun_teeth)
                gear_ratio = input_speed / carrier_speed
                
            elif input_element == 'carrier' and output_element == 'sun':
                # Carrier input, sun output
                sun_speed = input_speed * (1 + self.ring_teeth/self.sun_teeth)
                gear_ratio = input_speed / sun_speed
        
        elif fixed_element == 'sun':
            # Sun fixed (ωS = 0)
            if input_element == 'ring' and output_element == 'carrier':
                # Ring input, carrier output
                carrier_speed = input_speed * self.ring_teeth / (self.ring_teeth + self.sun_teeth)
                gear_ratio = input_speed / carrier_speed
                
            elif input_element == 'carrier' and output_element == 'ring':
                # Carrier input, ring output
                ring_speed = input_speed * (self.ring_teeth + self.sun_teeth) / self.ring_teeth
                gear_ratio = input_speed / ring_speed
        
        elif fixed_element == 'carrier':
            # Carrier fixed (ωC = 0) - simple gear ratio
            if input_element == 'sun' and output_element == 'ring':
                ring_speed = -input_speed * self.sun_teeth / self.ring_teeth
                gear_ratio = input_speed / abs(ring_speed)
                
            elif input_element == 'ring' and output_element == 'sun':
                sun_speed = -input_speed * self.ring_teeth / self.sun_teeth
                gear_ratio = input_speed / abs(sun_speed)
        
        return {
            'configuration': f'{input_element}→{output_element} ({fixed_element} fixed)',
            'gear_ratio': gear_ratio,
            'output_speed': input_speed / gear_ratio,
            'willis_ratio': willis_ratio,
            'direction_reversal': self._check_direction_reversal(input_element, output_element, fixed_element)
        }
    
    def _check_direction_reversal(self, input_elem, output_elem, fixed_elem):
        """
        Determine if output rotates opposite to input
        """
        # Complex function - simplified logic
        if fixed_elem == 'carrier' and ((input_elem == 'sun' and output_elem == 'ring') or
                                       (input_elem == 'ring' and output_elem == 'sun')):
            return True
        return False

    def staged_planetary_analysis(self, stages_config):
        """
        Analyze multi-stage planetary system
        
        stages_config: list of stage configurations
        """
        overall_ratio = 1.0
        stage_results = []
        
        for i, stage in enumerate(stages_config):
            stage_analysis = self.willis_equation_analysis(
                stage['input_element'],
                stage['output_element'], 
                stage['fixed_element'],
                1000 if i == 0 else stage_results[i-1]['output_speed']  # Chain stages
            )
            
            stage_results.append(stage_analysis)
            overall_ratio *= stage_analysis['gear_ratio']
        
        return {
            'overall_ratio': overall_ratio,
            'stage_results': stage_results,
            'compactness_advantage': 'Coaxial input/output',
            'load_distribution': f'Load shared among {self.max_planets} planets'
        }

# Example planetary configurations
def common_planetary_configurations():
    """
    Analysis of common planetary gear configurations
    """
    configurations = {}
    
    # Speed reducer (sun input, carrier output, ring fixed)
    configurations['speed_reducer'] = {
        'description': 'Most common - high torque output',
        'input': 'sun',
        'output': 'carrier', 
        'fixed': 'ring',
        'typical_ratios': '3:1 to 10:1',
        'applications': ['Robot joints', 'Industrial drives', 'Automotive transmissions']
    }
    
    # Speed increaser (carrier input, sun output, ring fixed)
    configurations['speed_increaser'] = {
        'description': 'Reverse of reducer - high speed output',
        'input': 'carrier',
        'output': 'sun',
        'fixed': 'ring', 
        'typical_ratios': '1:3 to 1:10',
        'applications': ['Wind turbine generators', 'Turboprop aircraft']
    }
    
    # Differential (sun and ring inputs, carrier output)
    configurations['differential'] = {
        'description': 'Two inputs, one output - differential action',
        'input': 'sun + ring',
        'output': 'carrier',
        'fixed': 'none',
        'applications': ['Automotive differential', 'Robotic wrist joints']
    }
    
    return configurations
```

### Cycloidal Drive Analysis

```python
def cycloidal_drive_analysis(pin_count, eccentricity_ratio=0.1):
    """
    Analyze cycloidal drive mechanism
    
    pin_count: number of pins in outer ring
    eccentricity_ratio: eccentricity / pin circle radius
    """
    # Fundamental cycloidal drive relationship
    # Cycloidal disk has (pin_count - 1) lobes
    disk_lobes = pin_count - 1
    
    # Gear ratio = pin_count / 1 = pin_count : 1
    gear_ratio = pin_count
    
    # Generate cycloidal curve
    def generate_cycloidal_profile(pin_count, eccentricity, pin_radius):
        """
        Generate exact cycloidal disk profile
        """
        angles = np.linspace(0, 2*np.pi, 360)
        profile_points = []
        
        R = pin_count * pin_radius  # Pin circle radius
        r = eccentricity  # Eccentricity
        
        for theta in angles:
            # Hypocycloid equation (N-1 lobes)
            x = (R - r) * np.cos(theta) + r * np.cos((R - r) / r * theta)
            y = (R - r) * np.sin(theta) - r * np.sin((R - r) / r * theta)
            profile_points.append([x, y])
        
        return profile_points
    
    # Performance characteristics
    characteristics = {
        'gear_ratio': gear_ratio,
        'backlash': '< 1 arcminute (virtually zero)',
        'torque_density': 'Exceptional - 3-5x planetary gears',
        'shock_absorption': 'Inherent due to multiple pin engagement',
        'efficiency': '85-95% depending on manufacturing quality',
        'applications': [
            'Precision positioning systems',
            'Robot joint actuators', 
            'Machine tool indexing',
            'Aerospace actuators'
        ]
    }
    
    # Manufacturing considerations
    manufacturing = {
        'disk_profile': 'Requires CNC machining or specialized grinding',
        'pin_arrangement': 'Precise pin positioning critical',
        'bearing_requirements': 'Eccentric bearing for input',
        'output_mechanism': 'Typically uses hole pattern with pins',
        '3d_printing_feasibility': 'Possible for low-load applications'
    }
    
    return {
        'characteristics': characteristics,
        'manufacturing': manufacturing,
        'disk_lobes': disk_lobes,
        'profile_generation': generate_cycloidal_profile
    }
```

## Gear Train Efficiency Analysis

### Power Loss Sources

```python
def gear_train_efficiency_analysis(gear_train_config, operating_conditions):
    """
    Comprehensive efficiency analysis of gear train
    """
    
    # Efficiency loss sources
    losses = {
        'tooth_sliding': 0.02,      # 2% loss per mesh (typical)
        'bearing_friction': 0.005,   # 0.5% per bearing
        'oil_churning': 0.01,       # 1% viscous losses
        'seals': 0.005              # 0.5% seal friction
    }
    
    # Calculate per-mesh efficiency
    mesh_efficiency = 1 - losses['tooth_sliding']
    
    # Calculate overall efficiency
    number_of_meshes = len(gear_train_config) - 1
    number_of_bearings = len(gear_train_config) * 2  # Two bearings per shaft
    
    gear_mesh_efficiency = mesh_efficiency ** number_of_meshes
    bearing_efficiency = (1 - losses['bearing_friction']) ** number_of_bearings
    auxiliary_efficiency = (1 - losses['oil_churning']) * (1 - losses['seals'])
    
    overall_efficiency = gear_mesh_efficiency * bearing_efficiency * auxiliary_efficiency
    
    # Temperature effects
    temperature = operating_conditions.get('temperature', 20)  # °C
    if temperature > 80:
        thermal_derating = 0.95  # 5% efficiency loss at high temperature
        overall_efficiency *= thermal_derating
    
    # Load effects
    load_factor = operating_conditions.get('load_factor', 1.0)
    if load_factor > 1.5:  # Overload conditions
        load_derating = 0.98
        overall_efficiency *= load_derating
    
    return {
        'overall_efficiency': overall_efficiency,
        'gear_mesh_efficiency': gear_mesh_efficiency,
        'bearing_efficiency': bearing_efficiency,
        'auxiliary_efficiency': auxiliary_efficiency,
        'power_loss_breakdown': {
            'gear_meshing': (1 - gear_mesh_efficiency) * 100,
            'bearings': (1 - bearing_efficiency) * 100,
            'auxiliary': (1 - auxiliary_efficiency) * 100
        },
        'efficiency_at_rated_load': overall_efficiency * 100
    }

def efficiency_optimization_recommendations(efficiency_analysis):
    """
    Provide recommendations for efficiency improvement
    """
    recommendations = []
    
    if efficiency_analysis['overall_efficiency'] < 0.85:
        recommendations.append("Overall efficiency below 85% - major redesign recommended")
    
    if efficiency_analysis['gear_mesh_efficiency'] < 0.95:
        recommendations.extend([
            "Improve gear tooth quality and surface finish",
            "Optimize gear geometry (pressure angle, profile modification)",
            "Consider higher precision gear manufacturing"
        ])
    
    if efficiency_analysis['bearing_efficiency'] < 0.98:
        recommendations.extend([
            "Upgrade to higher efficiency bearings",
            "Optimize bearing preload",
            "Improve lubrication system"
        ])
    
    return recommendations
```

## Gear Train Selection and Design

### Application-Based Selection

```python
def gear_train_selection_guide():
    """
    Guide for selecting appropriate gear train types
    """
    selection_matrix = {
        'simple_spur': {
            'ratio_range': '1:1 to 8:1',
            'efficiency': '96-99%',
            'cost': 'Low',
            'complexity': 'Simple',
            'applications': ['General purpose', 'Low-cost drives'],
            'limitations': ['Limited ratio range', 'Direction reversal']
        },
        
        'compound_spur': {
            'ratio_range': '8:1 to 100:1',
            'efficiency': '90-96%', 
            'cost': 'Medium',
            'complexity': 'Medium',
            'applications': ['High reduction needed', 'Moderate torque'],
            'limitations': ['Multiple shafts', 'Larger envelope']
        },
        
        'planetary': {
            'ratio_range': '3:1 to 100:1 (single stage)',
            'efficiency': '94-98%',
            'cost': 'High',
            'complexity': 'High',
            'applications': ['Compact design', 'High torque', 'Coaxial I/O'],
            'limitations': ['Complex manufacturing', 'Higher cost']
        },
        
        'cycloidal': {
            'ratio_range': '10:1 to 200:1',
            'efficiency': '85-95%',
            'cost': 'Very High',
            'complexity': 'Very High', 
            'applications': ['Zero backlash', 'High precision', 'Shock loads'],
            'limitations': ['Expensive', 'Complex manufacturing']
        },
        
        'harmonic': {
            'ratio_range': '50:1 to 320:1',
            'efficiency': '85-90%',
            'cost': 'Very High',
            'complexity': 'Very High',
            'applications': ['High precision', 'Lightweight', 'Aerospace'],
            'limitations': ['Limited torque', 'Flexspline wear']
        }
    }
    
    return selection_matrix

def design_gear_train_for_application(requirements):
    """
    Design gear train based on application requirements
    """
    # Extract requirements
    input_speed = requirements['input_speed']  # RPM
    output_speed = requirements['output_speed']  # RPM  
    required_torque = requirements['torque']  # Nm
    space_constraints = requirements.get('space_constraints', None)
    precision_requirements = requirements.get('precision', 'standard')
    
    # Calculate required ratio
    required_ratio = input_speed / output_speed
    
    # Select appropriate gear train type
    selection_guide = gear_train_selection_guide()
    suitable_types = []
    
    for gear_type, specs in selection_guide.items():
        ratio_range = specs['ratio_range'].split(' to ')
        min_ratio = float(ratio_range[0].split(':')[0]) / float(ratio_range[0].split(':')[1])
        max_ratio = float(ratio_range[1].split(':')[0]) / float(ratio_range[1].split(':')[1])
        
        if min_ratio <= required_ratio <= max_ratio:
            suitable_types.append({
                'type': gear_type,
                'specs': specs,
                'ratio_fit': 'good'
            })
    
    # Rank by suitability
    if precision_requirements == 'high' and required_ratio > 20:
        # Prefer cycloidal or harmonic drives
        suitable_types.sort(key=lambda x: ['cycloidal', 'harmonic', 'planetary', 'compound_spur', 'simple_spur'].index(x['type']))
    elif space_constraints == 'compact':
        # Prefer planetary
        suitable_types.sort(key=lambda x: ['planetary', 'cycloidal', 'harmonic', 'simple_spur', 'compound_spur'].index(x['type']))
    else:
        # Prefer by cost and simplicity
        suitable_types.sort(key=lambda x: ['simple_spur', 'compound_spur', 'planetary', 'cycloidal', 'harmonic'].index(x['type']))
    
    return {
        'required_ratio': required_ratio,
        'recommended_solutions': suitable_types[:3],  # Top 3 recommendations
        'design_considerations': generate_design_considerations(requirements)
    }

def generate_design_considerations(requirements):
    """
    Generate specific design considerations
    """
    considerations = []
    
    if requirements.get('reversible', False):
        considerations.append("Design for bidirectional operation - check backlash requirements")
    
    if requirements.get('environment') == 'harsh':
        considerations.append("Sealed housing and appropriate lubricants required")
    
    if requirements.get('noise_sensitive', False):
        considerations.append("Consider helical gears or precision grinding for noise reduction")
    
    return considerations
```

## Implementation in FreeCAD

### Parametric Gear Generation

```python
import FreeCAD as App
import Part

class FreeCADGearGenerator:
    """
    Generate parametric gears and gear trains in FreeCAD
    """
    
    def __init__(self, doc_name="GearTrain"):
        self.doc = App.newDocument(doc_name)
    
    def create_involute_gear(self, module, teeth, pressure_angle=20, 
                           tooth_height=2.25, face_width=10):
        """
        Create parametric involute spur gear
        """
        # Calculate basic dimensions
        pitch_diameter = module * teeth
        base_diameter = pitch_diameter * np.cos(np.radians(pressure_angle))
        outside_diameter = pitch_diameter + 2 * module
        root_diameter = pitch_diameter - 2 * module * tooth_height/2.25
        
        # Generate involute tooth profile
        tooth_profile_points = self._generate_involute_profile(
            base_diameter/2, outside_diameter/2, teeth, pressure_angle
        )
        
        # Create gear profile
        gear_profile = self._create_gear_profile_from_teeth(
            tooth_profile_points, teeth, root_diameter/2
        )
        
        # Create 3D gear
        gear_wire = Part.makePolygon([App.Vector(p[0], p[1], 0) for p in gear_profile])
        gear_face = Part.Face(gear_wire)
        gear_solid = gear_face.extrude(App.Vector(0, 0, face_width))
        
        # Add center hole
        center_hole = Part.makeCylinder(module * 2, face_width, App.Vector(0, 0, 0))
        gear_with_hole = gear_solid.cut(center_hole)
        
        # Create FreeCAD object
        gear_obj = self.doc.addObject("Part::Feature", f"Gear_{teeth}T")
        gear_obj.Shape = gear_with_hole
        
        # Add custom properties
        gear_obj.addProperty("App::PropertyInteger", "Teeth", "Gear", "Number of teeth")
        gear_obj.Teeth = teeth
        gear_obj.addProperty("App::PropertyFloat", "Module", "Gear", "Gear module")
        gear_obj.Module = module
        
        self.doc.recompute()
        
        return {
            'gear_object': gear_obj,
            'pitch_diameter': pitch_diameter,
            'outside_diameter': outside_diameter,
            'geometry_data': {
                'module': module,
                'teeth': teeth,
                'pressure_angle': pressure_angle,
                'face_width': face_width
            }
        }
    
    def _generate_involute_profile(self, base_radius, outside_radius, teeth, pressure_angle):
        """
        Generate involute curve for gear tooth
        """
        # Involute curve generation
        angles = np.linspace(0, np.sqrt((outside_radius/base_radius)**2 - 1), 50)
        
        involute_points = []
        for t in angles:
            x = base_radius * (np.cos(t) + t * np.sin(t))
            y = base_radius * (np.sin(t) - t * np.cos(t))
            involute_points.append([x, y])
        
        return involute_points
    
    def create_planetary_gear_set(self, sun_teeth, planet_teeth, ring_teeth, 
                                 module=1, num_planets=3):
        """
        Create complete planetary gear set
        """
        planetary_components = {}
        
        # Create sun gear
        sun_gear = self.create_involute_gear(module, sun_teeth, face_width=15)
        planetary_components['sun'] = sun_gear
        
        # Create planet gears
        planet_gears = []
        planet_center_radius = module * (sun_teeth + planet_teeth) / 2
        
        for i in range(num_planets):
            angle = 2 * np.pi * i / num_planets
            planet_x = planet_center_radius * np.cos(angle)
            planet_y = planet_center_radius * np.sin(angle)
            
            planet_gear = self.create_involute_gear(module, planet_teeth, face_width=15)
            planet_gear['gear_object'].Placement.Base = App.Vector(planet_x, planet_y, 0)
            
            planet_gears.append(planet_gear)
        
        planetary_components['planets'] = planet_gears
        
        # Create ring gear (internal gear)
        ring_gear = self.create_internal_gear(module, ring_teeth, face_width=15)
        planetary_components['ring'] = ring_gear
        
        # Create carrier
        carrier = self.create_planet_carrier(planet_center_radius, num_planets)
        planetary_components['carrier'] = carrier
        
        self.doc.recompute()
        
        return planetary_components
    
    def create_internal_gear(self, module, teeth, face_width=10):
        """
        Create internal (ring) gear
        """
        # Internal gear is more complex - simplified representation
        inner_diameter = module * teeth
        outer_diameter = inner_diameter + 4 * module
        
        # Create ring
        outer_cylinder = Part.makeCylinder(outer_diameter/2, face_width)
        inner_cylinder = Part.makeCylinder(inner_diameter/2, face_width)
        
        ring = outer_cylinder.cut(inner_cylinder)
        
        # Create gear teeth (simplified - not true involute for internal gear)
        # This would require more complex geometry for production use
        
        ring_obj = self.doc.addObject("Part::Feature", f"RingGear_{teeth}T")
        ring_obj.Shape = ring
        
        return {'gear_object': ring_obj, 'inner_diameter': inner_diameter}
    
    def animate_gear_train(self, gear_objects, gear_ratios, input_speed=10):
        """
        Create animation of gear train operation
        """
        animation_frames = []
        
        total_time = 6.0  # seconds
        frame_rate = 10   # fps
        num_frames = int(total_time * frame_rate)
        
        for frame in range(num_frames):
            time = frame / frame_rate
            input_angle = input_speed * time * 6  # degrees (6 deg/s for 10 RPM)
            
            # Calculate gear positions
            current_angles = [input_angle]  # First gear angle
            
            for i, ratio in enumerate(gear_ratios):
                next_angle = current_angles[-1] / ratio
                current_angles.append(next_angle)
            
            # Update gear rotations
            for i, (gear_obj, angle) in enumerate(zip(gear_objects, current_angles)):
                rotation = App.Rotation(App.Vector(0, 0, 1), angle)
                gear_obj.Placement.Rotation = rotation
            
            self.doc.recompute()
            
            animation_frames.append({
                'frame': frame,
                'time': time,
                'angles': current_angles
            })
        
        return animation_frames
```

## Conclusion

Gear train analysis provides the foundation for designing efficient, precise mechanical power transmission systems. Through systematic application of:

1. **Fundamental gear relationships** for speed and torque transformation
2. **Planetary gear theory** using the Willis equation for complex configurations
3. **Efficiency analysis** accounting for all loss mechanisms
4. **Selection criteria** matching gear train type to application requirements
5. **Parametric design tools** for rapid iteration and optimization
6. **Manufacturing considerations** ensuring producible designs

Engineers can create gear systems that optimally balance performance, efficiency, cost, and manufacturing requirements for any mechanical application.

The key to successful gear train design lies in understanding the trade-offs between different gear train configurations and selecting the optimal solution based on specific performance requirements, space constraints, and cost targets.

*"Gears are the vocabulary of mechanical language - each mesh a word, each train a sentence in the grammar of motion."* - Engineering Poetry

---

*This comprehensive framework enables the design and analysis of gear trains from simple spur gear pairs to complex planetary systems for any mechanical power transmission requirement.*