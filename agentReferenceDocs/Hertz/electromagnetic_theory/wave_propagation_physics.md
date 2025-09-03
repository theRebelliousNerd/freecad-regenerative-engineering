# Wave Propagation Physics: From Near-Field to Far-Field

## Executive Summary
This module provides comprehensive analysis of electromagnetic wave propagation mechanisms, from the reactive near-field through the radiating near-field to far-field radiation. Understanding these regions is critical for antenna design, SAR compliance, and system integration.

**Propagation Principle**: "Electromagnetic waves carry both energy and information. Master their propagation characteristics, and you control their destiny."

---

## Wave Propagation Regions

### Near-Field Boundaries
The electromagnetic field around any antenna divides into distinct regions:

**Reactive Near-Field** (r < λ/2π):
- **Dominant mechanism**: Energy storage (reactive power)
- **Field behavior**: |E| ∝ 1/r², |H| ∝ 1/r³
- **Wave impedance**: Z_w = E/H varies dramatically with distance
- **Phase relationship**: E and H not in phase quadrature
- **Engineering significance**: Dominates antenna impedance, coupling, SAR

**Radiating Near-Field** (λ/2π < r < 2D²/λ):
- **Dominant mechanism**: Wave formation (Fresnel region)
- **Field behavior**: |E| ∝ 1/r, complex angular dependence
- **Wave impedance**: Approaches η₀ = 377Ω asymptotically
- **Phase relationship**: Transitioning toward quadrature
- **Engineering significance**: Pattern formation, measurement proximity

**Far-Field** (r > 2D²/λ):
- **Dominant mechanism**: Radiated power (Fraunhofer region)
- **Field behavior**: |E| ∝ 1/r, angular pattern independent of distance
- **Wave impedance**: Z_w = η₀ = 377Ω (plane wave)
- **Phase relationship**: E and H in phase quadrature, both transverse
- **Engineering significance**: Antenna pattern characterization

### Critical Distance Calculation
**Formula**: r_ff = 2D²/λ

**Design Examples**:
- **Mobile phone antenna** (D = 10cm @ 2GHz): r_ff = 2.7cm
- **WiFi router antenna** (D = 15cm @ 2.4GHz): r_ff = 3.6cm  
- **Parabolic dish** (D = 1m @ 10GHz): r_ff = 66.7m

**Safety Implication**: Human exposure occurs primarily in near-field for portable devices.

---

## Free Space Propagation

### Friis Transmission Equation
**Link Budget Formula**:
```
P_r/P_t = (G_t × G_r × λ²)/((4π)² × R²)
```

**Logarithmic Form** (dB):
```
P_r = P_t + G_t + G_r - FSPL
```

Where FSPL = 20log₁₀(4πR/λ) = 32.45 + 20log₁₀(f_MHz) + 20log₁₀(R_km)

### Path Loss Mechanisms

#### Free Space Path Loss (FSPL)
- **Physical basis**: Spherical wave spreading
- **Formula**: FSPL = (4πR/λ)² (linear), 20log₁₀(4πR/λ) (dB)
- **Frequency dependence**: Increases as f² (6dB per octave)
- **Distance dependence**: Increases as R² (6dB per distance doubling)

**Engineering Insight**: FSPL represents geometric dilution of power density, not absorption.

#### Atmospheric Absorption
**Oxygen absorption**: 
- **Peak**: ~60 GHz (O₂ molecular resonance)
- **Attenuation**: 10-15 dB/km at peak
- **Bandwidth**: Several GHz wide

**Water vapor absorption**:
- **Peaks**: 22.2 GHz, 183 GHz, 325 GHz
- **Attenuation**: 0.1-0.5 dB/km (variable with humidity)
- **Weather dependence**: Rain significantly increases attenuation

**Rain attenuation**:
- **Mechanism**: Scattering and absorption by droplets
- **Formula**: γ = aR^b (dB/km) where R = rainfall rate (mm/hr)
- **Frequency scaling**: Increases dramatically above 10 GHz

---

## Multipath Propagation

### Reflection Mechanisms

#### Specular Reflection
**Condition**: Smooth surface with roughness h < λ/(8cos θ)
**Reflection coefficient**: 
```
Γ = (cos θ - √(εᵣ - sin² θ))/(cos θ + √(εᵣ - sin² θ))  [vertical polarization]
```

#### Ground Reflection
**Two-ray model**: Direct path + ground reflected path
**Path difference**: Δ = (h_t × h_r × 4π)/(λR) for R >> h_t, h_r
**Interference pattern**: Constructive/destructive based on path difference

### Diffraction Effects

#### Fresnel Zones
**First Fresnel zone radius**: r₁ = √(λR₁R₂/(R₁+R₂))
**Clearance criterion**: 60% of first Fresnel zone must be clear
**Diffraction loss**: Significant when obstacles block > 40% of first zone

#### Knife-edge Diffraction
**Fresnel parameter**: ν = h√(2(d₁+d₂)/(λd₁d₂))
**Diffraction loss**: L = -20log₁₀|F(ν)| where F(ν) is Fresnel integral

### Scattering Phenomena

#### Rayleigh Scattering
**Condition**: Particle size << λ
**Cross-section**: σ ∝ 1/λ⁴
**Examples**: Atmospheric particles, small rain drops

#### Mie Scattering  
**Condition**: Particle size ≈ λ
**Cross-section**: Complex function of size parameter
**Examples**: Rain drops at millimeter waves

---

## Propagation in Materials

### Dielectric Materials
**Wave equation**: ∇²E = γ²E where γ² = ω²με*
**Complex permittivity**: ε* = ε₀εᵣ(1 - j tan δ)
**Propagation constant**: γ = α + jβ = jω√(μ₀ε*)

**Key parameters**:
- **Phase velocity**: v_p = ω/β = c/√(εᵣ)
- **Attenuation constant**: α ≈ (ω tan δ)/(2c) √εᵣ (low loss)
- **Wave impedance**: η = η₀√(μᵣ/εᵣ)

### Conducting Materials
**Skin effect**: Current density J(z) = J₀e^(-z/δ)
**Skin depth**: δ = √(2/(ωμσ)) = √(2ρ/(ωμ))

**Material examples** at 1 GHz:
- **Copper**: δ = 2.1 μm, Rs = 8.3 mΩ/square
- **Aluminum**: δ = 2.7 μm, Rs = 10.5 mΩ/square  
- **Silver**: δ = 1.9 μm, Rs = 7.9 mΩ/square

### Plasma Media
**Plasma frequency**: ωₚ = √(Ne²/(ε₀m))
**Refractive index**: n = √(1 - ωₚ²/ω²)
**Cutoff condition**: No propagation when ω < ωₚ

**Ionosphere effects**:
- **HF reflection**: Total internal reflection below critical frequency
- **Group delay**: Dispersive propagation affects GPS accuracy
- **Faraday rotation**: Polarization rotation in magnetic field

---

## Antenna Near-Field Physics

### Reactive Near-Field Characteristics
**Electric energy density**: u_E = ½ε₀|E|²
**Magnetic energy density**: u_H = ½μ₀|H|²  
**Energy balance**: u_E ≠ u_H (energy storage dominates)

**Field impedance**: Z_wave = E/H varies as:
- **Electric dipole**: Z_wave > η₀ (capacitive)
- **Magnetic dipole**: Z_wave < η₀ (inductive)
- **Balanced antenna**: Z_wave → η₀ as r increases

### Radiating Near-Field Formation
**Fresnel phase**: Spherical wavefronts with radius-dependent phase
**Angular pattern evolution**: Pattern shape changes with distance
**Transition behavior**: Smooth asymptotic approach to far-field pattern

### SAR and Near-Field Exposure
**Specific Absorption Rate**: SAR = σ|E|²/(2ρ) (W/kg)
**Peak SAR location**: Typically 1-2 mm into tissue
**Averaging volume**: 10g (IEEE) or 1g (IEC) tissue mass
**Compliance testing**: Requires detailed near-field calculation

---

## Polarization Effects

### Polarization States
**Linear polarization**: E-field oscillates in fixed plane
- **Vertical (V)**: E parallel to vertical reference
- **Horizontal (H)**: E perpendicular to vertical reference
- **Slant**: E at arbitrary angle α to reference

**Circular polarization**: E-field rotates at wave frequency
- **Right-hand (RHCP)**: Clockwise rotation (viewed toward source)
- **Left-hand (LHCP)**: Counter-clockwise rotation
- **Axial ratio**: AR = E_major/E_minor (1 for perfect circular)

**Elliptical polarization**: General case with arbitrary axial ratio

### Polarization Mismatch
**Power coupling factor**: ρ = |e_t · e_r*|²
Where e_t, e_r are unit polarization vectors

**Common mismatches**:
- **Co-polar/cross-polar**: 0 dB / -∞ dB (ideal)
- **Linear orthogonal**: -∞ dB coupling
- **Circular opposite**: -∞ dB coupling
- **Circular/linear**: -3 dB coupling (random orientation)

### Faraday Rotation
**Rotation angle**: Θ = (K × B · dl)/f² 
**Ionosphere effects**: Several degrees at VHF
**Compensation methods**: Diversity reception, circular polarization

---

## Environmental Propagation Effects

### Vegetation Effects
**Attenuation mechanisms**: 
- **Absorption**: Water content in leaves/branches
- **Scattering**: Multiple scattering from leaves
- **Seasonal variation**: 3-10 dB difference (leaves vs bare)

**Models**:
- **ITU-R P.833**: Statistical vegetation model
- **COST 235**: European vegetation database
- **Modified exponential**: γ = A × f^B × d^C

### Building Effects  
**Penetration loss**: Varies with construction materials
- **Wood frame**: 4-8 dB at 2.4 GHz
- **Concrete/brick**: 10-15 dB at 2.4 GHz  
- **Metal frame**: 20-30 dB at 2.4 GHz
- **Low-E glass**: 25-35 dB (metallic coating)

**Internal propagation**: 
- **Floor loss**: 10-20 dB per floor
- **Wall loss**: 3-8 dB per interior wall
- **Corridor effects**: Waveguiding can enhance propagation

### Urban Propagation
**Propagation mechanisms**:
- **Line-of-sight**: Direct path (best case)
- **Reflection**: Building surfaces, ground
- **Diffraction**: Building edges, terrain
- **Scattering**: Rough surfaces, vehicles

**Empirical models**:
- **Okumura-Hata**: Macrocell suburban/urban
- **COST 231-Hata**: Extension to 2 GHz
- **Lee model**: Simplified path loss prediction
- **Walfisch-Ikegami**: Street canyon model

---

## Link Budget Analysis

### System Link Budget
**Power budget equation**:
```
P_r = P_t + G_t - L_t + G_r - L_r - L_path - L_misc - M_fade
```

**Parameters**:
- **P_t**: Transmit power (dBm)
- **G_t, G_r**: Antenna gains (dBi)  
- **L_t, L_r**: Transmit/receive losses (dB)
- **L_path**: Propagation path loss (dB)
- **L_misc**: Miscellaneous losses (dB)
- **M_fade**: Fade margin (dB)

### Fade Margin Design
**Fast fading**: Multipath interference (Rayleigh/Rician)
**Slow fading**: Shadowing effects (log-normal)
**Combined statistics**: Composite fading models

**Design margins**:
- **Fixed links**: 20-30 dB fade margin
- **Mobile systems**: 8-15 dB fade margin + diversity
- **Indoor systems**: 10-20 dB margin for coverage reliability

### Interference Analysis
**Carrier-to-interference ratio**: C/I = desired/interference power
**Co-channel interference**: Same frequency, different cells
**Adjacent channel interference**: Spectral spillover effects
**Intermodulation**: Nonlinear mixing products

---

## Measurement and Validation

### Near-Field Measurements
**SAR measurement**: Robotic probe in tissue phantom
**Near-field scanning**: Phase/amplitude mapping
**Spherical near-field**: Complete far-field pattern prediction

### Far-Field Measurements  
**Anechoic chamber**: Absorber-lined RF-quiet environment
**Outdoor range**: Ground reflection range, elevated range
**Compact range**: Collimated plane wave using reflector

### Propagation Measurements
**Drive testing**: Mobile measurements along routes
**Fixed monitoring**: Continuous link quality assessment
**Channel sounding**: Wideband impulse response measurement

**Validation criteria**: Measurements must match theoretical predictions within measurement uncertainty bounds (typically ±1-3 dB).

---

## Engineering Applications

### Antenna Design
- **Near-field coupling**: Affects input impedance and bandwidth
- **Pattern formation**: Fresnel zone clearance for desired pattern
- **Efficiency optimization**: Minimize near-field losses

### System Integration  
- **Component spacing**: Avoid near-field coupling between antennas
- **Shielding design**: Consider both near-field and far-field sources
- **EMC compliance**: Near-field emissions often dominate

### Link Planning
- **Coverage prediction**: Propagation models for deployment
- **Interference analysis**: Co-channel and adjacent channel planning
- **Capacity optimization**: Spatial reuse patterns

**Design Philosophy**: "Wave propagation follows immutable physical laws. Engineering success comes from working with these laws, not against them."