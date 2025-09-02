# Structural Typologies and Design Grammars

## The Concept of Structural Grammar

Fazlur Rahman Khan revolutionized structural engineering by creating a systematic "grammar" of structural solutions - a hierarchical classification system that maps building height to optimal structural systems. This approach transforms structural design from art to science, providing clear guidelines for system selection based on quantifiable criteria.

## Khan's Hierarchical Typology System

### Height-Based Classification

Khan established clear height ranges for different structural systems:

| Height Range | Steel Systems | Concrete Systems |
|-------------|---------------|------------------|
| 0-20 floors | Rigid Frame | Rigid Frame |
| 20-40 floors | Frame + Shear Truss | Frame + Shear Wall |
| 40-60 floors | Framed Tube | Framed Tube |
| 60-80 floors | Trussed Tube | Tube-in-Tube |
| 80-100 floors | Bundled Tube | Modular Tube |
| 100+ floors | Mixed Systems | Mixed Systems |

## Primary Tube Typologies

### 1. Framed Tube System

**Definition**: A three-dimensional space structure with closely spaced exterior columns connected by deep spandrel beams, forming a rigid box.

**Characteristics:**
- Column spacing: 1.5-4.5m (typically 3m)
- Spandrel beam depth: 600-1200mm
- Column dimensions: 400-800mm
- Efficiency range: 38-300m height

**Structural Behavior:**
```python
# Framed tube stiffness calculation
lateral_stiffness = (E * I_tube) / H^3
where:
    E = modulus of elasticity
    I_tube = moment of inertia of entire tube
    H = building height
```

**Design Grammar Rules:**
1. IF height < 150m AND aspect_ratio < 6 THEN use_framed_tube
2. Column spacing = min(4.5m, floor_to_floor_height × 1.2)
3. Spandrel depth = max(600mm, span/10)

**Optimization Parameters:**
- Minimize: Column spacing (for maximum tube action)
- Maximize: Spandrel beam depth (within architectural limits)
- Balance: Window area vs structural efficiency

### 2. Trussed Tube (Braced Tube) System

**Definition**: A framed tube with diagonal braces added to the exterior, creating a truss action that handles lateral loads through axial forces rather than bending.

**Characteristics:**
- Diagonal angle: 35-55° (typically 45°)
- Brace intersections: Every 6-12 floors
- Column spacing: 4.5-9m (wider than framed tube)
- Efficiency range: 150-400m height

**Structural Behavior:**
```python
# Trussed tube efficiency
axial_efficiency = lateral_load / (brace_area × stress_limit)
bending_reduction = 1 - (axial_component / total_load)
```

**Design Grammar Rules:**
1. IF height > 150m AND wind_load > threshold THEN add_diagonal_braces
2. Brace angle = atan(floor_height × n_floors / bay_width)
3. Brace size ∝ accumulated_shear_force

**Notable Examples:**
- John Hancock Center, Chicago (344m, 100 floors)
- Bank of China Tower, Hong Kong (367m, 70 floors)

### 3. Tube-in-Tube System

**Definition**: Dual tube system with an outer framed tube and inner core tube working together to resist lateral loads.

**Characteristics:**
- Outer tube: Framed or trussed configuration
- Inner core: 20-30% of floor plate
- Interaction: Through rigid floor diaphragms
- Efficiency range: 200-450m height

**Load Distribution:**
```python
# Load sharing between tubes
outer_tube_share = 0.6 - 0.8 × total_lateral_load
inner_core_share = 0.2 - 0.4 × total_lateral_load
coupling_effect = floor_stiffness × relative_displacement
```

**Design Grammar Rules:**
1. Core dimensions = √(0.2 to 0.3 × floor_area)
2. Outriggers at mechanical floors (every 30-40 floors)
3. Core wall thickness = H/1000 to H/500

### 4. Bundled Tube System

**Definition**: Multiple tubes connected to work as a single unit, allowing for varied building geometry and improved efficiency.

**Characteristics:**
- Individual tube cells: 10-15m width
- Shared walls between tubes
- Modular construction approach
- Efficiency range: 300-500m+ height

**Structural Innovation:**
```python
# Bundled tube modularity
total_stiffness = Σ(individual_tube_stiffness) × interaction_factor
where interaction_factor = 1.2 - 1.5 (due to shared walls)
```

**Design Grammar Rules:**
1. IF height > 300m THEN consider_bundled_configuration
2. Tube modules terminate at different heights for architectural effect
3. Shared walls = 1.5 × exterior wall thickness

**Notable Example:**
- Willis Tower (formerly Sears Tower): 442m, 110 floors
- 9 bundled tubes terminating at different heights

## Advanced Hybrid Systems

### 5. Outrigger Systems

**Integration with Tube Systems:**
- Location: Every 30-40 floors
- Connection: Core to perimeter columns
- Effect: 25-40% drift reduction

**Optimization Strategy:**
```python
optimal_outrigger_location = 0.4 to 0.6 × building_height
number_of_outriggers = floor(height / 120m)
```

### 6. Mega-Frame Systems

**Modern Evolution:**
- Mega-columns at corners
- Multi-story trusses
- Open architecture possibilities

## Transition Rules Between Typologies

### Decision Framework

```python
def select_structural_system(height, aspect_ratio, wind_load, seismic_zone):
    if height < 100m:
        if aspect_ratio < 4:
            return "Rigid Frame"
        else:
            return "Frame + Shear Wall"
    
    elif height < 200m:
        if wind_load < moderate:
            return "Framed Tube"
        else:
            return "Trussed Tube"
    
    elif height < 300m:
        if seismic_zone > 3:
            return "Tube-in-Tube + Outriggers"
        else:
            return "Trussed Tube"
    
    else:  # height > 300m
        return "Bundled Tube or Mega-Frame"
```

## Typology Performance Metrics

### Comparative Analysis

| System Type | Material (kg/m²) | Drift (H/x) | Natural Period | Cost Index |
|-------------|------------------|-------------|----------------|------------|
| Rigid Frame | 250-350 | H/300 | 0.1n | 1.0 |
| Framed Tube | 145-200 | H/400 | 0.08n | 0.85 |
| Trussed Tube | 120-160 | H/500 | 0.07n | 0.90 |
| Tube-in-Tube | 130-170 | H/450 | 0.075n | 0.95 |
| Bundled Tube | 110-150 | H/500 | 0.065n | 1.05 |

*where n = number of stories

## Grammar Application Rules

### Rule-Based Design Process

1. **Height Classification**
   ```
   IF height < 100m THEN Category_1
   ELSE IF height < 200m THEN Category_2
   ELSE IF height < 300m THEN Category_3
   ELSE Category_4
   ```

2. **Load Condition Assessment**
   ```
   wind_criticality = wind_load / gravity_load
   IF wind_criticality > 0.25 THEN enhance_lateral_system
   ```

3. **Aspect Ratio Consideration**
   ```
   IF aspect_ratio > 7 THEN require_enhanced_system
   IF aspect_ratio > 9 THEN require_auxiliary_damping
   ```

4. **System Selection Logic**
   ```
   system = base_typology(height)
   system = modify_for_loads(system, wind, seismic)
   system = adjust_for_geometry(system, aspect_ratio)
   system = optimize_for_context(system, cost, schedule)
   ```

## Parametric Generation Rules

### Automated Typology Generation

```python
class StructuralTypology:
    def __init__(self, height, footprint):
        self.height = height
        self.footprint = footprint
        self.system = self.select_system()
    
    def select_system(self):
        # Grammar rules encoded
        if self.height < 100:
            return RigidFrame()
        elif self.height < 200:
            return FramedTube()
        elif self.height < 300:
            return TrussedTube()
        else:
            return BundledTube()
    
    def optimize_parameters(self):
        # Parametric optimization within typology
        self.system.column_spacing = optimize_spacing()
        self.system.beam_depth = optimize_depth()
        self.system.material = optimize_material()
```

## FreeCAD Implementation Strategy

### Creating Typology Libraries

1. **Parametric Templates**
   - Create base geometry for each typology
   - Expose key parameters (height, bay width, core size)
   - Link parameters to spreadsheet for optimization

2. **Automated Selection**
   ```python
   # FreeCAD Python script
   def generate_structural_system(building_height, footprint):
       typology = select_typology(building_height)
       model = create_parametric_model(typology, footprint)
       optimize_parameters(model)
       return model
   ```

3. **Performance Validation**
   - Link to FEM workbench
   - Automated mesh generation
   - Load case application
   - Results extraction and comparison

## Typology Evolution Path

### Progressive Enhancement Strategy

1. **Start Simple**: Begin with basic framed tube
2. **Add Complexity**: Introduce bracing if needed
3. **Enhance Performance**: Add outriggers or belt trusses
4. **Optimize Globally**: Consider bundled or hybrid systems

### Transition Thresholds

- Add shear walls when drift > H/400
- Add diagonal bracing when height > 40 stories
- Add outriggers when height > 60 stories
- Consider bundled tube when height > 80 stories

## Summary

Khan's structural typologies provide a comprehensive grammar for tall building design, offering:

1. **Clear Classification**: Height-based system selection
2. **Predictable Performance**: Known efficiency ranges
3. **Systematic Optimization**: Parameters within each typology
4. **Evolution Path**: Natural progression with increasing height
5. **Design Confidence**: Proven systems with known behavior

This grammar transforms the complex problem of structural system selection into a systematic, rule-based process that can be automated and optimized computationally.