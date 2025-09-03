# Case Studies of Optimized Structures

## Introduction

This document presents detailed case studies of structures that exemplify Khan's optimization principles, demonstrating how systematic approaches to structural design achieve remarkable efficiency gains. Each case study includes design challenges, optimization strategies, and quantified results.

## Case Study 1: John Hancock Center (1969)

### Project Overview
- **Location**: Chicago, Illinois
- **Height**: 344m (100 stories)
- **Structural System**: Trussed Tube
- **Chief Engineer**: Fazlur Rahman Khan

### Design Challenge
Create a mixed-use supertall building combining residential and office space with maximum efficiency in one of the world's windiest cities.

### Optimization Strategy

```python
class HancockOptimization:
    def __init__(self):
        self.height = 344  # meters
        self.floors = 100
        self.wind_speed = 160  # km/h design wind
        
    def trussed_tube_design(self):
        """Optimize trussed tube configuration"""
        
        # Diagonal brace optimization
        brace_angle = 45  # degrees - optimal for load transfer
        brace_intersection_interval = 18  # floors
        
        # Column spacing optimization
        exterior_column_spacing = 3.05  # meters
        
        # Material distribution
        steel_at_base = 280  # kg/m² (lower floors)
        steel_at_top = 95   # kg/m² (upper floors)
        average_steel = 145  # kg/m² (overall)
        
        return {
            'brace_efficiency': 0.65,  # portion of lateral load taken by braces
            'material_savings': '30%',  # vs conventional frame
            'drift_ratio': 'H/500'
        }
```

### Key Innovations

1. **Exposed Diagonal Bracing**: 
   - X-braces visible on facade
   - Eliminates need for internal bracing
   - Creates column-free interiors

2. **Tapered Form**:
   - Base: 50m × 80m
   - Top: 30m × 50m
   - Reduces wind load and overturning moment

3. **Variable Column Sizes**:
   ```python
   def column_sizing(floor_level):
       base_size = 1200  # mm
       reduction_rate = 0.007  # per floor
       column_size = base_size * (1 - reduction_rate * floor_level)
       return max(column_size, 400)  # minimum 400mm
   ```

### Results
- **Material Efficiency**: 145 kg/m² (vs 206 kg/m² for Empire State)
- **Cost Savings**: $15 million (1969 dollars)
- **Construction Time**: 4 years (fast for the era)
- **Usable Space**: 90% floor efficiency

## Case Study 2: Willis Tower (1973)

### Project Overview
- **Location**: Chicago, Illinois
- **Height**: 442m (110 stories)
- **Structural System**: Bundled Tube
- **Chief Engineer**: Fazlur Rahman Khan

### Design Challenge
Design the world's tallest building with maximum rentable area and architectural flexibility.

### Optimization Strategy

```python
class WillisTowerOptimization:
    def __init__(self):
        self.tubes = 9  # number of bundled tubes
        self.tube_dimension = 22.9  # meters (75 feet)
        
    def bundled_tube_configuration(self):
        """Optimize bundled tube arrangement"""
        
        # Tube termination heights for optimal stiffness
        termination_schedule = {
            'tubes_1_2': 50,   # floors
            'tubes_3_4': 66,   # floors
            'tubes_5_6': 90,   # floors
            'tube_7': 108,     # floors
            'tubes_8_9': 110   # floors (full height)
        }
        
        # Shared wall optimization
        shared_wall_thickness = 1.5  # times exterior wall
        material_sharing_benefit = 0.25  # 25% reduction
        
        return {
            'total_tubes': 9,
            'configuration': '3×3 grid',
            'stiffness_gain': '40%',
            'material_efficiency': 161  # kg/m²
        }
```

### Modular Design Benefits

1. **Phased Construction**:
   ```python
   def construction_sequence():
       phases = [
           {'floors': '1-50', 'tubes': 9, 'duration': '12 months'},
           {'floors': '51-66', 'tubes': 9, 'duration': '4 months'},
           {'floors': '67-90', 'tubes': 7, 'duration': '6 months'},
           {'floors': '91-110', 'tubes': 2, 'duration': '4 months'}
       ]
       return phases
   ```

2. **Structural Efficiency**:
   - Shared walls between tubes
   - Load redistribution capability
   - Enhanced torsional resistance

### Results
- **Material Usage**: 161 kg/m²
- **Floor Efficiency**: 75,000 ft² (lower floors), adaptable layouts
- **Wind Drift**: H/500 (within comfort limits)
- **Construction Speed**: 110 floors in 3 years

## Case Study 3: Modern Application - Shanghai Tower (2015)

### Project Overview
- **Height**: 632m (128 stories)
- **Structural System**: Outrigger-braced Mega-frame
- **Design**: Gensler (Architecture), Thornton Tomasetti (Structure)

### Optimization Through Computational Methods

```python
class ShanghaiTowerOptimization:
    def __init__(self):
        self.height = 632
        self.twist_angle = 120  # degrees total twist
        
    def aerodynamic_optimization(self):
        """CFD-based form optimization"""
        
        # Wind load reduction through twisting form
        straight_cylinder_load = 1.0  # baseline
        twisted_form_load = 0.76  # 24% reduction
        
        # Vortex shedding mitigation
        strouhal_number_straight = 0.2
        strouhal_number_twisted = 0.14  # 30% reduction
        
        return {
            'wind_load_reduction': '24%',
            'vortex_reduction': '30%',
            'material_savings': '25,000 tons of steel'
        }
    
    def topology_optimization(self):
        """Optimize structural member distribution"""
        
        # Mega-column optimization
        mega_columns = 8
        super_columns = 4
        
        # Outrigger optimization
        outrigger_locations = [
            0.25 * self.height,  # Zone 2-3 transition
            0.50 * self.height,  # Zone 4-5 transition
            0.75 * self.height   # Zone 6-7 transition
        ]
        
        # Belt truss locations
        belt_truss_floors = [25, 51, 77, 103]
        
        return {
            'lateral_system_weight': '65 kg/m²',
            'gravity_system_weight': '85 kg/m²',
            'total_structural_steel': '150 kg/m²'
        }
```

### Advanced Optimization Techniques

1. **Parametric Wind Analysis**:
   ```python
   def wind_optimization_loop():
       twist_angles = range(0, 180, 10)
       taper_ratios = [0.7, 0.75, 0.8, 0.85]
       
       optimal_config = None
       min_base_moment = float('inf')
       
       for twist in twist_angles:
           for taper in taper_ratios:
               wind_load = cfd_analysis(twist, taper)
               base_moment = calculate_base_moment(wind_load)
               
               if base_moment < min_base_moment:
                   min_base_moment = base_moment
                   optimal_config = (twist, taper)
       
       return optimal_config  # (120°, 0.8)
   ```

2. **Multi-Objective Optimization**:
   - Minimize material usage
   - Maximize usable area
   - Minimize wind loads
   - Optimize constructability

### Results
- **Material Efficiency**: 150 kg/m² (excellent for 632m height)
- **Wind Load Reduction**: 24% through form optimization
- **Energy Savings**: 21% reduction in annual energy
- **Construction Time**: 73 months (rapid for complexity)

## Case Study 4: Topology-Optimized High-Rise Concept

### Conceptual Design Using Modern Computational Methods

```python
class TopologyOptimizedTower:
    def __init__(self):
        self.height = 400  # meters
        self.footprint = (60, 40)  # meters
        
    def run_topology_optimization(self):
        """Full building topology optimization"""
        
        # Define design domain
        domain = create_3d_domain(
            x=60, y=40, z=400,
            mesh_size=2.0  # meters
        )
        
        # Load cases
        loads = {
            'gravity': distributed_load(10, 'kN/m²'),
            'wind_x': lateral_load(wind_profile, 'x'),
            'wind_y': lateral_load(wind_profile, 'y'),
            'seismic': seismic_load(zone=3)
        }
        
        # SIMP optimization
        density_distribution = SIMP_3D(
            domain=domain,
            loads=loads,
            volume_fraction=0.3,
            filter_radius=4.0,
            penalty=3.0
        )
        
        # Extract structural system
        structural_system = interpret_topology(density_distribution)
        
        return structural_system
```

### Optimization Results

```python
def analyze_optimized_design():
    """Compare optimized vs conventional design"""
    
    comparison = {
        'conventional': {
            'material_volume': 45000,  # m³
            'steel_weight': 35000,     # tons
            'max_drift': 'H/400',
            'fundamental_period': 7.2,  # seconds
        },
        'optimized': {
            'material_volume': 31500,  # m³ (30% reduction)
            'steel_weight': 24500,     # tons (30% reduction)
            'max_drift': 'H/500',      # (improved)
            'fundamental_period': 6.8,  # seconds (stiffer)
        }
    }
    
    savings = {
        'material_cost': '$15 million',
        'construction_time': '3 months',
        'embodied_carbon': '8,500 tons CO2'
    }
    
    return comparison, savings
```

### Key Features of Optimized Design

1. **Variable Density Structure**:
   - High density at core and corners
   - Reduced material in low-stress zones
   - Organic load paths

2. **Integrated Systems**:
   - Structure and architecture unified
   - Services integrated into voids
   - Optimal material distribution

## Case Study 5: Parametric Stadium Roof

### Project: Optimized Long-Span Structure

```python
class StadiumRoofOptimization:
    def __init__(self):
        self.span = 200  # meters
        self.width = 150  # meters
        
    def genetic_algorithm_optimization(self):
        """GA optimization for roof structure"""
        
        # Design variables
        variables = {
            'rise_to_span_ratio': (0.05, 0.25),
            'grid_divisions_x': (10, 30),
            'grid_divisions_y': (8, 24),
            'member_depths': (0.5, 3.0),
            'cable_prestress': (100, 1000)  # kN
        }
        
        # Run genetic algorithm
        ga = GeneticAlgorithm(
            population_size=100,
            generations=500,
            crossover_rate=0.8,
            mutation_rate=0.1
        )
        
        optimal_design = ga.optimize(
            objective=minimize_weight,
            constraints=[
                max_deflection < span/300,
                max_stress < 0.9 * yield_stress,
                min_frequency > 1.0  # Hz
            ]
        )
        
        return optimal_design
```

### Results
- **Weight Reduction**: 45% vs initial design
- **Cost Savings**: $12 million
- **Construction Time**: 18 months (6 months saved)
- **Deflection**: L/350 (within limits)

## Comparative Analysis

### Efficiency Metrics Across Case Studies

| Project | Year | Height (m) | System Type | Material (kg/m²) | Innovation |
|---------|------|------------|-------------|------------------|------------|
| John Hancock | 1969 | 344 | Trussed Tube | 145 | Exposed bracing |
| Willis Tower | 1973 | 442 | Bundled Tube | 161 | Modular tubes |
| Shanghai Tower | 2015 | 632 | Mega-frame | 150 | Aerodynamic form |
| Topology Concept | Future | 400 | Optimized | 105 | AI-generated |
| Stadium Roof | Modern | 200 span | Hybrid | 85 | GA-optimized |

## Lessons Learned

### 1. System Selection Impact
- Proper system selection can save 30-50% material
- Height-based typologies provide clear guidance
- Hybrid systems offer best performance for extreme heights

### 2. Computational Power
- Modern optimization finds solutions beyond intuition
- Multi-objective optimization reveals trade-offs
- Parametric models enable rapid iteration

### 3. Integration Benefits
- Architectural-structural integration improves efficiency
- Early optimization has maximum impact
- Holistic design outperforms component optimization

### 4. Validation Importance
- Every optimization must be validated
- Non-linear effects become critical at extremes
- Safety factors must be maintained

## FreeCAD Implementation Examples

### Parametric Tube Structure

```python
import FreeCAD
import Part

def create_tube_structure(height, floors, tube_type='framed'):
    """Generate parametric tube structure in FreeCAD"""
    
    doc = FreeCAD.newDocument("TubeStructure")
    
    # Parameters
    floor_height = height / floors
    bay_width = 4500  # mm
    
    if tube_type == 'framed':
        # Create framed tube
        columns = create_perimeter_columns(bay_width)
        beams = create_spandrel_beams(bay_width, floor_height)
        
    elif tube_type == 'trussed':
        # Add diagonal braces
        columns = create_perimeter_columns(bay_width * 2)
        diagonals = create_diagonal_braces(bay_width * 2, floor_height * 6)
        
    elif tube_type == 'bundled':
        # Create multiple tubes
        tubes = []
        for i in range(3):
            for j in range(3):
                tube = create_single_tube(
                    x_offset=i * 25000,
                    y_offset=j * 25000,
                    height=height * termination_factor(i, j)
                )
                tubes.append(tube)
    
    doc.recompute()
    return doc

# Run optimization
optimal_config = optimize_tube_parameters()
structure = create_tube_structure(**optimal_config)
```

## Conclusions

These case studies demonstrate that:

1. **Systematic optimization yields consistent results**: 30-50% material savings
2. **Innovation compounds**: Each advancement builds on previous knowledge
3. **Computational methods extend possibilities**: Modern tools surpass manual design
4. **Validation ensures safety**: Optimization never compromises structural integrity
5. **Integration maximizes benefits**: Holistic approach outperforms isolated optimization

The principles established by Khan remain valid and are enhanced by modern computational capabilities, enabling even greater efficiency in structural design.