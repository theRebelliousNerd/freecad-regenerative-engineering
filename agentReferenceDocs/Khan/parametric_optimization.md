# Parametric Optimization Methods

## Introduction to Parametric Design Space

Parametric optimization transforms structural design from fixed solutions to explorable solution spaces. By defining relationships between design variables, we can systematically search for optimal configurations that balance multiple objectives.

## Core Parametric Variables

### Geometric Parameters

```python
class StructuralParameters:
    # Primary dimensions
    building_height = Parameter(50, 500, unit='m')
    floor_to_floor = Parameter(3.0, 5.0, unit='m')
    footprint_x = Parameter(20, 80, unit='m')
    footprint_y = Parameter(20, 80, unit='m')
    
    # Structural grid
    column_grid_x = Parameter(3, 12, unit='m')
    column_grid_y = Parameter(3, 12, unit='m')
    
    # Member sizes
    column_dimension = Parameter(400, 1500, unit='mm')
    beam_depth = Parameter(300, 1200, unit='mm')
    slab_thickness = Parameter(150, 350, unit='mm')
    core_wall_thickness = Parameter(200, 800, unit='mm')
```

### Material Parameters

```python
material_properties = {
    'concrete': {
        'strength': Parameter(25, 80, unit='MPa'),
        'density': 2400,  # kg/m³
        'E_modulus': lambda fc: 4700 * sqrt(fc),  # MPa
        'cost': Parameter(100, 200, unit='$/m³')
    },
    'steel': {
        'yield_strength': Parameter(250, 550, unit='MPa'),
        'density': 7850,  # kg/m³
        'E_modulus': 200000,  # MPa
        'cost': Parameter(800, 1500, unit='$/ton')
    }
}
```

## Optimization Algorithms

### 1. Genetic Algorithm Implementation

```python
class GeneticOptimizer:
    def __init__(self, population_size=100, generations=500):
        self.population_size = population_size
        self.generations = generations
        self.mutation_rate = 0.1
        self.crossover_rate = 0.7
        
    def create_individual(self):
        """Create random individual with parameters"""
        return {
            'column_spacing': random.uniform(3, 9),
            'beam_depth': random.uniform(400, 1000),
            'core_thickness': random.uniform(200, 600),
            'material_grade': random.choice([30, 40, 50, 60]),
        }
    
    def fitness_function(self, individual):
        """Multi-objective fitness evaluation"""
        structure = create_structure(individual)
        
        # Calculate objectives
        material_cost = calculate_material_cost(structure)
        drift_ratio = calculate_drift(structure)
        usable_area = calculate_usable_area(structure)
        
        # Weighted fitness
        fitness = (
            0.4 * (1 / material_cost) +
            0.3 * (1 / drift_ratio) +
            0.3 * usable_area
        )
        return fitness
    
    def crossover(self, parent1, parent2):
        """Blend crossover for continuous variables"""
        alpha = 0.5
        child = {}
        for key in parent1.keys():
            if random.random() < self.crossover_rate:
                child[key] = alpha * parent1[key] + (1-alpha) * parent2[key]
            else:
                child[key] = parent1[key] if random.random() < 0.5 else parent2[key]
        return child
    
    def mutate(self, individual):
        """Gaussian mutation"""
        for key in individual.keys():
            if random.random() < self.mutation_rate:
                sigma = 0.1 * (param_max[key] - param_min[key])
                individual[key] += random.gauss(0, sigma)
                individual[key] = clip(individual[key], param_min[key], param_max[key])
        return individual
```

### 2. Particle Swarm Optimization

```python
class ParticleSwarmOptimizer:
    def __init__(self, n_particles=50, n_iterations=200):
        self.n_particles = n_particles
        self.n_iterations = n_iterations
        self.w = 0.7  # inertia weight
        self.c1 = 1.5  # cognitive parameter
        self.c2 = 1.5  # social parameter
        
    def optimize(self, objective_function, bounds):
        # Initialize swarm
        swarm = self.initialize_swarm(bounds)
        global_best = None
        global_best_fitness = float('inf')
        
        for iteration in range(self.n_iterations):
            for particle in swarm:
                # Evaluate fitness
                fitness = objective_function(particle.position)
                
                # Update personal best
                if fitness < particle.best_fitness:
                    particle.best_position = particle.position.copy()
                    particle.best_fitness = fitness
                
                # Update global best
                if fitness < global_best_fitness:
                    global_best = particle.position.copy()
                    global_best_fitness = fitness
            
            # Update velocities and positions
            for particle in swarm:
                particle.velocity = (
                    self.w * particle.velocity +
                    self.c1 * random.random() * (particle.best_position - particle.position) +
                    self.c2 * random.random() * (global_best - particle.position)
                )
                particle.position += particle.velocity
                particle.position = clip(particle.position, bounds)
        
        return global_best, global_best_fitness
```

### 3. Gradient-Based Optimization

```python
class GradientOptimizer:
    def __init__(self, learning_rate=0.01, tolerance=1e-6):
        self.learning_rate = learning_rate
        self.tolerance = tolerance
        
    def compute_gradient(self, f, x, h=1e-5):
        """Numerical gradient computation"""
        grad = np.zeros_like(x)
        for i in range(len(x)):
            x_plus = x.copy()
            x_minus = x.copy()
            x_plus[i] += h
            x_minus[i] -= h
            grad[i] = (f(x_plus) - f(x_minus)) / (2 * h)
        return grad
    
    def optimize(self, objective, initial_point, constraints=None):
        x = initial_point.copy()
        
        for iteration in range(1000):
            # Compute gradient
            grad = self.compute_gradient(objective, x)
            
            # Apply constraints using projection
            if constraints:
                grad = self.project_gradient(grad, x, constraints)
            
            # Update parameters
            x_new = x - self.learning_rate * grad
            
            # Check convergence
            if np.linalg.norm(x_new - x) < self.tolerance:
                break
            
            x = x_new
        
        return x
```

## Topology Optimization

### SIMP Method Implementation

```python
class SIMPOptimizer:
    """Solid Isotropic Material with Penalization"""
    
    def __init__(self, nelx=60, nely=30, volfrac=0.4, penal=3):
        self.nelx = nelx  # elements in x
        self.nely = nely  # elements in y
        self.volfrac = volfrac  # volume fraction
        self.penal = penal  # penalization factor
        
    def optimize(self):
        # Initialize density distribution
        x = self.volfrac * np.ones((self.nely, self.nelx))
        
        loop = 0
        change = 1
        
        while change > 0.01 and loop < 200:
            loop += 1
            
            # FE-Analysis
            U = self.FE_analysis(x)
            
            # Objective and sensitivity
            c, dc = self.objective_sensitivity(x, U)
            
            # Filtering
            dc = self.sensitivity_filter(x, dc)
            
            # Optimality criteria update
            x_new = self.OC_update(x, dc)
            
            # Compute change
            change = np.max(np.abs(x_new - x))
            x = x_new
            
            print(f"Iteration {loop}: Obj = {c:.3f}, Vol = {np.mean(x):.3f}")
        
        return x
    
    def material_model(self, x):
        """SIMP material interpolation"""
        E = self.E_min + x**self.penal * (self.E_0 - self.E_min)
        return E
```

### Level-Set Method with B-Splines

```python
class LevelSetOptimizer:
    def __init__(self, domain_size, control_points=20):
        self.domain = domain_size
        self.n_control = control_points
        
    def create_level_set(self, control_values):
        """Create level-set function using B-spline interpolation"""
        x = np.linspace(0, self.domain[0], 100)
        y = np.linspace(0, self.domain[1], 100)
        
        # B-spline surface from control points
        tck = interpolate.bisplrep(
            control_points_x, 
            control_points_y, 
            control_values,
            s=0
        )
        
        # Evaluate level-set on grid
        phi = interpolate.bisplev(x, y, tck)
        
        return phi
    
    def evolve_level_set(self, phi, velocity):
        """Evolve level-set using Hamilton-Jacobi equation"""
        dt = 0.1
        phi_new = phi - dt * velocity * np.abs(np.gradient(phi))
        return phi_new
```

## Multi-Objective Optimization

### Pareto Front Generation

```python
class ParetoOptimizer:
    def __init__(self, objectives):
        self.objectives = objectives
        
    def is_dominated(self, sol1, sol2):
        """Check if sol1 is dominated by sol2"""
        better_in_any = False
        for obj in self.objectives:
            if obj(sol1) > obj(sol2):
                return False
            if obj(sol1) < obj(sol2):
                better_in_any = True
        return better_in_any
    
    def find_pareto_front(self, solutions):
        """Extract non-dominated solutions"""
        pareto_front = []
        
        for i, sol1 in enumerate(solutions):
            dominated = False
            for j, sol2 in enumerate(solutions):
                if i != j and self.is_dominated(sol1, sol2):
                    dominated = True
                    break
            if not dominated:
                pareto_front.append(sol1)
        
        return pareto_front
    
    def weighted_sum_method(self, weights):
        """Scalarize multi-objective problem"""
        def combined_objective(x):
            total = 0
            for i, obj in enumerate(self.objectives):
                total += weights[i] * obj(x)
            return total
        return combined_objective
```

## Parametric Sweep Strategies

### Full Factorial Design

```python
def full_factorial_sweep(parameters, levels):
    """Generate all parameter combinations"""
    from itertools import product
    
    param_ranges = {}
    for param, (min_val, max_val) in parameters.items():
        param_ranges[param] = np.linspace(min_val, max_val, levels)
    
    combinations = list(product(*param_ranges.values()))
    
    results = []
    for combo in combinations:
        design = dict(zip(parameters.keys(), combo))
        performance = evaluate_design(design)
        results.append((design, performance))
    
    return results
```

### Latin Hypercube Sampling

```python
def latin_hypercube_sampling(parameters, n_samples):
    """Efficient sampling of parameter space"""
    from pyDOE import lhs
    
    n_params = len(parameters)
    samples = lhs(n_params, samples=n_samples)
    
    # Scale samples to parameter ranges
    designs = []
    for sample in samples:
        design = {}
        for i, (param, (min_val, max_val)) in enumerate(parameters.items()):
            design[param] = min_val + sample[i] * (max_val - min_val)
        designs.append(design)
    
    return designs
```

## FreeCAD Integration

### Parametric Model Generation

```python
import FreeCAD
import Part

class ParametricStructure:
    def __init__(self, doc):
        self.doc = doc
        
    def create_parametric_column(self, x, y, height, width, depth):
        """Create parametric column"""
        col = self.doc.addObject("Part::Box", "Column")
        col.Length = width
        col.Width = depth
        col.Height = height
        col.Placement.Base = FreeCAD.Vector(x, y, 0)
        
        # Make parameters accessible
        self.doc.recompute()
        return col
    
    def create_parametric_frame(self, grid_x, grid_y, n_floors):
        """Generate full parametric structural frame"""
        columns = []
        beams = []
        
        for i in range(len(grid_x)):
            for j in range(len(grid_y)):
                # Create column
                col = self.create_parametric_column(
                    grid_x[i], grid_y[j], 
                    n_floors * 3500,  # floor height
                    400, 400  # column size
                )
                columns.append(col)
        
        # Create beams between columns
        for floor in range(n_floors):
            z = floor * 3500
            # X-direction beams
            for i in range(len(grid_x)-1):
                for j in range(len(grid_y)):
                    beam = self.create_beam(
                        grid_x[i], grid_y[j], z,
                        grid_x[i+1] - grid_x[i],
                        'x'
                    )
                    beams.append(beam)
        
        return columns, beams
```

### Optimization Loop Integration

```python
def optimize_structure_in_freecad():
    """Main optimization routine for FreeCAD"""
    
    # Define parameter ranges
    params = {
        'column_spacing': (3000, 9000),
        'beam_depth': (400, 1000),
        'column_size': (400, 800),
    }
    
    # Initialize optimizer
    optimizer = GeneticOptimizer()
    
    best_fitness = float('inf')
    best_design = None
    
    for generation in range(100):
        # Generate population
        population = optimizer.create_population()
        
        for individual in population:
            # Create FreeCAD model
            model = create_parametric_model(individual)
            
            # Run FEM analysis
            fem_results = run_fem_analysis(model)
            
            # Evaluate fitness
            fitness = evaluate_fitness(fem_results, individual)
            
            if fitness < best_fitness:
                best_fitness = fitness
                best_design = individual
                save_model(model, f"optimal_gen_{generation}")
        
        # Evolve population
        population = optimizer.evolve(population)
    
    return best_design
```

## Performance Metrics

### Optimization Convergence Tracking

```python
class OptimizationMonitor:
    def __init__(self):
        self.history = {
            'iteration': [],
            'objective': [],
            'constraints': [],
            'parameters': []
        }
    
    def log_iteration(self, iteration, objective, constraints, parameters):
        self.history['iteration'].append(iteration)
        self.history['objective'].append(objective)
        self.history['constraints'].append(constraints)
        self.history['parameters'].append(parameters.copy())
    
    def plot_convergence(self):
        import matplotlib.pyplot as plt
        
        plt.figure(figsize=(12, 4))
        
        # Objective convergence
        plt.subplot(1, 3, 1)
        plt.plot(self.history['iteration'], self.history['objective'])
        plt.xlabel('Iteration')
        plt.ylabel('Objective Value')
        plt.title('Optimization Convergence')
        
        # Parameter evolution
        plt.subplot(1, 3, 2)
        params = np.array(self.history['parameters'])
        for i in range(params.shape[1]):
            plt.plot(self.history['iteration'], params[:, i], 
                    label=f'Param {i+1}')
        plt.xlabel('Iteration')
        plt.ylabel('Parameter Value')
        plt.legend()
        
        # Constraint satisfaction
        plt.subplot(1, 3, 3)
        constraints = np.array(self.history['constraints'])
        plt.plot(self.history['iteration'], np.max(constraints, axis=1))
        plt.xlabel('Iteration')
        plt.ylabel('Max Constraint Violation')
        plt.axhline(y=0, color='r', linestyle='--')
        
        plt.tight_layout()
        plt.show()
```

## Summary

Parametric optimization provides a systematic framework for exploring vast design spaces and finding optimal structural configurations. Key principles:

1. **Define Clear Parameters**: Identify all variable aspects of the design
2. **Choose Appropriate Algorithms**: Match optimization method to problem characteristics
3. **Implement Robust Evaluation**: Accurate fitness/objective functions
4. **Monitor Convergence**: Track optimization progress
5. **Validate Results**: Verify optimized designs meet all requirements

The integration with FreeCAD enables practical implementation of these methods for real structural design problems.