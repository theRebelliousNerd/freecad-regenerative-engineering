# Heat Transfer Fundamentals and Analysis Methods
## Comprehensive Thermal Design Framework for FreeCAD Applications

*"Heat always finds a path - we must control it."* - Marie Curie's Thermal Design Principle

## Fundamental Heat Transfer Mechanisms

### 1. Heat Conduction (Fourier's Law)

**One-Dimensional Steady State**:
```
q = -k·A·(dT/dx)
```
Where:
- q = heat transfer rate (W)  
- k = thermal conductivity (W/m·K)
- A = cross-sectional area (m²)
- dT/dx = temperature gradient (K/m)

**Multi-Dimensional Steady State**:
```
∇·(k∇T) + Q = 0
```
Where Q = internal heat generation (W/m³)

**Transient Heat Conduction Equation**:
```
ρ·Cp·(∂T/∂t) = ∇·(k∇T) + Q
```

### 2. Convective Heat Transfer (Newton's Law of Cooling)

**Basic Convection Equation**:
```
q = h·A·(Ts - T∞)
```
Where:
- h = convective heat transfer coefficient (W/m²·K)
- Ts = surface temperature (K)
- T∞ = bulk fluid temperature (K)

**Natural Convection Correlations**:

*Vertical Plate* (10⁴ < Ra < 10⁹):
```
Nu = 0.59·Ra^(1/4)    for Ra < 10⁹
Nu = 0.1·Ra^(1/3)     for Ra > 10⁹
```

*Horizontal Cylinder* (Ra < 10¹²):
```
Nu = {0.6 + [0.387·Ra^(1/6)]/[1 + (0.559/Pr)^(9/16)]^(8/27)}²
```

**Forced Convection Correlations**:

*Flow over Flat Plate*:
```
Laminar: Nu = 0.332·Re^(1/2)·Pr^(1/3)  (Re < 5×10⁵)
Turbulent: Nu = 0.0296·Re^(4/5)·Pr^(1/3) (Re > 5×10⁵)
```

*Flow in Circular Pipes*:
```
Laminar: Nu = 3.66  (constant wall temperature)
Turbulent: Nu = 0.023·Re^(0.8)·Pr^n  (n=0.4 heating, n=0.3 cooling)
```

### 3. Thermal Radiation (Stefan-Boltzmann Law)

**Between Two Surfaces**:
```
q₁₂ = A₁·F₁₂·σ·(T₁⁴ - T₂⁴)
```

**Linearized Radiation**:
```
hr = 4·ε·σ·T̄³
```
Where T̄ is average absolute temperature

**Combined Convection-Radiation**:
```
htotal = hconv + hrad
```

## Thermal Network Analysis

### Thermal Resistance Concepts

**Conduction Resistance**:
```
Rth,cond = L/(k·A)
```

**Convection Resistance**:  
```
Rth,conv = 1/(h·A)
```

**Radiation Resistance**:
```
Rth,rad = 1/(hr·A)
```

**Contact Resistance** (critical for interfaces):
```
Rth,contact = Rc/A    [K·cm²/W → K/W]
```

### Series-Parallel Networks

**Series Resistances**:
```
Rtotal = R₁ + R₂ + R₃ + ... + Rₙ
```

**Parallel Resistances**:
```
1/Rtotal = 1/R₁ + 1/R₂ + 1/R₃ + ... + 1/Rₙ
```

**Temperature Drop Calculation**:
```
ΔT = q·Rth
```

## Heat Sink Design and Analysis

### Natural Convection Heat Sink Design

**Optimal Fin Spacing** (vertical orientation):
```
S_opt = 2.714·(L/Ra_L)^(1/4)
```
Where:
- S = fin spacing (m)
- L = fin height (m)
- Ra_L = Rayleigh number based on fin height

**Fin Efficiency**:
```
ηf = tanh(mL)/(mL)
```
Where m = √(2h/(k·t)) for rectangular fins

**Overall Surface Efficiency**:
```
ηo = 1 - (Af/A)·(1 - ηf)
```

### Heat Sink Performance Calculation

**Thermal Resistance of Heat Sink**:
```
Rth,hs = 1/(ηo·h·A)
```

**Junction-to-Ambient Resistance**:
```
Rth,ja = Rth,jc + Rth,contact + Rth,hs
```

**Maximum Power Dissipation**:
```
Pmax = (Tj,max - Ta)/(Rth,ja)
```

## Thermal Interface Materials (TIM) Analysis

### TIM Selection Criteria Matrix

| Power Density | Recommended TIM | Thermal Resistance | Comments |
|---------------|-----------------|-------------------|----------|
| < 1 W/cm² | Thermal paste | 0.1-0.5 K·cm²/W | Cost-effective |
| 1-5 W/cm² | High-performance paste | 0.05-0.2 K·cm²/W | Good compliance |
| 5-20 W/cm² | Phase change materials | 0.02-0.1 K·cm²/W | Self-leveling |
| > 20 W/cm² | Liquid metal | 0.01-0.03 K·cm²/W | Requires expertise |

### TIM Thickness Optimization

**Optimal Thickness**:
```
t_opt = √(Rc·k_TIM)
```
Where Rc is contact resistance without TIM

**Total Thermal Resistance**:
```
Rth,total = Rc1 + t/(k_TIM·A) + Rc2
```

## Transient Thermal Analysis

### Lumped Capacitance Method

**Validity Criterion** (Bi < 0.1):
```
Bi = h·Lc/k < 0.1
```
Where Lc = V/As (characteristic length)

**Temperature Response**:
```
T(t) = T∞ + (Ti - T∞)·exp(-t/τ)
```
Where τ = ρ·Cp·V/(h·A) (time constant)

### Semi-Infinite Solid Solution

**Surface Temperature Response**:
```
T(0,t) = Ti + (2·qs/k)·√(αt/π)
```
For constant surface heat flux qs

### Thermal Diffusivity and Time Constants

**Thermal Diffusivity**:
```
α = k/(ρ·Cp)    [m²/s]
```

**Characteristic Time**:
```
τ = L²/α
```

**Fourier Number**:
```
Fo = α·t/L²
```

## Multi-Physics Thermal Coupling

### Thermoelectric Effects

**Seebeck Effect** (thermocouples):
```
V = α·ΔT
```

**Peltier Effect** (thermoelectric coolers):
```
qp = α·I·T
```

**Thomson Effect**:
```
qt = β·I·(dT/dx)
```

### Thermal-Structural Coupling

**Thermal Stress** (constrained expansion):
```
σ = E·α·ΔT
```

**Thermal Strain** (free expansion):
```
ε = α·ΔT
```

**Bi-material Strip Curvature**:
```
κ = 6·(α₁ - α₂)·ΔT·t₁·t₂/(t₁ + t₂)²
```

## Validation and Uncertainty Analysis

### Experimental Validation Metrics

**Thermal Resistance Measurement**:
```
Rth,measured = ΔT_measured/Q_input
```

**Uncertainty Propagation**:
```
δRth/Rth = √[(δΔT/ΔT)² + (δQ/Q)²]
```

### Model Validation Hierarchy

1. **Analytical Solutions**: Exact solutions for simple geometries
2. **Semi-Empirical Correlations**: Validated correlations for common cases  
3. **Numerical Methods**: FEA/CFD for complex geometries
4. **Experimental Validation**: Physical testing for critical applications

### Safety Factors and Margins

**Thermal Design Guidelines**:
- **Electronics**: 20-30% thermal margin below max operating temperature
- **Power Electronics**: 15-25% margin with derating curves
- **LEDs**: Junction temperature <80% of maximum rating
- **Batteries**: Thermal runaway prevention margins

### Common Thermal Design Errors

1. **Ignoring Contact Resistance**: Often 20-50% of total thermal resistance
2. **Assuming Uniform Heat Generation**: Hot spots require local analysis
3. **Neglecting Radiation at High Temperatures**: Significant above 80-100°C
4. **Poor TIM Application**: Air gaps devastate performance
5. **Inadequate Transient Analysis**: Startup and shutdown thermal stress

## Practical Design Guidelines

### Heat Sink Selection Process

1. **Calculate Heat Dissipation**: Include all loss mechanisms
2. **Determine Allowable Temperature Rise**: Based on component limits
3. **Calculate Required Thermal Resistance**: Rth = ΔT/Q
4. **Select Heat Sink Geometry**: Natural vs. forced convection
5. **Optimize Fin Spacing**: Use correlations or CFD analysis
6. **Validate with Thermal Modeling**: FEA verification
7. **Prototype Testing**: Measure actual performance

### Thermal Management Strategy Hierarchy

1. **Minimize Heat Generation**: Efficient components, reduced losses
2. **Optimize Heat Paths**: Low-resistance conduction paths
3. **Maximize Heat Removal**: Effective convection/radiation
4. **Thermal Energy Storage**: Thermal mass for transients
5. **Active Cooling**: Fans, liquid cooling as needed

This framework provides the mathematical foundation and practical guidance for all thermal analysis within the Curie agent's domain, ensuring quantitative accuracy and engineering reliability.