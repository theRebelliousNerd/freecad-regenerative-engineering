# BRUNEL MATHEMATICAL AXIOMS - Structural Engineering Fundamentals

## Core Mathematical Principles

### Equilibrium Laws (Immutable)
Every structure must satisfy three fundamental conditions:

```
ΣFx = 0    (Sum of horizontal forces = 0)
ΣFy = 0    (Sum of vertical forces = 0)  
ΣM = 0     (Sum of moments about any point = 0)
```

**Failure to satisfy = Structural failure**

### Material Truth Laws

#### Stress-Strain Relationships
```
σ = E × ε    (Hooke's Law - within elastic limit)
σmax = P/A   (Direct stress)
σbend = My/I (Bending stress)
τ = VQ/It    (Shear stress)
```

#### Factor of Safety Laws
```
FOS = Ultimate Strength / Working Stress

Minimum acceptable values:
- Known loads, ductile material: FOS ≥ 2.0
- Variable loads: FOS ≥ 3.0  
- Impact/fatigue loads: FOS ≥ 4.0
- Brittle materials: FOS ≥ 5.0
- Human safety critical: FOS ≥ 6.0
```

### Scaling Laws (Cube-Square Rule)
```
Volume ∝ L³     (Material required)
Area ∝ L²       (Strength available)
Weight ∝ L³     (Load imposed)

Critical insight: Strength-to-weight ratio decreases with scale
Material transition thresholds are mathematically deterministic
```

### Load Path Axiom
**Every force must have a complete, continuous path to ground**

```
Applied Load → Primary Member → Connection → Secondary Member → Support → Ground

Any break in this chain = Failure
Each transition point = Potential stress concentration
```

## Structural Constants

### Material Properties (Verified Historical Data)
```
Wrought Iron (Brunel's primary material):
- Ultimate Tensile: 309 N/mm² (20 tons/in²)
- Yield Strength: 247 N/mm² (16 tons/in²) 
- Elastic Modulus: 200 GPa
- Density: 7750 kg/m³
- Poisson's Ratio: 0.27

Modern Steel (A36):
- Yield Strength: 250 MPa
- Ultimate Tensile: 400 MPa
- Elastic Modulus: 200 GPa
- Density: 7850 kg/m³
```

### Stress Concentration Factors (Geometric Constants)
```
Circular hole in infinite plate: Kt = 3.0
Sharp corner (r = 0): Kt → ∞
Fillet transition: Kt = 1.5-2.5 (depending on r/h ratio)
Welded joint: Kt = 1.5-2.0
Bolt hole: Kt = 2.5-3.0
```

### Connection Strength Factors
```
Rivet in shear: τallow = 0.6 × σtensile
Bolt in tension: Reduce by 20% for threads
Weld efficiency: 85-95% of base material
```

## Critical Buckling Formulas

### Euler Buckling (Long Columns)
```
Pcr = π²EI/(KL)²

Where:
K = 0.5 (fixed-fixed)
K = 0.7 (fixed-pinned) 
K = 1.0 (pinned-pinned)
K = 2.0 (fixed-free)

Slenderness ratio: λ = KL/r
Critical λ for steel ≈ 100-120
```

### Plate Buckling
```
σcr = k × π²E/(12(1-ν²)) × (t/b)²

Where k depends on edge conditions:
- Simply supported: k = 4.0
- Fixed edges: k = 6.97
- One edge free: k = 1.28
```

## Dynamic Amplification

### Resonance Avoidance
```
Operating frequency < Natural frequency / 2

For beams: f = (n²/2π) × √(EI/μL⁴)
Where μ = mass per unit length
```

### Impact Factor
```
Dynamic amplification = 1 + √(1 + 2h/δst)
Where h = drop height, δst = static deflection
```

## Temperature Effects

### Thermal Expansion
```
ΔL = L × α × ΔT

Steel: α = 12 × 10⁻⁶ /°C
Aluminum: α = 23 × 10⁻⁶ /°C
Concrete: α = 10 × 10⁻⁶ /°C
```

### Thermal Stress (Constrained expansion)
```
σthermal = E × α × ΔT
```

## Fatigue Laws

### S-N Curve Relationship
```
N = A / σᵐ
Where:
N = cycles to failure
σ = stress amplitude  
A, m = material constants
```

### Stress Concentration in Fatigue
```
Fatigue life reduction factor = Kt²
(Geometric stress concentrations are MORE critical in fatigue)
```

## Deflection Limits

### Serviceability Criteria
```
Beams: δmax < L/250 (general)
Beams: δmax < L/360 (supporting brittle elements)
Cantilevers: δmax < L/180
```

## These axioms are IMMUTABLE
- They represent physical laws, not guidelines
- Violation = Failure (mathematical certainty)
- Safety comes from conservative application, not violation
- All design decisions must satisfy these axioms simultaneously

## Verification Protocol
Every structural analysis MUST verify:
1. Force equilibrium (ΣF = 0, ΣM = 0)
2. Stress limits (σ < σallow/FOS)  
3. Deflection limits (δ < δallow)
4. Buckling stability (P < Pcr)
5. Fatigue life (if applicable)
6. Connection capacity (joints stronger than members)

**Any unverified parameter = Design incomplete**