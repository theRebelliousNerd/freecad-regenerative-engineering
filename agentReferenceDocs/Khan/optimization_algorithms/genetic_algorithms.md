# Genetic Algorithms for Structural Optimization

## Overview

Genetic algorithms (GAs) provide powerful evolutionary optimization methods for complex structural design problems where traditional gradient-based methods may fail. This guide covers implementation of genetic algorithms specifically tailored for structural optimization in FreeCAD environments.

## Fundamental GA Concepts for Structural Design

### 1. Encoding Schemes for Structural Parameters

```python
class StructuralGeneticAlgorithm:
    def __init__(self, problem_definition):
        self.problem = problem_definition
        self.population_size = 100
        self.generations = 500
        self.crossover_rate = 0.8
        self.mutation_rate = 0.02
        self.selection_method = 'tournament'
    
    def encode_structural_parameters(self, design_variables):
        """Convert structural parameters to genetic representation"""
        encoding_methods = {
            'real_valued': self.real_value_encoding,
            'binary': self.binary_encoding,
            'integer': self.integer_encoding,
            'permutation': self.permutation_encoding,
            'tree': self.tree_encoding
        }
        
        encoded_chromosome = {}
        for var_name, var_data in design_variables.items():
            encoding_type = var_data.get('encoding', 'real_valued')
            encoded_chromosome[var_name] = encoding_methods[encoding_type](var_data)
        
        return encoded_chromosome
    
    def real_value_encoding(self, variable_data):
        """Real-valued encoding for continuous structural parameters"""
        min_value = variable_data['bounds'][0]
        max_value = variable_data['bounds'][1]
        precision = variable_data.get('precision', 0.01)
        
        # Generate random value within bounds
        value = random.uniform(min_value, max_value)
        
        # Apply precision constraint
        value = round(value / precision) * precision
        
        return {
            'type': 'real',
            'value': value,
            'bounds': (min_value, max_value),
            'precision': precision
        }
    
    def binary_encoding(self, variable_data):
        """Binary encoding for discrete structural choices"""
        bit_length = variable_data.get('bit_length', 8)
        min_value = variable_data['bounds'][0]
        max_value = variable_data['bounds'][1]
        
        # Calculate number of possible values
        num_values = 2**bit_length - 1
        value_range = max_value - min_value
        
        # Generate random binary string
        binary_string = ''.join([str(random.randint(0, 1)) for _ in range(bit_length)])
        
        # Convert to actual value
        decimal_value = int(binary_string, 2)
        actual_value = min_value + (decimal_value / num_values) * value_range
        
        return {
            'type': 'binary',
            'binary_string': binary_string,
            'value': actual_value,
            'bit_length': bit_length
        }
```

### 2. Fitness Function Design for Structural Problems

```python
def create_structural_fitness_function(objectives, constraints, weights):
    """Create comprehensive fitness function for structural optimization"""
    
    def fitness_function(individual, freecad_doc=None):
        """Evaluate structural design fitness"""
        
        # Decode individual to design parameters
        design_params = decode_individual(individual)
        
        # Update FreeCAD model if provided
        if freecad_doc:
            update_freecad_model(freecad_doc, design_params)
            geometric_properties = extract_geometric_properties(freecad_doc)
        else:
            geometric_properties = calculate_properties_analytically(design_params)
        
        # Calculate objective values
        objective_values = {}
        for obj_name, obj_func in objectives.items():
            objective_values[obj_name] = obj_func(design_params, geometric_properties)
        
        # Evaluate constraints
        constraint_violations = 0
        constraint_penalty = 0
        
        for const_name, const_func in constraints.items():
            violation = const_func(design_params, geometric_properties)
            if violation > 0:
                constraint_violations += 1
                constraint_penalty += violation
        
        # Multi-objective fitness calculation
        if len(objectives) == 1:
            # Single objective with penalty method
            fitness = objective_values[list(objectives.keys())[0]]
            if constraint_violations > 0:
                fitness += 1e6 * constraint_penalty  # Large penalty for infeasible solutions
        else:
            # Multi-objective fitness (Pareto-based)
            fitness = {
                'objectives': objective_values,
                'constraint_violation': constraint_penalty,
                'feasible': constraint_violations == 0
            }
        
        return fitness
    
    return fitness_function

def structural_objectives_library():
    """Library of common structural optimization objectives"""
    return {
        'minimize_weight': lambda params, props: props['total_mass'],
        'minimize_deflection': lambda params, props: props['max_deflection'],
        'minimize_stress': lambda params, props: props['max_stress'] / props['allowable_stress'],
        'minimize_cost': lambda params, props: calculate_material_cost(props) + calculate_fabrication_cost(params),
        'maximize_stiffness': lambda params, props: 1.0 / props['deflection_index'],
        'minimize_buckling_ratio': lambda params, props: props['applied_load'] / props['critical_buckling_load'],
        'maximize_frequency': lambda params, props: props['fundamental_frequency'],
        'minimize_volume': lambda params, props: props['total_volume']
    }

def structural_constraints_library():
    """Library of common structural constraints"""
    return {
        'stress_constraint': lambda params, props: max(0, props['max_stress'] - props['allowable_stress']),
        'deflection_constraint': lambda params, props: max(0, props['max_deflection'] - props['allowable_deflection']),
        'frequency_constraint': lambda params, props: max(0, props['min_frequency'] - props['fundamental_frequency']),
        'buckling_constraint': lambda params, props: max(0, 2.0 - props['buckling_safety_factor']),
        'geometric_constraint': lambda params, props: check_geometric_feasibility(params),
        'manufacturing_constraint': lambda params, props: check_manufacturing_feasibility(params)
    }
```

### 3. Selection Methods for Structural Optimization

```python
class StructuralSelection:
    def __init__(self, selection_pressure=2.0):
        self.selection_pressure = selection_pressure
    
    def tournament_selection(self, population, tournament_size=3):
        """Tournament selection optimized for structural problems"""
        selected_parents = []
        
        for _ in range(len(population)):
            # Select random tournament participants
            tournament = random.sample(population, tournament_size)
            
            # Find best individual based on structural fitness
            best_individual = self.find_best_structural_individual(tournament)
            selected_parents.append(best_individual)
        
        return selected_parents
    
    def find_best_structural_individual(self, individuals):
        """Find best individual considering structural constraints"""
        feasible_individuals = [ind for ind in individuals if ind.fitness.get('feasible', True)]
        
        if feasible_individuals:
            # Select from feasible solutions
            return min(feasible_individuals, key=lambda x: x.fitness['objectives'].get('weight', float('inf')))
        else:
            # Select least infeasible solution
            return min(individuals, key=lambda x: x.fitness.get('constraint_violation', float('inf')))
    
    def rank_based_selection(self, population):
        """Rank-based selection for structural multi-objective problems"""
        # Sort by constraint violation first, then by objective
        def sorting_key(individual):
            if hasattr(individual.fitness, 'constraint_violation'):
                return (individual.fitness['constraint_violation'], 
                       individual.fitness['objectives'].get('weight', 0))
            else:
                return individual.fitness
        
        sorted_population = sorted(population, key=sorting_key)
        
        # Assign selection probabilities based on rank
        selection_probs = []
        for i, individual in enumerate(sorted_population):
            rank = len(population) - i
            prob = (2 - self.selection_pressure) + 2 * (self.selection_pressure - 1) * (rank - 1) / (len(population) - 1)
            selection_probs.append(prob / len(population))
        
        # Select individuals based on probabilities
        selected = []
        for _ in range(len(population)):
            selected_index = self.roulette_wheel_selection(selection_probs)
            selected.append(sorted_population[selected_index])
        
        return selected
    
    def nsga_selection(self, population):
        """NSGA-II selection for multi-objective structural optimization"""
        # Fast non-dominated sorting
        fronts = self.fast_non_dominated_sort(population)
        
        # Calculate crowding distance for each front
        for front in fronts:
            self.calculate_crowding_distance(front)
        
        # Select individuals for next generation
        selected = []
        for front in fronts:
            if len(selected) + len(front) <= len(population):
                selected.extend(front)
            else:
                # Sort remaining front by crowding distance
                front.sort(key=lambda x: x.crowding_distance, reverse=True)
                remaining_slots = len(population) - len(selected)
                selected.extend(front[:remaining_slots])
                break
        
        return selected
```

### 4. Crossover Operators for Structural Parameters

```python
class StructuralCrossover:
    def __init__(self, crossover_probability=0.8):
        self.crossover_probability = crossover_probability
    
    def structural_blend_crossover(self, parent1, parent2, alpha=0.5):
        """Blend crossover optimized for structural parameters"""
        if random.random() > self.crossover_probability:
            return parent1.copy(), parent2.copy()
        
        child1 = parent1.copy()
        child2 = parent2.copy()
        
        # Blend continuous parameters
        for param_name in parent1.parameters:
            if param_name in parent2.parameters:
                p1_val = parent1.parameters[param_name]['value']
                p2_val = parent2.parameters[param_name]['value']
                
                # Calculate blend range
                diff = abs(p1_val - p2_val)
                min_val = min(p1_val, p2_val) - alpha * diff
                max_val = max(p1_val, p2_val) + alpha * diff
                
                # Ensure bounds are respected
                bounds = parent1.parameters[param_name].get('bounds', (None, None))
                if bounds[0] is not None:
                    min_val = max(min_val, bounds[0])
                if bounds[1] is not None:
                    max_val = min(max_val, bounds[1])
                
                # Generate offspring values
                child1.parameters[param_name]['value'] = random.uniform(min_val, max_val)
                child2.parameters[param_name]['value'] = random.uniform(min_val, max_val)
        
        return child1, child2
    
    def sectional_crossover(self, parent1, parent2):
        """Crossover operator for structural sections (I-beams, etc.)"""
        child1 = parent1.copy()
        child2 = parent2.copy()
        
        # Group related parameters
        section_groups = {
            'flange_params': ['flange_width', 'flange_thickness'],
            'web_params': ['web_height', 'web_thickness'],
            'geometric_params': ['length', 'orientation']
        }
        
        # Crossover by parameter groups
        for group_name, param_list in section_groups.items():
            if random.random() < 0.5:  # Swap this group
                for param in param_list:
                    if param in parent1.parameters and param in parent2.parameters:
                        temp = child1.parameters[param]['value']
                        child1.parameters[param]['value'] = child2.parameters[param]['value']
                        child2.parameters[param]['value'] = temp
        
        return child1, child2
    
    def topology_crossover(self, parent1, parent2):
        """Crossover for topological optimization problems"""
        # This handles cases where structure connectivity can change
        child1_topology = parent1.topology.copy()
        child2_topology = parent2.topology.copy()
        
        # Identify common nodes/elements
        common_elements = set(parent1.topology.elements.keys()) & set(parent2.topology.elements.keys())
        
        # Randomly assign elements from each parent
        for element_id in common_elements:
            if random.random() < 0.5:
                child1_topology.elements[element_id] = parent2.topology.elements[element_id]
                child2_topology.elements[element_id] = parent1.topology.elements[element_id]
        
        return child1_topology, child2_topology
```

### 5. Mutation Operators for Structural Design

```python
class StructuralMutation:
    def __init__(self, mutation_probability=0.02):
        self.mutation_probability = mutation_probability
    
    def gaussian_mutation(self, individual, mutation_strength=0.1):
        """Gaussian mutation for continuous structural parameters"""
        mutated_individual = individual.copy()
        
        for param_name, param_data in mutated_individual.parameters.items():
            if random.random() < self.mutation_probability:
                current_value = param_data['value']
                bounds = param_data.get('bounds', (None, None))
                
                # Calculate mutation range based on parameter bounds
                if bounds[0] is not None and bounds[1] is not None:
                    param_range = bounds[1] - bounds[0]
                    mutation_std = mutation_strength * param_range
                else:
                    mutation_std = mutation_strength * abs(current_value)
                
                # Apply Gaussian mutation
                mutation_delta = random.gauss(0, mutation_std)
                new_value = current_value + mutation_delta
                
                # Ensure bounds are respected
                if bounds[0] is not None:
                    new_value = max(new_value, bounds[0])
                if bounds[1] is not None:
                    new_value = min(new_value, bounds[1])
                
                mutated_individual.parameters[param_name]['value'] = new_value
        
        return mutated_individual
    
    def structural_specific_mutation(self, individual):
        """Mutation operators specific to structural engineering"""
        mutated_individual = individual.copy()
        
        mutation_operators = {
            'resize_section': self.resize_section_mutation,
            'change_material': self.material_mutation,
            'add_stiffener': self.stiffener_mutation,
            'modify_connection': self.connection_mutation
        }
        
        # Select random mutation operator
        selected_operator = random.choice(list(mutation_operators.keys()))
        mutated_individual = mutation_operators[selected_operator](mutated_individual)
        
        return mutated_individual
    
    def resize_section_mutation(self, individual):
        """Mutate structural section dimensions"""
        section_params = ['depth', 'width', 'thickness', 'flange_thickness', 'web_thickness']
        available_params = [p for p in section_params if p in individual.parameters]
        
        if available_params:
            selected_param = random.choice(available_params)
            current_value = individual.parameters[selected_param]['value']
            
            # Apply scaling mutation
            scale_factor = random.uniform(0.8, 1.2)  # ±20% change
            new_value = current_value * scale_factor
            
            # Respect bounds
            bounds = individual.parameters[selected_param].get('bounds', (None, None))
            if bounds[0] is not None:
                new_value = max(new_value, bounds[0])
            if bounds[1] is not None:
                new_value = min(new_value, bounds[1])
            
            individual.parameters[selected_param]['value'] = new_value
        
        return individual
    
    def material_mutation(self, individual):
        """Mutate material selection"""
        if 'material_type' in individual.parameters:
            available_materials = individual.parameters['material_type'].get('options', [])
            if available_materials:
                new_material = random.choice(available_materials)
                individual.parameters['material_type']['value'] = new_material
        
        return individual
```

### 6. Integration with FreeCAD

```python
class FreeCADGeneticOptimization:
    def __init__(self, freecad_model_path):
        self.model_path = freecad_model_path
        self.doc = FreeCAD.openDocument(freecad_model_path)
        self.parameter_mapping = self.create_parameter_mapping()
    
    def create_parameter_mapping(self):
        """Map GA parameters to FreeCAD model parameters"""
        spreadsheet = self.doc.getObject('DesignParameters')
        if not spreadsheet:
            raise ValueError("FreeCAD model must contain 'DesignParameters' spreadsheet")
        
        mapping = {}
        # Map spreadsheet cells to GA parameters
        for cell in spreadsheet.PropertiesList:
            if cell.startswith('C'):  # Assuming column C contains parameter values
                param_name = spreadsheet.get(f'A{cell[1:]}')  # Parameter name in column A
                mapping[param_name] = cell
        
        return mapping
    
    def update_freecad_model(self, individual):
        """Update FreeCAD model with GA individual parameters"""
        spreadsheet = self.doc.getObject('DesignParameters')
        
        for param_name, param_data in individual.parameters.items():
            if param_name in self.parameter_mapping:
                cell_address = self.parameter_mapping[param_name]
                spreadsheet.set(cell_address, str(param_data['value']))
        
        # Recompute model
        self.doc.recompute()
        
        # Handle recompute errors
        if self.doc.State != 'Valid':
            return False  # Model update failed
        
        return True
    
    def extract_model_properties(self):
        """Extract structural properties from updated FreeCAD model"""
        properties = {}
        
        # Extract geometric properties
        total_volume = 0
        total_mass = 0
        
        for obj in self.doc.Objects:
            if hasattr(obj, 'Shape') and obj.Shape.Volume > 0:
                volume = obj.Shape.Volume
                # Get material density (assume steel if not specified)
                density = getattr(obj, 'Material', {}).get('Density', 7850)  # kg/m³
                mass = volume * density / 1e9  # Convert mm³ to m³
                
                total_volume += volume
                total_mass += mass
        
        properties['total_volume'] = total_volume
        properties['total_mass'] = total_mass
        
        # Extract FEM results if available
        fem_analysis = self.doc.getObject('FEMAnalysis')
        if fem_analysis:
            properties.update(self.extract_fem_results(fem_analysis))
        
        return properties
    
    def run_genetic_optimization(self, optimization_setup):
        """Run genetic algorithm optimization with FreeCAD evaluation"""
        ga = StructuralGeneticAlgorithm(optimization_setup)
        
        # Initialize population
        population = ga.initialize_population()
        
        # Evolution loop
        best_fitness_history = []
        
        for generation in range(ga.generations):
            print(f"Generation {generation + 1}")
            
            # Evaluate population
            for individual in population:
                if self.update_freecad_model(individual):
                    properties = self.extract_model_properties()
                    individual.fitness = ga.fitness_function(individual, properties)
                else:
                    # Assign penalty fitness for invalid models
                    individual.fitness = {'constraint_violation': 1e6, 'feasible': False}
            
            # Track best fitness
            best_individual = min(population, key=lambda x: x.fitness.get('constraint_violation', 0))
            best_fitness_history.append(best_individual.fitness)
            
            # Selection
            parents = ga.selection(population)
            
            # Crossover and mutation
            offspring = []
            for i in range(0, len(parents), 2):
                if i + 1 < len(parents):
                    child1, child2 = ga.crossover(parents[i], parents[i + 1])
                    child1 = ga.mutation(child1)
                    child2 = ga.mutation(child2)
                    offspring.extend([child1, child2])
            
            # Create next generation
            population = ga.survivor_selection(parents + offspring)
            
            # Log progress
            print(f"Best fitness: {best_individual.fitness}")
        
        # Return optimization results
        return {
            'best_individual': best_individual,
            'best_fitness_history': best_fitness_history,
            'final_population': population
        }
```

### 7. Advanced GA Techniques for Structural Problems

```python
class AdvancedStructuralGA:
    def __init__(self):
        self.adaptive_parameters = True
        self.niching_enabled = True
        self.multi_population = True
    
    def adaptive_parameter_control(self, generation, max_generations, population_diversity):
        """Adapt GA parameters based on search progress"""
        progress = generation / max_generations
        
        # Adaptive mutation rate
        if population_diversity < 0.1:  # Low diversity
            mutation_rate = 0.05  # Increase mutation
        elif population_diversity > 0.8:  # High diversity
            mutation_rate = 0.01  # Decrease mutation
        else:
            mutation_rate = 0.02 + 0.03 * (1 - progress)  # Decrease over time
        
        # Adaptive crossover rate
        crossover_rate = 0.9 - 0.2 * progress  # Decrease over time
        
        return {
            'mutation_rate': mutation_rate,
            'crossover_rate': crossover_rate,
            'selection_pressure': 1.5 + 0.5 * progress
        }
    
    def calculate_population_diversity(self, population):
        """Calculate diversity measure for structural population"""
        if len(population) < 2:
            return 0.0
        
        total_distance = 0
        comparison_count = 0
        
        for i in range(len(population)):
            for j in range(i + 1, len(population)):
                distance = self.calculate_structural_distance(population[i], population[j])
                total_distance += distance
                comparison_count += 1
        
        average_distance = total_distance / comparison_count if comparison_count > 0 else 0
        return average_distance
    
    def calculate_structural_distance(self, individual1, individual2):
        """Calculate distance between two structural designs"""
        total_distance = 0
        param_count = 0
        
        common_params = set(individual1.parameters.keys()) & set(individual2.parameters.keys())
        
        for param in common_params:
            val1 = individual1.parameters[param]['value']
            val2 = individual2.parameters[param]['value']
            bounds = individual1.parameters[param].get('bounds', (0, 1))
            
            # Normalize by parameter range
            param_range = bounds[1] - bounds[0] if bounds[1] != bounds[0] else 1
            normalized_distance = abs(val1 - val2) / param_range
            
            total_distance += normalized_distance
            param_count += 1
        
        return total_distance / param_count if param_count > 0 else 0
    
    def niching_selection(self, population, niche_radius=0.1):
        """Maintain diversity through niching"""
        niches = []
        
        for individual in population:
            assigned_to_niche = False
            
            for niche in niches:
                if self.calculate_structural_distance(individual, niche['representative']) < niche_radius:
                    niche['members'].append(individual)
                    assigned_to_niche = True
                    break
            
            if not assigned_to_niche:
                niches.append({
                    'representative': individual,
                    'members': [individual]
                })
        
        # Select best individual from each niche
        selected = []
        for niche in niches:
            best_in_niche = min(niche['members'], 
                               key=lambda x: x.fitness.get('constraint_violation', 0))
            selected.append(best_in_niche)
        
        return selected
```

This comprehensive genetic algorithm framework provides robust optimization capabilities specifically tailored for structural engineering problems in FreeCAD environments, with advanced features for handling constraints, maintaining diversity, and adapting to problem characteristics.