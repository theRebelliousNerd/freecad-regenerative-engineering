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
