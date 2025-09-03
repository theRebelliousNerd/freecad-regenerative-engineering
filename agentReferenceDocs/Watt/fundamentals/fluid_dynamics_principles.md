# Fluid Dynamics Principles for Thermal Systems

*"Every action of Nature is shortened in the best possible way."* - James Watt

## Executive Summary

Fluid dynamics governs the convective heat transfer that dominates most thermal management systems. Understanding fluid flow enables the design of effective cooling systems with predictable pressure drops, heat transfer rates, and acoustic performance. We don't need full CFD to get 90% accurate results - bulk flow approximations with empirical correlations provide engineering precision.

## Fundamental Flow Principles

### Reynolds Number - The Flow Regime Predictor

```
Re = ρ·V·D/μ = V·D/ν
```

Where:
- ρ = fluid density [kg/m³]
- V = characteristic velocity [m/s]
- D = characteristic length (hydraulic diameter) [m]
- μ = dynamic viscosity [Pa·s]
- ν = kinematic viscosity [m²/s]

**Critical Reynolds Numbers:**
- **Re < 2300**: Laminar flow (predictable, low mixing)
- **2300 < Re < 4000**: Transition (unstable)
- **Re > 4000**: Turbulent flow (enhanced mixing, higher pressure drop)

### Hydraulic Diameter for Non-Circular Ducts
```
D_h = 4·A/P
```
Where A = cross-sectional area, P = wetted perimeter

**Examples:**
- Circular duct: D_h = D
- Square duct (side a): D_h = a
- Rectangular duct (a×b): D_h = 2ab/(a+b)
- Parallel plates (gap h): D_h = 2h

### Pressure Drop Calculations

**Darcy-Weisbach Equation:**
```
ΔP = f·(L/D)·(ρ·V²/2)
```

**Friction Factor Correlations:**
- **Laminar Flow**: f = 64/Re
- **Turbulent Smooth**: f = 0.316/Re^0.25 (Re < 2×10⁵)
- **Turbulent Rough**: Use Moody diagram or Colebrook equation

**Minor Losses (Fittings, Bends, Contractions):**
```
ΔP = K·(ρ·V²/2)
```

**Common K Values:**
- 90° elbow: K = 0.9
- Sudden expansion: K = 1.0
- Sudden contraction: K = 0.5
- Sharp entrance: K = 0.5
- Well-rounded entrance: K = 0.05

## Heat Transfer in Flowing Fluids

### Forced Convection Correlations

**Internal Flow - Circular Tubes:**

*Laminar (Re < 2300):*
```
Nu = 3.66 (constant wall temperature)
Nu = 4.36 (constant heat flux)
```

*Turbulent (Re > 10,000):*
```
Nu = 0.023·Re^0.8·Pr^0.4  (Dittus-Boelter)
Nu = 0.027·Re^0.8·Pr^(1/3)  (Colburn, more accurate)
```

**External Flow - Flow Over Surfaces:**

*Flat Plate (parallel flow):*
```
Nu = 0.664·Re^0.5·Pr^(1/3)  (Laminar)
Nu = 0.037·Re^0.8·Pr^(1/3)  (Turbulent)
```

*Cylinder in Cross-flow:*
```
Nu = 0.62·Re^0.5·Pr^(1/3)  (Re: 40-4000)
Nu = 0.174·Re^0.618·Pr^(1/3)  (Re: 4000-40,000)
```

### Prandtl Number Effects
```
Pr = μ·cp/k = ν/α
```

**Typical Values:**
- **Air**: Pr ≈ 0.7 (momentum and thermal diffusion similar)
- **Water**: Pr ≈ 7 (momentum dominates)
- **Oil**: Pr ≈ 100-1000 (very viscous)
- **Liquid Metals**: Pr ≈ 0.01 (thermal dominates)

## Fan Selection and System Design

### Fan Characteristic Curves

**Fan Laws (Scaling Relationships):**
- Flow rate: Q₂/Q₁ = (N₂/N₁)·(D₂/D₁)³
- Pressure: P₂/P₁ = (N₂/N₁)²·(D₂/D₁)²·(ρ₂/ρ₁)
- Power: W₂/W₁ = (N₂/N₁)³·(D₂/D₁)⁵·(ρ₂/ρ₁)

Where N = rotational speed, D = impeller diameter

### System Curve Derivation

**System Pressure Drop:**
```
P_system = P_static + P_dynamic + P_friction
P_system = ΔP_elevation + Σ(K·ρ·V²/2) + f·(L/D)·(ρ·V²/2)
```

**Parabolic System Curve:**
```
P = K_system·Q²
```

### Fan Operating Point Analysis

1. **Calculate system resistance at design flow rate**
2. **Plot system curve: P = K·Q²**
3. **Find intersection with fan curve**
4. **Verify adequate safety margin (20-30%)**
5. **Check acoustic performance at operating point**

### Fan Selection Criteria

**Pressure Capability:**
- **Low Pressure** (<500 Pa): Axial fans
- **Medium Pressure** (500-2500 Pa): Mixed flow or centrifugal
- **High Pressure** (>2500 Pa): Centrifugal only

**Efficiency Guidelines:**
- **Axial Fans**: 40-60% peak efficiency
- **Centrifugal Fans**: 50-80% peak efficiency
- **EC Motors**: 85-95% efficiency vs 60-80% for AC

## Natural Convection Analysis

### Free Convection Correlations

**Vertical Surfaces (Height L):**
```
Nu = [0.825 + 0.387·Ra^(1/6)/[1+(0.492/Pr)^(9/16)]^(8/27)]²
```

**Horizontal Surfaces:**
*Hot surface facing up (or cold facing down):*
```
Nu = 0.54·Ra^(1/4)  (10⁴ < Ra < 10⁷)
Nu = 0.15·Ra^(1/3)  (10⁷ < Ra < 10¹¹)
```

*Hot surface facing down (or cold facing up):*
```
Nu = 0.27·Ra^(1/4)  (10⁵ < Ra < 10¹⁰)
```

### Rayleigh Number Calculation
```
Ra = g·β·ΔT·L³/(ν·α)
```

**For Air at 20°C:**
- g = 9.81 m/s²
- β ≈ 1/T ≈ 0.0034 K⁻¹
- ν ≈ 15.6×10⁻⁶ m²/s
- α ≈ 22.0×10⁻⁶ m²/s

**Simplified for Air:**
```
Ra ≈ 9.6×10⁶·ΔT·L³
```

## Flow Distribution and Manifold Design

### Parallel Channel Flow Distribution

**Pressure Drop Equality Principle:**
All parallel paths must have equal pressure drop for flow to distribute evenly.

**Flow Rate in Parallel Channels:**
```
Q_total = Σ Q_i
Q_i ∝ 1/√(R_i)  where R_i is resistance of channel i
```

### Manifold Design Guidelines

**Flow Distribution Quality:**
- **Inlet/Outlet Area Ratio**: A_manifold/A_channels > 2.5
- **Velocity Reduction**: V_manifold < 0.5·V_channels
- **Taper Angle**: < 7° for diffusers to avoid separation

**Common Distribution Problems:**
- First channel gets excessive flow
- Last channel gets insufficient flow
- Solution: Tapered manifold or flow restrictors

## Acoustic Considerations

### Fan Noise Prediction

**Sound Power Level:**
```
Lw = 10·log₁₀(W_acoustic/10⁻¹²)
```

**Empirical Fan Noise:**
```
Lw ≈ 10·log₁₀(Q·P) + 40  (dB re 10⁻¹² W)
```

**Noise Reduction Strategies:**
1. **Lower tip speed** (most effective)
2. **Increase blade count** (lower pressure per blade)
3. **Improve inlet conditions** (avoid turbulence)
4. **Add acoustic treatment** (absorptive materials)

### Frequency Content

**Blade Pass Frequency (BPF):**
```
f_BPF = N·RPM/60
```
Where N = number of blades

**Broadband vs Tonal Noise:**
- **Broadband**: Turbulence, boundary layer
- **Tonal**: Blade passing, resonance
- **Control**: Design to avoid structural resonances at BPF

## Fluid Properties and Environmental Effects

### Temperature Effects on Air Properties

**Air Density:**
```
ρ = P/(R·T) = 1.225·(273.15/T)  [kg/m³ at sea level]
```

**Air Viscosity (Sutherland's Law):**
```
μ/μ₀ = (T/T₀)^1.5·(T₀+110)/(T+110)
```

**Altitude Effects:**
- **Density decreases** ≈ 12% per 1000m elevation
- **Cooling capacity decreases** proportionally
- **Fan curve shifts** (lower mass flow rate)

### Humidity Effects

**Psychrometric Properties:**
- **Dry air density at 20°C**: 1.204 kg/m³
- **Saturated air (100% RH)**: ≈ 2% less dense
- **Heat capacity increases** with humidity
- **Condensation risk** at cold surfaces

## Flow Measurement Techniques

### Velocity Measurement Methods

**Pitot Tubes:**
```
V = √(2·ΔP/ρ)
```
- Accurate for point measurements
- Requires straight duct runs (10D upstream, 3D downstream)

**Hot-Wire Anemometers:**
- High frequency response
- Good for turbulence measurement
- Fragile, requires calibration

**Laser Doppler Velocimetry (LDV):**
- Non-intrusive
- High spatial resolution
- Expensive but accurate

### Flow Rate Measurement

**Orifice Plates:**
```
Q = Cd·A₀·√(2·ΔP/ρ)
```
- Simple, inexpensive
- High pressure drop penalty

**Venturi Meters:**
- Lower pressure drop than orifice
- More expensive
- Self-cleaning

**Thermal Mass Flow Meters:**
- Direct mass flow measurement
- Good for low flow rates
- Temperature sensitive

## CFD-Light Methodology

### When to Use Simplified Analysis

**Use Bulk Flow Methods When:**
- Geometry is relatively simple
- Flow is primarily one-dimensional
- Preliminary design phase
- Quick parametric studies needed

**Use CFD When:**
- Complex three-dimensional flow
- Separation or recirculation expected
- Detailed temperature distribution needed
- Optimization of specific geometries

### Hand Calculation Validation

**Energy Balance Check:**
```
Q_convection = m_dot·cp·ΔT = h·A·LMTD
```
Where LMTD = Log Mean Temperature Difference

**Momentum Balance Check:**
```
ΔP_total = ΔP_friction + ΔP_acceleration + ΔP_elevation
```

**Mass Balance Check:**
```
ρ₁·V₁·A₁ = ρ₂·V₂·A₂  (continuity equation)
```

## Practical Design Examples

### Example 1: CPU Cooler Design

**Given:**
- Heat load: 95W
- Ambient: 25°C
- Target junction: <85°C
- Available space: 120mm × 120mm × 160mm

**Solution Approach:**
1. Calculate thermal budget: ΔT_total = 85-25 = 60°C
2. Estimate thermal resistances:
   - R_jc: 0.5 K/W (given)
   - R_ci: 0.1 K/W (good TIM)
   - R_ca: (60-95×0.6)/95 = 0.57 K/W (required)
3. Heat sink design for R_ca = 0.57 K/W
4. Natural convection check: Insufficient
5. Fan selection for forced convection

### Example 2: Ducted Cooling System

**Given:**
- Airflow requirement: 0.1 m³/s
- Duct length: 5m
- Duct diameter: 150mm
- 4 × 90° elbows

**Pressure Drop Calculation:**
1. Velocity: V = Q/A = 0.1/(π×0.075²) = 5.66 m/s
2. Reynolds number: Re = 5.66×0.15/15.6×10⁻⁶ = 54,400
3. Friction factor: f = 0.316/54,400^0.25 = 0.020
4. Friction loss: ΔP_f = 0.020×(5/0.15)×(1.204×5.66²/2) = 390 Pa
5. Minor losses: ΔP_m = 4×0.9×(1.204×5.66²/2) = 348 Pa
6. Total: ΔP_total = 390 + 348 = 738 Pa

## Quality Assurance for Fluid Systems

### Design Verification Checklist

1. **Flow Rate Verification**
   - [ ] Required cooling capacity calculated
   - [ ] System flow rate determined
   - [ ] Fan curve intersection verified

2. **Pressure Drop Analysis**
   - [ ] All major and minor losses calculated
   - [ ] System curve constructed
   - [ ] Operating point identified with margin

3. **Heat Transfer Validation**
   - [ ] Reynolds number calculated
   - [ ] Appropriate Nu correlation selected
   - [ ] Heat transfer coefficient verified

4. **Acoustic Assessment**
   - [ ] Fan noise level estimated
   - [ ] Blade pass frequency calculated
   - [ ] Resonance potential evaluated

Remember: "The same amount of motion in the working fluid should produce the maximum useful effect." This principle guides all thermal-fluid design decisions toward optimal efficiency and effectiveness.

Every fluid system must balance flow rate, pressure drop, heat transfer, and acoustic performance. Understanding these trade-offs enables systematic design with predictable results.