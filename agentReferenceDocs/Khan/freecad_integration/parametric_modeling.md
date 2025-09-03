# FreeCAD Parametric Modeling for Optimization

## Overview

This guide provides comprehensive methods for creating parametric models in FreeCAD that support systematic optimization workflows. The approach emphasizes constraint-driven design, parameter relationships, and automated model regeneration capabilities.

## Parametric Modeling Foundations

### 1. Constraint-Based Design Philosophy

```python
class ParametricModel:
    def __init__(self, design_intent, constraints):
        self.design_intent = design_intent
        self.constraints = constraints
        self.parameters = {}
        self.relationships = {}
        self.feature_tree = []
    
    def establish_design_intent(self):
        """Define the fundamental design relationships that drive the model"""
        design_intent = {
            'primary_dimensions': {
                'overall_length': {'type': 'driving', 'value': 1000, 'units': 'mm'},
                'overall_width': {'type': 'driving', 'value': 500, 'units': 'mm'},
                'overall_height': {'type': 'driving', 'value': 200, 'units': 'mm'}
            },
            'proportional_relationships': {
                'aspect_ratio': 'overall_length / overall_width',
                'height_ratio': 'overall_height / overall_width'
            },
            'functional_requirements': {
                'minimum_clearance': 10,  # mm
                'maximum_stress': 200e6,  # Pa
                'maximum_deflection': 'span / 250'
            }
        }
        return design_intent
    
    def create_parameter_hierarchy(self):
        """Establish parameter dependencies and relationships"""
        parameter_hierarchy = {
            'level_1_primary': ['overall_length', 'overall_width', 'material_type'],
            'level_2_derived': ['section_depth', 'flange_width', 'web_thickness'],
            'level_3_detailed': ['fillet_radius', 'hole_diameter', 'bolt_spacing'],
            'level_4_manufacturing': ['draft_angle', 'surface_finish', 'tolerance_class']
        }
        
        # Define parameter relationships
        self.relationships = {
            'section_depth': 'overall_height * 0.8',
            'flange_width': 'overall_width * 0.6',
            'web_thickness': 'max(5, section_depth / 40)',
            'fillet_radius': 'min(web_thickness, 10)',
            'hole_diameter': 'max(6, flange_width / 10)'
        }
        
        return parameter_hierarchy
```

### 2. FreeCAD Spreadsheet Integration

```python
def setup_parametric_spreadsheet(doc, parameters):
    """Create and populate FreeCAD spreadsheet with design parameters"""
    # Create spreadsheet object
    spreadsheet = doc.addObject('Spreadsheet::Sheet', 'DesignParameters')
    
    # Define parameter categories and locations
    parameter_layout = {
        'A1': 'DESIGN PARAMETERS',
        'A3': 'Primary Dimensions',
        'A4': 'Length', 'B4': str(parameters['overall_length']), 'C4': 'mm',
        'A5': 'Width', 'B5': str(parameters['overall_width']), 'C5': 'mm',
        'A6': 'Height', 'B6': str(parameters['overall_height']), 'C6': 'mm',
        
        'A8': 'Structural Properties',
        'A9': 'Young_Modulus', 'B9': str(parameters['young_modulus']), 'C9': 'MPa',
        'A10': 'Yield_Strength', 'B10': str(parameters['yield_strength']), 'C10': 'MPa',
        'A11': 'Density', 'B11': str(parameters['density']), 'C11': 'kg/m³',
        
        'A13': 'Derived Parameters',
        'A14': 'Section_Depth', 'B14': '=B6*0.8', 'C14': 'mm',
        'A15': 'Flange_Width', 'B15': '=B5*0.6', 'C15': 'mm',
        'A16': 'Web_Thickness', 'B16': '=max(5;B14/40)', 'C16': 'mm'
    }
    
    # Populate spreadsheet
    for cell, value in parameter_layout.items():
        spreadsheet.set(cell, value)
    
    # Set cell aliases for easy reference
    spreadsheet.setAlias('B4', 'Length')
    spreadsheet.setAlias('B5', 'Width')
    spreadsheet.setAlias('B6', 'Height')
    spreadsheet.setAlias('B14', 'SectionDepth')
    spreadsheet.setAlias('B15', 'FlangeWidth')
    spreadsheet.setAlias('B16', 'WebThickness')
    
    doc.recompute()
    return spreadsheet
```

### 3. Constraint-Driven Sketching

```python
def create_parametric_sketch(doc, spreadsheet):
    """Create parametric sketch with constraints linked to spreadsheet"""
    # Create sketch
    sketch = doc.addObject('Sketcher::SketchObject', 'BaseProfile')
    
    # Create geometry
    # Rectangle for main profile
    sketch.addGeometry(Part.LineSegment(
        FreeCAD.Vector(0, 0, 0), 
        FreeCAD.Vector(100, 0, 0)  # Initial values, will be constrained
    ))
    sketch.addGeometry(Part.LineSegment(
        FreeCAD.Vector(100, 0, 0), 
        FreeCAD.Vector(100, 50, 0)
    ))
    sketch.addGeometry(Part.LineSegment(
        FreeCAD.Vector(100, 50, 0), 
        FreeCAD.Vector(0, 50, 0)
    ))
    sketch.addGeometry(Part.LineSegment(
        FreeCAD.Vector(0, 50, 0), 
        FreeCAD.Vector(0, 0, 0)
    ))
    
    # Add constraints linking to spreadsheet
    sketch.addConstraint(Sketcher.Constraint('Coincident', 0, 2, 1, 1))
    sketch.addConstraint(Sketcher.Constraint('Coincident', 1, 2, 2, 1))
    sketch.addConstraint(Sketcher.Constraint('Coincident', 2, 2, 3, 1))
    sketch.addConstraint(Sketcher.Constraint('Coincident', 3, 2, 0, 1))
    
    # Dimensional constraints linked to spreadsheet
    sketch.addConstraint(Sketcher.Constraint('Distance', 0, 'DesignParameters.Length'))
    sketch.addConstraint(Sketcher.Constraint('Distance', 1, 'DesignParameters.Height'))
    
    # Additional constraints for structural profile
    # Web thickness constraint
    sketch.addGeometry(Part.LineSegment(
        FreeCAD.Vector(10, 0, 0), 
        FreeCAD.Vector(10, 50, 0)
    ))
    sketch.addConstraint(Sketcher.Constraint('Distance', 4, 'DesignParameters.WebThickness'))
    
    doc.recompute()
    return sketch
```

## Advanced Parametric Features

### 1. Adaptive Feature Creation

```python
class AdaptiveFeatureSystem:
    def __init__(self, doc, base_geometry):
        self.doc = doc
        self.base_geometry = base_geometry
        self.feature_rules = self.define_feature_rules()
    
    def define_feature_rules(self):
        """Define rules for when features should be created or modified"""
        rules = {
            'reinforcement_ribs': {
                'condition': lambda params: params['span'] > 500,  # mm
                'creation_rule': self.create_reinforcement_ribs,
                'parameters': ['rib_spacing', 'rib_height', 'rib_thickness']
            },
            'lightening_holes': {
                'condition': lambda params: params['section_depth'] > 100,  # mm
                'creation_rule': self.create_lightening_holes,
                'parameters': ['hole_diameter', 'hole_spacing', 'edge_distance']
            },
            'gusset_plates': {
                'condition': lambda params: params['load_magnitude'] > 10000,  # N
                'creation_rule': self.create_gusset_plates,
                'parameters': ['gusset_size', 'gusset_thickness', 'fillet_radius']
            }
        }
        return rules
    
    def update_adaptive_features(self, current_parameters):
        """Update features based on current parameter values"""
        for feature_name, rule in self.feature_rules.items():
            if rule['condition'](current_parameters):
                # Feature should exist
                if not self.feature_exists(feature_name):
                    self.create_feature(feature_name, rule, current_parameters)
                else:
                    self.update_feature(feature_name, rule, current_parameters)
            else:
                # Feature should not exist
                if self.feature_exists(feature_name):
                    self.remove_feature(feature_name)
    
    def create_reinforcement_ribs(self, parameters):
        """Create reinforcement ribs based on parameters"""
        rib_spacing = parameters.get('rib_spacing', 200)  # mm
        rib_height = parameters.get('rib_height', 20)  # mm
        rib_thickness = parameters.get('rib_thickness', 5)  # mm
        
        # Calculate number of ribs
        span = parameters['span']
        num_ribs = int(span / rib_spacing) - 1
        
        ribs = []
        for i in range(num_ribs):
            position = (i + 1) * rib_spacing
            
            # Create rib sketch
            rib_sketch = self.doc.addObject('Sketcher::SketchObject', f'RibSketch_{i}')
            
            # Create rib geometry
            rib_sketch.addGeometry(Part.LineSegment(
                FreeCAD.Vector(0, 0, 0),
                FreeCAD.Vector(rib_height, 0, 0)
            ))
            rib_sketch.addGeometry(Part.LineSegment(
                FreeCAD.Vector(rib_height, 0, 0),
                FreeCAD.Vector(rib_height, rib_thickness, 0)
            ))
            rib_sketch.addGeometry(Part.LineSegment(
                FreeCAD.Vector(rib_height, rib_thickness, 0),
                FreeCAD.Vector(0, rib_thickness, 0)
            ))
            rib_sketch.addGeometry(Part.LineSegment(
                FreeCAD.Vector(0, rib_thickness, 0),
                FreeCAD.Vector(0, 0, 0)
            ))
            
            # Position rib
            rib_sketch.Placement = FreeCAD.Placement(
                FreeCAD.Vector(position, 0, 0),
                FreeCAD.Rotation(0, 0, 0)
            )
            
            # Create pad feature
            rib_pad = self.doc.addObject('PartDesign::Pad', f'Rib_{i}')
            rib_pad.Profile = rib_sketch
            rib_pad.Length = parameters['width']
            
            ribs.append(rib_pad)
        
        self.doc.recompute()
        return ribs
```

### 2. Multi-Configuration Management

```python
class ConfigurationManager:
    def __init__(self, doc):
        self.doc = doc
        self.configurations = {}
        self.current_config = None
    
    def create_configuration(self, config_name, parameters):
        """Create a new configuration with specific parameter set"""
        configuration = {
            'name': config_name,
            'parameters': parameters.copy(),
            'features': self.capture_current_features(),
            'created_date': datetime.now(),
            'performance_metrics': {}
        }
        
        self.configurations[config_name] = configuration
        return configuration
    
    def apply_configuration(self, config_name):
        """Apply a specific configuration to the model"""
        if config_name not in self.configurations:
            raise ValueError(f"Configuration '{config_name}' not found")
        
        config = self.configurations[config_name]
        
        # Update spreadsheet parameters
        spreadsheet = self.doc.getObject('DesignParameters')
        for param_name, value in config['parameters'].items():
            self.update_spreadsheet_parameter(spreadsheet, param_name, value)
        
        # Update feature states
        self.apply_feature_states(config['features'])
        
        # Recompute model
        self.doc.recompute()
        
        self.current_config = config_name
    
    def compare_configurations(self, config_names):
        """Compare multiple configurations across key metrics"""
        comparison_data = {
            'configurations': config_names,
            'parameters': {},
            'performance_metrics': {},
            'feature_differences': {}
        }
        
        # Extract parameter differences
        all_params = set()
        for config_name in config_names:
            all_params.update(self.configurations[config_name]['parameters'].keys())
        
        for param in all_params:
            comparison_data['parameters'][param] = {}
            for config_name in config_names:
                config = self.configurations[config_name]
                comparison_data['parameters'][param][config_name] = \
                    config['parameters'].get(param, 'N/A')
        
        return comparison_data
    
    def optimize_across_configurations(self, objective_function):
        """Find optimal configuration based on objective function"""
        best_config = None
        best_score = float('-inf')
        
        for config_name, config in self.configurations.items():
            # Apply configuration
            self.apply_configuration(config_name)
            
            # Calculate objective
            score = objective_function(self.doc, config['parameters'])
            
            if score > best_score:
                best_score = score
                best_config = config_name
        
        # Apply best configuration
        if best_config:
            self.apply_configuration(best_config)
        
        return {
            'optimal_configuration': best_config,
            'optimal_score': best_score,
            'all_scores': {name: objective_function(self.doc, config['parameters']) 
                          for name, config in self.configurations.items()}
        }
```

### 3. Automated Model Generation

```python
class ParametricModelGenerator:
    def __init__(self):
        self.model_templates = self.load_model_templates()
        self.generation_rules = self.define_generation_rules()
    
    def generate_structural_model(self, design_requirements):
        """Generate complete structural model from requirements"""
        # Analyze requirements to select appropriate template
        template = self.select_model_template(design_requirements)
        
        # Create new document
        doc = FreeCAD.newDocument()
        
        # Setup parametric spreadsheet
        spreadsheet = self.setup_spreadsheet(doc, design_requirements)
        
        # Generate base geometry
        base_geometry = self.generate_base_geometry(doc, spreadsheet, template)
        
        # Apply structural features
        structural_features = self.apply_structural_features(
            doc, base_geometry, design_requirements
        )
        
        # Add connection details
        connections = self.add_connection_details(
            doc, structural_features, design_requirements
        )
        
        # Create assembly structure
        assembly = self.create_assembly_structure(
            doc, structural_features, connections
        )
        
        # Validate model
        validation_results = self.validate_model(doc, design_requirements)
        
        return {
            'document': doc,
            'spreadsheet': spreadsheet,
            'geometry': base_geometry,
            'features': structural_features,
            'connections': connections,
            'assembly': assembly,
            'validation': validation_results
        }
    
    def generate_beam_model(self, doc, spreadsheet, beam_parameters):
        """Generate parametric beam model"""
        # Create beam profile sketch
        beam_sketch = doc.addObject('Sketcher::SketchObject', 'BeamProfile')
        
        # Determine beam type and create appropriate profile
        beam_type = beam_parameters.get('type', 'rectangular')
        
        if beam_type == 'I_beam':
            profile = self.create_i_beam_profile(beam_sketch, spreadsheet)
        elif beam_type == 'rectangular':
            profile = self.create_rectangular_profile(beam_sketch, spreadsheet)
        elif beam_type == 'circular':
            profile = self.create_circular_profile(beam_sketch, spreadsheet)
        
        # Create sweep path
        sweep_path = self.create_sweep_path(doc, spreadsheet)
        
        # Create sweep feature
        beam_sweep = doc.addObject('Part::Sweep', 'BeamSweep')
        beam_sweep.Sections = [beam_sketch]
        beam_sweep.Spine = sweep_path
        beam_sweep.Solid = True
        beam_sweep.Frenet = True
        
        # Add structural features
        if beam_parameters.get('add_stiffeners', False):
            stiffeners = self.add_stiffeners(doc, beam_sweep, spreadsheet)
        
        if beam_parameters.get('add_connection_plates', False):
            connection_plates = self.add_connection_plates(doc, beam_sweep, spreadsheet)
        
        doc.recompute()
        return beam_sweep
    
    def create_i_beam_profile(self, sketch, spreadsheet):
        """Create parametric I-beam profile"""
        # Overall dimensions
        height = f'{spreadsheet.Name}.Height'
        flange_width = f'{spreadsheet.Name}.FlangeWidth'
        web_thickness = f'{spreadsheet.Name}.WebThickness'
        flange_thickness = f'{spreadsheet.Name}.FlangeThickness'
        
        # Create I-beam outline
        points = [
            (f'-{flange_width}/2', f'-{height}/2'),
            (f'{flange_width}/2', f'-{height}/2'),
            (f'{flange_width}/2', f'-{height}/2+{flange_thickness}'),
            (f'{web_thickness}/2', f'-{height}/2+{flange_thickness}'),
            (f'{web_thickness}/2', f'{height}/2-{flange_thickness}'),
            (f'{flange_width}/2', f'{height}/2-{flange_thickness}'),
            (f'{flange_width}/2', f'{height}/2'),
            (f'-{flange_width}/2', f'{height}/2'),
            (f'-{flange_width}/2', f'{height}/2-{flange_thickness}'),
            (f'-{web_thickness}/2', f'{height}/2-{flange_thickness}'),
            (f'-{web_thickness}/2', f'-{height}/2+{flange_thickness}'),
            (f'-{flange_width}/2', f'-{height}/2+{flange_thickness}')
        ]
        
        # Create geometry
        for i in range(len(points)):
            next_i = (i + 1) % len(points)
            line = Part.LineSegment(
                self.create_expression_vector(points[i][0], points[i][1], 0),
                self.create_expression_vector(points[next_i][0], points[next_i][1], 0)
            )
            sketch.addGeometry(line)
        
        # Add constraints for closed profile
        for i in range(len(points)):
            next_i = (i + 1) % len(points)
            sketch.addConstraint(Sketcher.Constraint('Coincident', i, 2, next_i, 1))
        
        return sketch
```

### 4. Performance-Driven Parametrics

```python
class PerformanceDrivenParametrics:
    def __init__(self, doc):
        self.doc = doc
        self.performance_objectives = {}
        self.constraint_functions = {}
        self.update_callbacks = []
    
    def add_performance_objective(self, name, calculation_function, target_value=None):
        """Add performance objective to be monitored"""
        self.performance_objectives[name] = {
            'function': calculation_function,
            'target': target_value,
            'current_value': None,
            'history': []
        }
    
    def add_constraint_function(self, name, constraint_function, limit_value):
        """Add constraint that must be satisfied"""
        self.constraint_functions[name] = {
            'function': constraint_function,
            'limit': limit_value,
            'satisfied': None
        }
    
    def evaluate_current_performance(self):
        """Evaluate all performance objectives and constraints"""
        results = {
            'objectives': {},
            'constraints': {},
            'overall_feasible': True
        }
        
        # Evaluate objectives
        for obj_name, objective in self.performance_objectives.items():
            current_value = objective['function'](self.doc)
            objective['current_value'] = current_value
            objective['history'].append(current_value)
            
            results['objectives'][obj_name] = {
                'value': current_value,
                'target': objective['target'],
                'deviation': abs(current_value - objective['target']) if objective['target'] else None
            }
        
        # Evaluate constraints
        for const_name, constraint in self.constraint_functions.items():
            constraint_value = constraint['function'](self.doc)
            satisfied = constraint_value <= constraint['limit']
            constraint['satisfied'] = satisfied
            
            results['constraints'][const_name] = {
                'value': constraint_value,
                'limit': constraint['limit'],
                'satisfied': satisfied,
                'violation': max(0, constraint_value - constraint['limit'])
            }
            
            if not satisfied:
                results['overall_feasible'] = False
        
        return results
    
    def suggest_parameter_improvements(self, sensitivity_analysis=True):
        """Suggest parameter changes to improve performance"""
        current_performance = self.evaluate_current_performance()
        suggestions = []
        
        if sensitivity_analysis:
            sensitivities = self.calculate_parameter_sensitivities()
            
            # Find most influential parameters
            for obj_name, objective in self.performance_objectives.items():
                if objective['target'] is not None:
                    deviation = abs(objective['current_value'] - objective['target'])
                    if deviation > 0.05 * objective['target']:  # 5% threshold
                        # Find parameters most sensitive to this objective
                        obj_sensitivities = sensitivities.get(obj_name, {})
                        most_sensitive_param = max(obj_sensitivities.items(), 
                                                 key=lambda x: abs(x[1]), 
                                                 default=(None, 0))
                        
                        if most_sensitive_param[0]:
                            # Calculate suggested change
                            sensitivity = most_sensitive_param[1]
                            required_change = (objective['target'] - objective['current_value']) / sensitivity
                            
                            suggestions.append({
                                'parameter': most_sensitive_param[0],
                                'current_objective': obj_name,
                                'suggested_change': required_change,
                                'expected_improvement': abs(required_change * sensitivity),
                                'confidence': 'medium'
                            })
        
        return {
            'current_performance': current_performance,
            'suggestions': suggestions,
            'feasible': current_performance['overall_feasible']
        }
    
    def calculate_parameter_sensitivities(self, perturbation_ratio=0.01):
        """Calculate sensitivity of objectives to parameter changes"""
        spreadsheet = self.doc.getObject('DesignParameters')
        if not spreadsheet:
            return {}
        
        sensitivities = {}
        
        # Get current parameter values
        current_params = self.extract_spreadsheet_parameters(spreadsheet)
        baseline_performance = self.evaluate_current_performance()
        
        # Perturb each parameter and measure response
        for param_name, current_value in current_params.items():
            if isinstance(current_value, (int, float)):
                perturbation = current_value * perturbation_ratio
                
                # Positive perturbation
                self.set_spreadsheet_parameter(spreadsheet, param_name, 
                                             current_value + perturbation)
                self.doc.recompute()
                perturbed_performance = self.evaluate_current_performance()
                
                # Calculate sensitivities for each objective
                param_sensitivities = {}
                for obj_name, obj_data in baseline_performance['objectives'].items():
                    baseline_value = obj_data['value']
                    perturbed_value = perturbed_performance['objectives'][obj_name]['value']
                    sensitivity = (perturbed_value - baseline_value) / perturbation
                    param_sensitivities[obj_name] = sensitivity
                
                sensitivities[param_name] = param_sensitivities
                
                # Restore original value
                self.set_spreadsheet_parameter(spreadsheet, param_name, current_value)
        
        self.doc.recompute()
        return sensitivities
```

## Integration with Optimization Algorithms

### 1. Parameter Space Definition

```python
def define_optimization_parameter_space(doc):
    """Define parameter space for optimization algorithms"""
    spreadsheet = doc.getObject('DesignParameters')
    
    parameter_space = {
        'design_variables': {
            'Length': {'min': 500, 'max': 2000, 'type': 'continuous', 'units': 'mm'},
            'Width': {'min': 100, 'max': 800, 'type': 'continuous', 'units': 'mm'},
            'Height': {'min': 50, 'max': 400, 'type': 'continuous', 'units': 'mm'},
            'WebThickness': {'min': 5, 'max': 20, 'type': 'continuous', 'units': 'mm'},
            'FlangeThickness': {'min': 8, 'max': 30, 'type': 'continuous', 'units': 'mm'},
            'MaterialGrade': {'options': ['S235', 'S355', 'S420'], 'type': 'discrete'}
        },
        'objectives': {
            'minimize_weight': calculate_structural_weight,
            'minimize_deflection': calculate_maximum_deflection,
            'minimize_stress': calculate_maximum_stress,
            'minimize_cost': calculate_material_cost
        },
        'constraints': {
            'stress_limit': lambda doc: calculate_maximum_stress(doc) <= 200e6,
            'deflection_limit': lambda doc: calculate_maximum_deflection(doc) <= get_span(doc) / 250,
            'geometric_constraints': validate_geometric_feasibility
        }
    }
    
    return parameter_space
```

### 2. Automated Model Evaluation

```python
def evaluate_parametric_model(doc, parameter_values):
    """Evaluate parametric model with given parameter values"""
    # Update parameters
    update_model_parameters(doc, parameter_values)
    
    # Recompute model
    doc.recompute()
    
    # Extract geometric properties
    geometry_props = extract_geometric_properties(doc)
    
    # Perform structural analysis
    analysis_results = perform_structural_analysis(doc, geometry_props)
    
    # Calculate objectives
    objectives = {
        'weight': calculate_structural_weight(doc, geometry_props),
        'deflection': analysis_results['max_deflection'],
        'stress': analysis_results['max_stress'],
        'cost': calculate_material_cost(doc, geometry_props)
    }
    
    # Check constraints
    constraints = evaluate_constraints(doc, analysis_results)
    
    return {
        'objectives': objectives,
        'constraints': constraints,
        'feasible': all(constraints.values()),
        'geometry_properties': geometry_props,
        'analysis_results': analysis_results
    }
```

This comprehensive parametric modeling framework enables systematic optimization workflows in FreeCAD while maintaining design intent and ensuring model robustness throughout the optimization process.