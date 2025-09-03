# Load Paths and Stress Distribution

## Fundamental Concept

A load path is the route that forces take through a structure from the point of application to the ground or reaction points. Understanding and optimizing load paths is critical for structural integrity and efficiency.

## Load Path Principles

### Primary Rule
**Every force must have a complete, continuous path to ground**

Forces cannot simply disappear - they must be transferred through structural members until they reach a reaction point (ground, foundation, or support).

### Load Path Components
```
1. Load Application Point
   ↓
2. Primary Load-Bearing Members
   ↓
3. Load Transfer Points (Connections)
   ↓
4. Secondary Members
   ↓
5. Support Reactions
   ↓
6. Foundations
   ↓
7. Ground
```

## Types of Load Paths

### Direct Load Path
Forces travel in straight lines through members in pure compression or tension.

```
Example: Column under vertical load
     P
     ↓
   [===]  (compression)
     ↓
   Base
```

**Advantages:**
- Most efficient use of material
- Minimal bending stresses
- Predictable behavior

### Indirect Load Path
Forces must change direction through connections and joints.

```
Example: Portal frame
    P
    ↓
  ┌─┴─┐   (moment connection)
  │   │   (combined bending + axial)
  └───┘
```

**Considerations:**
- Stress concentrations at direction changes
- Bending moments induced
- Requires stronger connections

### Redundant Load Paths
Multiple paths available for load transfer.

```
Example: Truss with redundant members
    P
    ↓
  /│\   Multiple paths:
 / │ \  - Direct through center
/  │  \ - Through diagonal members
───────
```

**Benefits:**
- Increased safety (alternate paths if one fails)
- Load sharing reduces individual member stress
- Progressive collapse prevention

## Stress Distribution Patterns

### Uniform Stress Distribution
Ideal case where stress is constant across a section.

```
σ = P/A (constant across area)

Example: Axially loaded rod
|←─ A ─→|
┌───────┐
│       │ P →
└───────┘
σ = P/A everywhere
```

### Non-Uniform Stress Distribution

#### Bending Stress
```
σ = My/I

Distribution:
  Compression
    ────
    ─┬─
     │  } Neutral axis (σ = 0)
    ─┴─
    ────
   Tension

Maximum at extreme fibers
```

#### Shear Stress in Beams
```
τ = VQ/(It)

Parabolic distribution:
│\     /│
│ \   / │  Maximum at neutral axis
│  \_/  │  Zero at top/bottom
│       │
```

### Stress Concentration

Stress multiplies at geometric discontinuities:

```
Circular Hole:
  ───┬───
     │    K_t = 3.0
  ───○───  σ_max = 3σ_nominal
     │
  ───┴───

Fillet:
  ──┐
    │╲    K_t = 1.5-2.5
  ──┴─    depending on r/d ratio
```

## Load Path Analysis in Complex Structures

### Brunel's Royal Albert Bridge

```
Load Path Diagram:
                Train Load (W)
                     ↓
              [Deck Girder]
                  ↓    ↓
           [Hangers - Tension]
              ↓          ↓
    [Chains - Tension]  [Verticals]
         ↓                   ↓
    [Arch Tube - Compression]
              ↓     ↓
         [Pier]   [Pier]
           ↓         ↓
      [Foundation] [Foundation]
```

**Force Distribution:**
- Deck load: W
- Hanger tension: W/n (n = number of hangers)
- Chain tension: T = WL/(8h)
- Arch compression: C = T/cos(θ)
- Pier vertical: W/2
- Pier horizontal: H = T×cos(θ)

### Great Eastern Hull

```
Wave Load Distribution:

Hogging (wave crest amidships):
     ╱╲
    ╱  ╲     Compression in deck
   ╱    ╲    Tension in keel
  ────────

Sagging (wave trough amidships):
  ────────
   \    /    Tension in deck
    \  /     Compression in keel
     \/
```

**Double Hull Load Sharing:**
- Outer hull: 60% of bending moment
- Inner hull: 30% of bending moment
- Connecting structure: 10% + shear transfer

## Optimizing Load Paths

### Design Strategies

#### 1. Minimize Path Length
Shorter paths = less material, lower deflection

```
Poor:          Better:
  P              P
  │              │
  └──┐          ╱│
     │         ╱ │
     └──┐     ╱  │
        │    ╱   │
        ▼   ▼    ▼
```

#### 2. Align with Principal Stresses
Orient members along stress trajectories

```
Stress Trajectories:
┌─────────────┐
│ ╱ ╱ ╱ ╱ ╱ ╱ │ ← Compression
│╱ ╱ ╱ ╱ ╱ ╱  │
│ ╱ ╱ ╱ ╱ ╱ ╱ │
└─────────────┘
    Optimal member orientation
```

#### 3. Gradual Load Transfer
Avoid sudden changes in stiffness

```
Abrupt:         Gradual:
████│           ████╲
████│           ████ ╲
    │                 ╲
    │                  ╲
Stress spike     Smooth transition
```

## Connection Design for Load Transfer

### Principles
1. **Capacity**: Connection stronger than members
2. **Stiffness**: Compatible with member stiffness
3. **Ductility**: Ability to redistribute loads
4. **Redundancy**: Multiple fasteners/welds

### Load Transfer Mechanisms

#### Bearing
```
   Bolt
    │
 ┌──▼──┐
 │plate│  Force transferred through contact
 └─────┘
```

#### Shear
```
 ───┬───
    │    Bolt in double shear
 ───┼───
    │
 ───┴───
```

#### Friction
```
 ═══╪═══  Pretensioned connection
    ║     Force transferred by friction
 ═══╪═══
```

## Calculating Load Distribution

### Method of Joints (Trusses)
```python
def analyze_joint(forces, angles):
    """
    Equilibrium at each joint:
    ΣFx = 0, ΣFy = 0
    """
    # For each joint
    sum_fx = sum(F * cos(θ) for F, θ in zip(forces, angles))
    sum_fy = sum(F * sin(θ) for F, θ in zip(forces, angles))
    
    assert abs(sum_fx) < tolerance
    assert abs(sum_fy) < tolerance
```

### Method of Sections
```python
def analyze_section(cut_members, loads, distances):
    """
    Cut through structure, analyze equilibrium
    ΣF = 0, ΣM = 0
    """
    # Take moments about convenient point
    moment_sum = sum(F * d for F, d in zip(loads, distances))
    
    # Solve for unknown member forces
    return solve_equilibrium(moment_sum)
```

### Finite Element Approach
```python
# Stiffness method
[K]{u} = {F}

where:
K = Global stiffness matrix
u = Displacement vector
F = Force vector

# Solve for displacements
u = K^(-1) * F

# Calculate stresses
σ = [D][B]{u}
where:
D = Material matrix
B = Strain-displacement matrix
```

## Load Path Verification

### Physical Testing
Brunel's approach to validation:

1. **Component Testing**: Individual members tested to failure
2. **Assembly Testing**: Subassemblies loaded to design + safety factor
3. **Proof Loading**: Complete structure tested at 1.5× design load

Example: Clifton Bridge chains tested to 10 tons/in² (design: 5.5 tons/in²)

### Modern FEM Validation

```python
def verify_load_path(model, applied_loads):
    """
    FreeCAD FEM verification process
    """
    # 1. Apply loads
    fem_model.add_loads(applied_loads)
    
    # 2. Solve
    results = fem_solver.solve()
    
    # 3. Extract stress along load path
    path_stress = []
    for element in load_path_elements:
        stress = results.get_stress(element)
        path_stress.append(stress)
    
    # 4. Verify continuity
    check_force_balance(path_stress)
    
    # 5. Check against allowables
    for stress in path_stress:
        assert stress < allowable_stress
    
    return results
```

## Case Study: Load Path Optimization

### Original Design
```
Problem: Eccentric load causing bending

    P (offset)
    ↓
┌───────┐
│       │  Large bending moment
│   □   │  High stress concentration
│       │
└───────┘
```

### Optimized Design
```
Solution: Add stiffeners to create direct path

    P
    ↓
┌───┬───┐
│   │   │  Stiffener under load
│   │   │  Direct compression path
│   │   │  Minimal bending
└───┴───┘
```

**Results:**
- 60% reduction in maximum stress
- 40% weight reduction
- Improved fatigue life

## Advanced Load Path Concepts

### Shear Lag
In wide flanges, stress distributes non-uniformly:

```
Effective width concept:
|←────── Actual width ──────→|
     |←─ Effective ─→|
     ████████████████  High stress
  ███                ███  Low stress
```

### Load Path in Composite Structures
```
Fiber direction critical:
→→→→→→→  0° (along load) - Strong
↑↑↑↑↑↑↑  90° (perpendicular) - Weak
↗↗↗↗↗↗↗  45° (shear) - Moderate
```

### Thermal Load Paths
```
Thermal expansion creates internal load paths:
         ΔT
    ┌─────────┐
    │ ← → ← → │  Constrained expansion
    └────┬────┘  creates internal stress
         ▼
    Reaction force
```

## FreeCAD Implementation

### Load Path Visualization
```python
# In FreeCAD FEM workbench
def visualize_load_path(fem_results):
    """
    Create vector plot showing force flow
    """
    # Extract principal stress directions
    principal_stresses = fem_results.PrincipalMax
    
    # Create vector field
    vectors = []
    for node in fem_results.Nodes:
        stress_vector = principal_stresses[node]
        vectors.append(stress_vector)
    
    # Display as arrows
    Part.show(vectors, "LoadPath")
```

### Assembly Load Transfer
```python
# Define assembly constraints that transfer loads
assembly = App.ActiveDocument.Assembly

# Coincident constraint - transfers all forces
constraint1 = assembly.add_constraint(
    type="Coincident",
    transfers=["Fx", "Fy", "Fz"]
)

# Parallel constraint - transfers normal force only
constraint2 = assembly.add_constraint(
    type="Parallel", 
    transfers=["Fn"]
)
```

## Best Practices

1. **Always trace complete load paths** - from application to ground
2. **Identify critical paths** - those carrying maximum load
3. **Check stress concentrations** - at every geometry change
4. **Verify load sharing** - in redundant systems
5. **Consider all load cases** - dead, live, environmental
6. **Document assumptions** - for future verification
7. **Validate with testing/FEM** - trust but verify

## Conclusion

Understanding load paths is fundamental to structural design. Brunel's success came from his ability to visualize and optimize these paths, creating efficient structures that have lasted over 150 years. Modern tools like FreeCAD FEM allow us to visualize and validate load paths with precision Brunel could only dream of, but the fundamental principles remain unchanged: forces must flow continuously from application to reaction, and the engineer's job is to provide the most efficient, safe path for that flow.