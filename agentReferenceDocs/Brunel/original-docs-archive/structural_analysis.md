# Structural Analysis Methods - Brunel's Engineering Approach

## Introduction

Brunel's structural analysis methods combined mathematical rigor with practical engineering judgment. His approach emphasized understanding force flow, stress distribution, and failure modes through calculation and testing.

## Fundamental Analysis Principles

### 1. Force Equilibrium
Every structure must satisfy three fundamental conditions:
- **ΣF_x = 0** (Sum of horizontal forces = 0)
- **ΣF_y = 0** (Sum of vertical forces = 0)  
- **ΣM = 0** (Sum of moments about any point = 0)

### 2. Stress-Strain Relationships
For wrought iron (Brunel's primary material):
- **Ultimate Tensile Strength**: 309 N/mm² (20 tons/in²)
- **Permissible Stress (Tension)**: 77 N/mm² (5 tons/in²)
- **Permissible Stress (Compression)**: 62 N/mm² (4 tons/in²)
- **Elastic Modulus**: 200 GPa
- **Factor of Safety**: 4-5 typical

## Structural Analysis Methodology

### Step 1: Load Identification
```
Dead Loads (permanent):
- Self-weight of structure
- Fixed equipment
- Permanent fixtures

Live Loads (variable):
- Traffic loads
- Wind loads
- Snow loads
- Dynamic effects

Environmental Loads:
- Thermal expansion/contraction
- Moisture effects
- Settlement
```

### Step 2: Load Path Analysis
Trace how loads flow through the structure:

```
Applied Load
    ↓
Primary Member (calculate stress)
    ↓
Connection Point (check stress concentration)
    ↓
Secondary Members (distribute load)
    ↓
Support Reactions
    ↓
Foundations
    ↓
Ground
```

### Step 3: Member Analysis

#### Tension Members
```
Stress σ = F/A
where:
  F = Applied force (N)
  A = Cross-sectional area (mm²)

Check: σ_actual < σ_allowable / FOS
```

#### Compression Members
```
Critical Buckling Load (Euler):
P_cr = π²EI / (KL)²

where:
  E = Elastic modulus
  I = Moment of inertia
  K = Effective length factor
  L = Member length

Slenderness Ratio: λ = KL/r
where r = radius of gyration = √(I/A)
```

#### Bending Members
```
Maximum Bending Stress:
σ = My/I

where:
  M = Bending moment
  y = Distance from neutral axis
  I = Second moment of area

Maximum Deflection (simply supported):
δ = 5wL⁴/(384EI)  (uniform load)
δ = PL³/(48EI)     (point load at center)
```

## Case Study: Clifton Suspension Bridge Analysis

### Given Parameters
- Span: 214m (702 ft)
- Width: 9.5m (31 ft)
- Design Load: Traffic + wind
- Material: Wrought iron chains

### Chain Analysis
```
Chain Tension Calculation:
T = wL²/(8h)

where:
  w = distributed load (kN/m)
  L = span (m)
  h = sag (m)

Maximum Tension (at tower):
T_max = T × √(1 + (4h/L)²)

Stress in Chain:
σ = T_max / A_chain

Brunel's Design: σ < 5.5 tons/in² (85 N/mm²)
Actual (with 3 chains): σ = 4.75 tons/in² (73 N/mm²)
```

### Tower Analysis
```
Vertical Load: V = 2T × sin(θ)
Horizontal Load: H = T × cos(θ)
Moment at Base: M = H × height

Check:
- Compression stress in masonry
- Overturning moment
- Sliding resistance
```

## Royal Albert Bridge - Hybrid System Analysis

### Unique Structural System
Combination of arch (compression) and chain (tension):

```
Tube (Compression):
P_tube = W × L/(8f) × (1 + f²/L²)

Chain (Tension):
T_chain = W × L/(8f)

Balance Condition:
P_tube × sin(α) = T_chain × sin(β)
```

### Stress Distribution
```
At midspan:
- Tube: Maximum compression
- Chain: Maximum tension
- Vertical hangers: Direct tension

At quarter points:
- Combined bending and axial stress
- Stress concentration factor: 2.3
- Requires local reinforcement
```

## Box Tunnel - Rock Mechanics

### Stress Around Circular Opening
```
Radial Stress: σ_r = σ_0(1 - a²/r²)
Tangential Stress: σ_θ = σ_0(1 + a²/r²)

where:
  σ_0 = in-situ stress
  a = tunnel radius
  r = distance from center

Maximum stress concentration: 2σ_0 at tunnel wall
```

### Support Requirements
```
Rock Load (Terzaghi):
P = γ × B × (1 - 2c/(γB))

where:
  γ = unit weight of rock
  B = tunnel width
  c = cohesion

Arch thickness required:
t = P × R / σ_allowable
```

## Great Eastern - Hull Stress Analysis

### Double Hull Benefits
```
Moment of Inertia (double hull):
I_double = I_outer + I_inner + A × d²

where d = separation between hulls

Increase in strength: ~300% for 15% weight increase
```

### Longitudinal Bending
```
Hogging Moment (wave crest amidships):
M_hog = W × L² / 24

Sagging Moment (wave trough amidships):
M_sag = W × L² / 12

Maximum Stress:
σ = M × y / I_total
```

### Plate Buckling
```
Critical Buckling Stress:
σ_cr = k × π² × E / (12(1-ν²)) × (t/b)²

where:
  k = buckling coefficient (depends on edge conditions)
  t = plate thickness
  b = plate width
  ν = Poisson's ratio
```

## Modern FEM Validation

### FreeCAD FEM Workflow
1. **Geometry Import**: CAD model from Part/PartDesign
2. **Material Assignment**: E, ν, yield strength
3. **Mesh Generation**: Tetrahedral/hexahedral elements
4. **Boundary Conditions**: Fixed supports, loads
5. **Solution**: CalculiX solver
6. **Post-processing**: Stress plots, deformation, FOS

### Validation Checklist
```python
# Stress Analysis Validation
def validate_stress(fem_results):
    checks = {
        'max_von_mises': fem_results.max_stress < yield_strength/FOS,
        'max_displacement': fem_results.max_disp < allowable_deflection,
        'buckling_factor': fem_results.buckling_factor > 1.5,
        'natural_frequency': fem_results.freq_1 > operating_frequency * 2
    }
    return all(checks.values())
```

## Connection Analysis

### Riveted Connections (Historical)
```
Shear Strength (single rivet):
P_s = π/4 × d² × τ_allowable

Bearing Strength:
P_b = d × t × σ_bearing

Tensile Strength (plate):
P_t = (p - d) × t × σ_tensile

Connection Capacity:
P_allowable = min(P_s, P_b, P_t) × n_rivets
```

### Modern Bolted Connections
```
Bolt Tension:
T = F × e / (n × r)

Combined Stress:
(σ_tensile/σ_t_allow)² + (τ_shear/τ_allow)² ≤ 1
```

## Stress Concentration Factors

### Common Geometries
```
Circular Hole in Plate:      K_t = 3.0
Filleted Shaft:              K_t = 1.5-2.5
Notched Beam:                K_t = 2.0-3.0
Welded Joint:                K_t = 1.5-2.0
```

### Mitigation Strategies
1. **Gradual Transitions**: Avoid sharp corners
2. **Reinforcement**: Add material at high-stress regions
3. **Load Redistribution**: Multiple load paths
4. **Surface Treatment**: Improve fatigue resistance

## Safety Factor Determination

### Brunel's Approach
```
FOS = Ultimate Strength / Working Stress

Typical Values:
- Steady loads, known material: 2.0-3.0
- Variable loads: 3.0-4.0
- Impact loads: 4.0-6.0
- Cast iron (brittle): 4.0-5.0
- Wrought iron (ductile): 3.0-4.0
```

### Modern Standards
```
Load Factors (LRFD):
1.4D + 1.6L  (strength)
1.0D + 1.0L  (serviceability)

where D = dead load, L = live load
```

## Failure Mode Analysis

### Progressive Failure Prevention
1. **Primary Failure**: Identify weakest link
2. **Load Redistribution**: Analyze alternate paths
3. **Secondary Failures**: Check overloaded members
4. **System Collapse**: Determine critical load

### Redundancy Design
```
System Reliability:
R_system = 1 - Π(1 - R_i)  for parallel paths

Minimum redundancy: 
n ≥ log(1 - R_required) / log(1 - R_component)
```

## Practical Calculation Examples

### Example 1: Simple Beam
```
Given: L = 5m, w = 10 kN/m, Steel I-beam
Required: Select beam size

Solution:
M_max = wL²/8 = 10 × 5²/8 = 31.25 kN⋅m
Required S = M/σ_allow = 31250/165 = 189 cm³
Select: IPE 200 (S = 194 cm³)

Check deflection:
δ = 5wL⁴/(384EI) = 5×10×5000⁴/(384×200×10⁶×1943)
δ = 21mm < L/250 = 20mm (marginal - consider larger beam)
```

### Example 2: Column Buckling
```
Given: L = 3m, P = 500 kN, pinned ends
Required: Column size

Solution:
Try 200×200×10 HSS
A = 7600 mm², I = 23.4×10⁶ mm⁴
r = √(I/A) = 55.5 mm
λ = KL/r = 1.0×3000/55.5 = 54

From buckling curves: σ_cr = 180 MPa
P_capacity = 180 × 7600 = 1368 kN > 500 kN ✓
```

## Conclusion

Brunel's structural analysis methods, though developed in the pre-computer era, established principles that remain fundamental:
- Rigorous load path analysis
- Conservative safety factors
- Testing to validate calculations
- Attention to connections and details
- System-level thinking

Modern FEM tools in FreeCAD allow us to validate these classical methods while exploring more complex geometries and loading conditions that Brunel could only approximate.