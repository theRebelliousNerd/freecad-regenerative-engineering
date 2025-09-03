# Typology Generation Rules: Systematic Design Grammar Creation

## Overview

Structural typologies represent families of design solutions that share common organizational principles, load-carrying mechanisms, and geometric relationships. Generation rules provide systematic methods for creating, modifying, and optimizing these typologies across different scales and applications.

## Fundamental Grammar Concepts

### 1. Shape Grammar Foundations

Shape grammars provide formal language for generating designs through rule-based transformations:

```python
class ShapeGrammar:
    def __init__(self, initial_shape, production_rules):
        self.vocabulary = self.define_vocabulary()
        self.initial_shape = initial_shape
        self.rules = production_rules
        self.generation_tree = []
    
    def define_vocabulary(self):
        """Define basic geometric and structural elements"""
        return {
            'structural_elements': ['beam', 'column', 'brace', 'plate', 'shell'],
            'connection_types': ['pinned', 'fixed', 'semi_rigid', 'welded', 'bolted'],
            'geometric_primitives': ['line', 'arc', 'surface', 'volume'],
            'load_paths': ['axial', 'bending', 'shear', 'torsion', 'combined'],
            'boundary_conditions': ['support', 'load', 'constraint', 'interface']
        }
    
    def apply_rule(self, current_design, rule_index):
        """Apply specific production rule to current design state"""
        rule = self.rules[rule_index]
        
        # Check if rule is applicable
        if self.rule_applicable(current_design, rule):
            new_design = rule.transform(current_design)
            self.generation_tree.append({
                'parent': current_design,
                'rule': rule,
                'offspring': new_design
            })
            return new_design
        
        return None
    
    def generate_typology_family(self, max_iterations=50):
        """Generate family of related structural solutions"""
        current_design = self.initial_shape
        typology_family = [current_design]
        
        for iteration in range(max_iterations):
            applicable_rules = self.find_applicable_rules(current_design)
            
            if not applicable_rules:
                break
            
            # Apply most promising rule (based on optimization criteria)
            best_rule = self.select_best_rule(applicable_rules, current_design)
            new_design = self.apply_rule(current_design, best_rule)
            
            if new_design and self.satisfies_constraints(new_design):
                typology_family.append(new_design)
                current_design = new_design
        
        return typology_family
```

### 2. Parametric Generation Framework

```python
class ParametricTypologyGenerator:
    def __init__(self, base_typology, parameter_space):
        self.base_typology = base_typology
        self.parameter_space = parameter_space
        self.constraint_functions = []
        self.objective_functions = []
    
    def define_parametric_relationships(self):
        """Establish relationships between design parameters"""
        relationships = {
            'proportional': self.define_proportional_rules(),
            'conditional': self.define_conditional_rules(),
            'optimization_driven': self.define_optimization_rules(),
            'constraint_based': self.define_constraint_rules()
        }
        return relationships
    
    def define_proportional_rules(self):
        """Rules based on proportional relationships"""
        return {
            'golden_ratio_proportions': {
                'beam_depth_to_span': lambda span: span / 12.0,  # L/12 rule
                'column_spacing_to_height': lambda height: height / 8.0,  # Typical ratio
                'width_to_height_ratio': 1.618  # Golden ratio for aesthetic proportion
            },
            'structural_efficiency_ratios': {
                'moment_of_inertia_scaling': lambda depth: depth**3 / 12,
                'section_modulus_optimization': lambda depth, width: width * depth**2 / 6,
                'slenderness_limits': lambda length, radius: length / radius < 200
            }
        }
    
    def generate_parametric_variants(self, parameter_ranges, sample_count=100):
        """Generate parameter combinations using systematic sampling"""
        # Latin Hypercube Sampling for efficient space exploration
        parameter_samples = self.latin_hypercube_sampling(
            parameter_ranges, sample_count
        )
        
        typology_variants = []
        for sample in parameter_samples:
            # Create parametric instance
            variant = self.instantiate_typology(sample)
            
            # Apply parametric relationships
            variant = self.apply_parametric_relationships(variant)
            
            # Validate against constraints
            if self.validate_variant(variant):
                # Calculate performance metrics
                performance = self.evaluate_performance(variant)
                variant.performance_metrics = performance
                typology_variants.append(variant)
        
        return typology_variants
```

## Structural System Generation Rules

### 1. Tube Structure Generation

```python
class TubeStructureGenerator:
    def __init__(self, building_parameters):
        self.height = building_parameters['height']
        self.footprint = building_parameters['footprint']
        self.loads = building_parameters['loads']
        self.materials = building_parameters['materials']
    
    def generate_tube_typologies(self):
        """Generate appropriate tube structure variants"""
        typologies = []
        
        # Rule-based typology selection
        if self.height < 50:
            typologies.append(self.generate_framed_tube())
        elif self.height < 100:
            typologies.extend([
                self.generate_framed_tube(),
                self.generate_trussed_tube()
            ])
        elif self.height < 150:
            typologies.extend([
                self.generate_trussed_tube(),
                self.generate_tube_in_tube()
            ])
        else:
            typologies.extend([
                self.generate_bundled_tube(),
                self.generate_mega_frame_system()
            ])
        
        return typologies
    
    def generate_framed_tube(self):
        """Generate framed tube structural system"""
        # Parametric rules for framed tube
        column_spacing = self.optimize_column_spacing()
        spandrel_depth = self.calculate_spandrel_depth()
        
        framed_tube = StructuralSystem({
            'type': 'framed_tube',
            'parameters': {
                'column_spacing': column_spacing,
                'spandrel_depth': spandrel_depth,
                'corner_column_size': self.calculate_corner_columns(),
                'facade_column_size': self.calculate_facade_columns(),
                'material_distribution': self.optimize_material_distribution()
            },
            'generation_rules': {
                'perimeter_stiffness': self.calculate_perimeter_stiffness,
                'shear_lag_mitigation': self.mitigate_shear_lag,
                'wind_load_distribution': self.distribute_wind_loads
            }
        })
        
        return framed_tube
    
    def generate_trussed_tube(self):
        """Generate trussed tube with diagonal bracing"""
        base_tube = self.generate_framed_tube()
        
        # Add bracing rules
        bracing_patterns = self.generate_bracing_patterns()
        optimal_pattern = self.select_optimal_bracing(bracing_patterns)
        
        trussed_tube = base_tube.copy()
        trussed_tube.update({
            'type': 'trussed_tube',
            'bracing_system': {
                'pattern': optimal_pattern,
                'brace_sizing': self.optimize_brace_sizing(optimal_pattern),
                'intersection_details': self.design_intersections(optimal_pattern),
                'construction_sequence': self.plan_construction_sequence(optimal_pattern)
            }
        })
        
        return trussed_tube
    
    def generate_bracing_patterns(self):
        """Generate different diagonal bracing configurations"""
        patterns = {
            'x_bracing': {
                'geometry': self.create_x_pattern(),
                'efficiency': self.calculate_x_efficiency(),
                'constructability': self.assess_x_constructability()
            },
            'k_bracing': {
                'geometry': self.create_k_pattern(),
                'efficiency': self.calculate_k_efficiency(),
                'constructability': self.assess_k_constructability()
            },
            'chevron_bracing': {
                'geometry': self.create_chevron_pattern(),
                'efficiency': self.calculate_chevron_efficiency(),
                'constructability': self.assess_chevron_constructability()
            }
        }
        
        return patterns
```

### 2. Bridge Structure Generation

```python
class BridgeTypologyGenerator:
    def __init__(self, span, loads, site_conditions):
        self.span = span
        self.loads = loads
        self.site_conditions = site_conditions
        self.typology_rules = self.define_bridge_rules()
    
    def define_bridge_rules(self):
        """Define span-based bridge typology selection rules"""
        return {
            'short_span': {
                'range': (0, 30),  # meters
                'preferred_types': ['beam', 'slab', 'box_girder'],
                'generation_rules': self.short_span_rules()
            },
            'medium_span': {
                'range': (30, 100),  # meters
                'preferred_types': ['truss', 'arch', 'prestressed_concrete'],
                'generation_rules': self.medium_span_rules()
            },
            'long_span': {
                'range': (100, 500),  # meters
                'preferred_types': ['cable_stayed', 'suspension', 'arch'],
                'generation_rules': self.long_span_rules()
            },
            'super_long_span': {
                'range': (500, 2000),  # meters
                'preferred_types': ['suspension', 'cable_stayed'],
                'generation_rules': self.super_long_span_rules()
            }
        }
    
    def generate_cable_stayed_typology(self):
        """Generate cable-stayed bridge variants"""
        # Parametric generation rules
        tower_configurations = self.generate_tower_configurations()
        cable_arrangements = self.generate_cable_arrangements()
        deck_systems = self.generate_deck_systems()
        
        cable_stayed_variants = []
        
        for tower_config in tower_configurations:
            for cable_arrangement in cable_arrangements:
                for deck_system in deck_systems:
                    variant = CableStayedBridge({
                        'span': self.span,
                        'tower_configuration': tower_config,
                        'cable_arrangement': cable_arrangement,
                        'deck_system': deck_system
                    })
                    
                    # Apply generation rules
                    variant = self.apply_cable_optimization_rules(variant)
                    variant = self.apply_tower_optimization_rules(variant)
                    variant = self.apply_deck_optimization_rules(variant)
                    
                    if self.validate_bridge_design(variant):
                        cable_stayed_variants.append(variant)
        
        return cable_stayed_variants
    
    def generate_tower_configurations(self):
        """Generate tower geometry variants"""
        configurations = []
        
        # A-frame towers
        configurations.append({
            'type': 'a_frame',
            'geometry': self.create_a_frame_geometry(),
            'optimization_rules': self.a_frame_optimization_rules()
        })
        
        # H-frame towers
        configurations.append({
            'type': 'h_frame',
            'geometry': self.create_h_frame_geometry(),
            'optimization_rules': self.h_frame_optimization_rules()
        })
        
        # Diamond towers
        configurations.append({
            'type': 'diamond',
            'geometry': self.create_diamond_geometry(),
            'optimization_rules': self.diamond_optimization_rules()
        })
        
        return configurations
    
    def generate_cable_arrangements(self):
        """Generate cable stay arrangements"""
        arrangements = {
            'fan_pattern': {
                'geometry': self.create_fan_cable_pattern(),
                'advantages': ['Simple tower', 'Easy construction'],
                'disadvantages': ['Concentrated tower loads'],
                'optimization_rules': self.fan_pattern_rules()
            },
            'harp_pattern': {
                'geometry': self.create_harp_cable_pattern(),
                'advantages': ['Uniform tower loads', 'Better aesthetics'],
                'disadvantages': ['Complex tower', 'More cables'],
                'optimization_rules': self.harp_pattern_rules()
            },
            'semi_fan_pattern': {
                'geometry': self.create_semi_fan_cable_pattern(),
                'advantages': ['Compromise solution', 'Good efficiency'],
                'disadvantages': ['Moderate complexity'],
                'optimization_rules': self.semi_fan_pattern_rules()
            }
        }
        
        return arrangements
```

### 3. Space Frame Generation

```python
class SpaceFrameGenerator:
    def __init__(self, grid_parameters, loads):
        self.grid_parameters = grid_parameters
        self.loads = loads
        self.connection_systems = self.define_connection_systems()
    
    def generate_space_frame_topologies(self):
        """Generate space frame structural topologies"""
        topologies = []
        
        # Double layer grids
        topologies.extend(self.generate_double_layer_grids())
        
        # Barrel vaults
        topologies.extend(self.generate_barrel_vaults())
        
        # Domes
        topologies.extend(self.generate_dome_structures())
        
        # Free-form surfaces
        topologies.extend(self.generate_freeform_surfaces())
        
        return topologies
    
    def generate_double_layer_grids(self):
        """Generate double layer space frame variants"""
        grid_patterns = {
            'square_on_square_offset': {
                'top_layer': self.create_square_grid(offset=False),
                'bottom_layer': self.create_square_grid(offset=True),
                'web_members': self.create_offset_web_system(),
                'optimization_rules': self.square_offset_rules()
            },
            'triangular_grid': {
                'top_layer': self.create_triangular_grid(),
                'bottom_layer': self.create_triangular_grid(),
                'web_members': self.create_triangular_web_system(),
                'optimization_rules': self.triangular_grid_rules()
            },
            'hexagonal_grid': {
                'top_layer': self.create_hexagonal_grid(),
                'bottom_layer': self.create_hexagonal_grid(),
                'web_members': self.create_hexagonal_web_system(),
                'optimization_rules': self.hexagonal_grid_rules()
            }
        }
        
        return [self.instantiate_grid(pattern) for pattern in grid_patterns.values()]
    
    def create_triangular_grid(self):
        """Create triangular grid pattern"""
        grid = TriangularGrid(self.grid_parameters)
        
        # Apply generation rules
        grid.nodes = self.optimize_node_positions(grid.base_nodes)
        grid.members = self.optimize_member_sizing(grid.base_members)
        grid.connections = self.design_connections(grid.nodes, grid.members)
        
        return grid
    
    def optimize_node_positions(self, base_nodes):
        """Optimize node positions for structural efficiency"""
        optimization_variables = []
        for node in base_nodes:
            if node.movable:  # Some nodes fixed by boundary conditions
                optimization_variables.extend([node.x, node.y, node.z])
        
        # Multi-objective optimization
        objectives = [
            self.minimize_total_strain_energy,
            self.minimize_maximum_displacement,
            self.minimize_total_member_length,
            self.maximize_structural_stiffness
        ]
        
        optimal_positions = self.multi_objective_optimization(
            variables=optimization_variables,
            objectives=objectives,
            constraints=self.get_node_constraints()
        )
        
        return optimal_positions
```

## Topological Optimization Integration

### 1. SIMP Method for Typology Generation

```python
class SIMPTypologyGenerator:
    def __init__(self, design_domain, loads, constraints):
        self.design_domain = design_domain
        self.loads = loads
        self.constraints = constraints
        self.penalty_factor = 3.0
        self.filter_radius = 1.5
        self.volume_fraction = 0.5
    
    def generate_optimal_topology(self):
        """Generate structurally optimal topology using SIMP"""
        # Initialize density distribution
        densities = np.full(self.design_domain.elements.shape, self.volume_fraction)
        
        # Iterative optimization
        for iteration in range(200):
            # FEA with current densities
            displacement = self.finite_element_analysis(densities)
            
            # Sensitivity analysis
            sensitivities = self.calculate_sensitivities(densities, displacement)
            
            # Filtering
            filtered_sensitivities = self.density_filter(sensitivities)
            
            # Update densities
            new_densities = self.optimality_criteria_update(
                densities, filtered_sensitivities
            )
            
            # Convergence check
            if self.check_convergence(densities, new_densities):
                break
                
            densities = new_densities
        
        # Extract structural topology
        structural_topology = self.extract_structural_elements(densities)
        return structural_topology
    
    def extract_structural_elements(self, density_field):
        """Extract structural typology from optimized density field"""
        # Threshold density field
        binary_topology = (density_field > 0.5).astype(int)
        
        # Identify structural elements
        structural_elements = {
            'beams': self.identify_beam_elements(binary_topology),
            'columns': self.identify_column_elements(binary_topology),
            'braces': self.identify_brace_elements(binary_topology),
            'plates': self.identify_plate_elements(binary_topology)
        }
        
        # Generate design rules from topology
        design_rules = self.generate_rules_from_topology(structural_elements)
        
        return StructuralTypology(structural_elements, design_rules)
    
    def generate_rules_from_topology(self, structural_elements):
        """Generate parametric rules from optimized topology"""
        rules = {
            'member_sizing_rules': self.derive_sizing_rules(structural_elements),
            'connection_rules': self.derive_connection_rules(structural_elements),
            'load_path_rules': self.derive_load_path_rules(structural_elements),
            'geometry_rules': self.derive_geometry_rules(structural_elements)
        }
        
        return rules
```

### 2. Level Set Method for Boundary Evolution

```python
class LevelSetTypologyGenerator:
    def __init__(self, design_domain, objectives, constraints):
        self.design_domain = design_domain
        self.objectives = objectives
        self.constraints = constraints
        self.level_set_function = self.initialize_level_set()
    
    def evolve_structural_topology(self):
        """Evolve structural topology using level set method"""
        for iteration in range(100):
            # Calculate shape sensitivity
            shape_sensitivity = self.calculate_shape_sensitivity()
            
            # Update level set function
            self.level_set_function = self.update_level_set(shape_sensitivity)
            
            # Reinitialize level set function
            self.level_set_function = self.reinitialize_level_set()
            
            # Extract current topology
            current_topology = self.extract_topology()
            
            # Check convergence
            if self.topology_converged(current_topology):
                break
        
        # Generate structural typology
        final_topology = self.extract_final_topology()
        typology_rules = self.generate_typology_rules(final_topology)
        
        return StructuralTypology(final_topology, typology_rules)
    
    def extract_final_topology(self):
        """Extract final structural topology from level set"""
        # Zero level set defines structural boundary
        structural_boundary = self.extract_zero_level_set()
        
        # Generate structural members along boundary
        structural_members = self.generate_members_from_boundary(structural_boundary)
        
        # Optimize member cross-sections
        optimized_members = self.optimize_member_sections(structural_members)
        
        return optimized_members
```

## Grammar Validation and Performance Assessment

### 1. Structural Performance Validation

```python
def validate_generated_typology(typology, performance_criteria):
    """Comprehensive validation of generated structural typology"""
    validation_results = {
        'structural_adequacy': validate_structural_adequacy(typology),
        'constructability': assess_constructability(typology),
        'economic_efficiency': evaluate_economic_performance(typology),
        'architectural_integration': check_architectural_compatibility(typology),
        'sustainability_metrics': calculate_sustainability_scores(typology)
    }
    
    return validation_results

def validate_structural_adequacy(typology):
    """Validate structural performance of generated typology"""
    adequacy_checks = {
        'strength_check': verify_strength_requirements(typology),
        'stiffness_check': verify_stiffness_requirements(typology),
        'stability_check': verify_stability_requirements(typology),
        'dynamic_check': verify_dynamic_performance(typology),
        'fatigue_check': verify_fatigue_resistance(typology)
    }
    
    overall_adequacy = all(adequacy_checks.values())
    return {
        'individual_checks': adequacy_checks,
        'overall_adequate': overall_adequacy,
        'safety_factors': calculate_safety_factors(typology)
    }
```

### 2. Generation Rule Quality Assessment

```python
def assess_generation_rule_quality(rules, test_cases):
    """Assess quality and robustness of generation rules"""
    quality_metrics = {
        'completeness': assess_rule_completeness(rules, test_cases),
        'consistency': check_rule_consistency(rules),
        'efficiency': measure_generation_efficiency(rules),
        'novelty': evaluate_design_novelty(rules, test_cases),
        'practicality': assess_practical_implementability(rules)
    }
    
    return quality_metrics

def assess_rule_completeness(rules, test_cases):
    """Check if rules can handle all expected design scenarios"""
    coverage_score = 0
    for test_case in test_cases:
        if rules.can_generate_solution(test_case):
            coverage_score += 1
    
    completeness_ratio = coverage_score / len(test_cases)
    return {
        'coverage_ratio': completeness_ratio,
        'uncovered_cases': identify_uncovered_cases(rules, test_cases),
        'rule_gaps': identify_rule_gaps(rules, test_cases)
    }
```

## Implementation Strategy

The typology generation system should be implemented with the following priorities:

1. **Rule-Based Foundation**: Establish clear generation rules based on structural principles
2. **Parametric Flexibility**: Enable systematic parameter variation within typologies
3. **Optimization Integration**: Incorporate optimization algorithms for rule refinement
4. **Validation Framework**: Ensure generated typologies meet performance requirements
5. **Extensibility**: Allow for rule enhancement and new typology integration

This systematic approach to typology generation enables the creation of comprehensive design grammars that can generate families of structurally sound, economically viable, and architecturally integrated solutions.