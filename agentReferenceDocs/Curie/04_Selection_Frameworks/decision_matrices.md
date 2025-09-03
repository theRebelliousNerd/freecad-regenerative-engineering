# Material Selection Decision Matrices
## Systematic Multi-Objective Optimization for Engineering Design

*"Every material choice is a multi-objective optimization problem."* - Curie Selection Principle

## Selection Methodology Framework

### Phase 1: Requirements Extraction Matrix

| Category | Requirement Type | Quantification Method | Typical Units | Weight Factor |
|----------|------------------|----------------------|---------------|---------------|
| **Mechanical** | Yield strength | σy > σdesign/SF | MPa | 0.15-0.25 |
| | Ultimate strength | σult > σmax | MPa | 0.10-0.20 |
| | Stiffness | E > Emin | GPa | 0.10-0.15 |
| | Fatigue resistance | Endurance limit | MPa at N cycles | 0.10-0.20 |
| | Fracture toughness | KIC > KIC,min | MPa·m^(1/2) | 0.05-0.15 |
| **Thermal** | Operating temperature | Tmax > Toperation + margin | °C | 0.20-0.30 |
| | Thermal conductivity | k > kmin OR k < kmax | W/m·K | 0.15-0.25 |
| | Thermal expansion | α compatibility | 10^-6/K | 0.10-0.20 |
| | Thermal shock | ΔTcritical > ΔTservice | °C | 0.05-0.15 |
| **Electrical** | Conductivity/resistivity | σe or ρe within range | S/m or Ω·m | 0.10-0.30 |
| | Dielectric strength | Vbreakdown > Vapplied × SF | kV/mm | 0.15-0.25 |
| | Dielectric constant | εr within range | Dimensionless | 0.05-0.15 |
| **Environmental** | Corrosion resistance | Corrosion rate < limit | mm/year | 0.10-0.30 |
| | UV stability | Degradation rate < limit | %/year | 0.05-0.20 |
| | Chemical compatibility | Compatibility index | Pass/Fail | 0.05-0.25 |
| **Manufacturing** | Processability | Process compatibility | Index 1-10 | 0.10-0.20 |
| | Machinability | Machinability index | Scale 1-100 | 0.05-0.15 |
| | Weldability/joinability | Joint strength retention | % | 0.05-0.15 |
| **Economic** | Material cost | Cost per unit mass/volume | $/kg or $/m³ | 0.05-0.25 |
| | Availability | Supply chain reliability | Index 1-10 | 0.05-0.15 |
| **Sustainability** | Carbon footprint | CO₂ equivalent | kg CO₂/kg | 0.05-0.20 |
| | Recyclability | End-of-life options | Index 1-10 | 0.05-0.15 |

### Phase 2: Material Performance Indices

#### Mechanical Efficiency Indices

**Stiffness-Limited Design (minimum weight)**:
```
M₁ = E/ρ        [Specific modulus, m²/s²]
M₂ = E^(1/2)/ρ  [Plate stiffness index]
M₃ = E^(1/3)/ρ  [Beam stiffness index]
```

**Strength-Limited Design (minimum weight)**:
```
M₄ = σy/ρ       [Specific strength, m²/s²]
M₅ = σy^(2/3)/ρ [Plate strength index]  
M₆ = σy^(1/2)/ρ [Beam strength index]
```

**Combined Loading**:
```
M₇ = σy·E^(1/2)/ρ  [Combined strength-stiffness]
```

#### Thermal Performance Indices

**Heat Conduction (minimum weight)**:
```
M₈ = k/ρ        [Thermal diffusion index]
```

**Thermal Shock Resistance**:
```
M₉ = σy·k/(E·α)  [Thermal shock parameter]
```

**Heat Sink Effectiveness**:
```
M₁₀ = k^(1/2)/(ρ·Cp^(1/2))  [Thermal effusivity ratio]
```

#### Multi-Physics Indices

**Electromagnetic Applications**:
```
M₁₁ = σe/ρ      [Specific conductivity]
M₁₂ = 1/(σe·μr·ρ) [EM shielding effectiveness]
```

**Structural-Thermal**:
```
M₁₃ = σy/(E·α·ρ)  [Thermal stress resistance]
```

### Phase 3: Decision Matrix Construction

#### Weighted Decision Matrix Template

| Material | Mechanical (30%) | Thermal (25%) | Environmental (20%) | Manufacturing (15%) | Cost (10%) | Total Score |
|----------|------------------|---------------|-------------------|-------------------|------------|-------------|
| | M₄ | M₁ | M₈ | M₉ | Corr.Resist. | Process. | Avail. | Raw Cost | Weighted |
| **Steel 316L** | 0.039 | 0.025 | 0.020 | 1.8 | 9 | 7 | 8 | 6 | 6.12 |
| **Al 6061-T6** | 0.102 | 0.025 | 0.062 | 3.2 | 6 | 9 | 9 | 8 | 7.45 |
| **Ti-6Al-4V** | 0.206 | 0.010 | 0.016 | 2.1 | 8 | 4 | 5 | 2 | 5.89 |
| **PEEK** | 0.076 | 0.003 | 0.0002 | 0.05 | 9 | 6 | 7 | 3 | 5.23 |

**Scoring Method**:
1. Normalize all criteria to 0-10 scale
2. Apply weight factors based on application priorities
3. Calculate weighted sum for each candidate
4. Sensitivity analysis on weight factors

#### Application-Specific Selection Matrices

### High-Temperature Structural Applications (T > 500°C)

| Material | Max Temp (°C) | σy @ Temp (MPa) | Oxidation Resistance | Thermal Shock | Cost Factor |
|----------|---------------|----------------|-------------------|---------------|-------------|
| **Inconel 718** | 650 | 1240 | Excellent | Good | 15× |
| **Haynes 230** | 1100 | 415 | Excellent | Excellent | 25× |
| **Mo-TZM** | 1600 | 450 | Moderate | Fair | 50× |
| **SiC (sintered)** | 1400 | 350 | Excellent | Poor | 10× |
| **C/C Composite** | 2000 | 200 | Poor (needs coating) | Excellent | 100× |

**Selection Algorithm**:
```python
def select_high_temp_material(T_operating, stress_level, oxidizing_environment):
    candidates = filter_by_temperature(materials_db, T_operating + margin)
    candidates = filter_by_strength(candidates, stress_level * safety_factor)
    
    if oxidizing_environment:
        candidates = filter_by_oxidation_resistance(candidates, "Good")
    
    return optimize_by_cost_performance(candidates)
```

### Electronics Thermal Management

| Application | Power Density | Recommended Materials | Thermal Interface |
|-------------|---------------|----------------------|------------------|
| **CPU/GPU** | 50-300 W/cm² | Cu heat spreader + Al fins | TIM + liquid cooling |
| **Power LEDs** | 100-500 W/cm² | Cu-diamond composite | Phase change TIM |
| **Power Electronics** | 10-100 W/cm² | AlN substrate, Cu base | Thermal pads |
| **RF Amplifiers** | 20-200 W/cm² | Cu-Mo base, diamond coating | Liquid metal TIM |

**TIM Selection Matrix**:
```
Power < 1 W/cm²:     Standard thermal paste (0.5-3 W/m·K)
1-5 W/cm²:          High-performance paste (3-8 W/m·K)  
5-20 W/cm²:         Phase change materials (2-4 W/m·K)
20-100 W/cm²:       Liquid metal TIM (20-80 W/m·K)
>100 W/cm²:         Direct liquid cooling required
```

### Corrosion Resistance Applications

| Environment | pH Range | Temperature | Recommended Materials | Notes |
|-------------|----------|-------------|----------------------|-------|
| **Seawater** | 8.1-8.3 | 5-40°C | 316L SS, Duplex SS, Ti | Pitting/crevice concern |
| **Acids** | 0-3 | 20-80°C | 316L, Hastelloy, PTFE | Concentration dependent |
| **Caustic** | 11-14 | 20-100°C | Nickel, Monel, 316L | Stress corrosion cracking |
| **High-Cl⁻** | Variable | 20-200°C | Super duplex, Inconel | Localized corrosion |
| **Organic Solvents** | 6-8 | -20-150°C | PTFE, PEEK, 316L | Chemical compatibility |

### Weight-Critical Applications (Aerospace, Automotive)

**Material Efficiency Rankings** (higher = better):

| Material | σy/ρ | E/ρ | σy^(2/3)/ρ | Comments |
|----------|------|-----|------------|----------|
| **Carbon Fiber** | 600 | 142 | 112 | Anisotropic, expensive |
| **Ti-6Al-4V** | 206 | 25.7 | 134 | Excellent all-around |
| **Al 7075-T6** | 179 | 25.5 | 124 | Cost-effective |
| **Mg AZ91** | 144 | 25.0 | 102 | Corrosion concerns |
| **CFRP Unidirectional** | 800 | 150 | 160 | Highly anisotropic |

### Manufacturing Process Compatibility

| Process | Compatible Materials | Design Constraints | Surface Finish |
|---------|---------------------|-------------------|----------------|
| **3D Printing (FDM)** | PLA, ABS, PETG, Nylon | 45° overhang limit | Ra 6-25 μm |
| **3D Printing (SLA)** | Photopolymers | Fine features possible | Ra 0.5-2 μm |
| **3D Printing (SLS)** | Nylon, metals | No support needed | Ra 3-15 μm |
| **Machining** | Metals, plastics | Tool access required | Ra 0.1-6 μm |
| **Casting** | Al, Fe, polymers | Draft angles needed | Ra 3-25 μm |
| **Forming** | Ductile metals | Spring-back compensation | Varies |

## Decision Validation Framework

### Sensitivity Analysis Protocol

1. **Parameter Variation Study**:
   - Vary each weight factor ±20%
   - Recalculate rankings
   - Identify robust solutions

2. **Uncertainty Propagation**:
   - Property uncertainty bounds
   - Monte Carlo simulation
   - Confidence intervals on selection

3. **Alternative Scenario Testing**:
   - Different operating conditions
   - Changed requirements priorities
   - Supply chain disruptions

### Selection Confidence Metrics

**Confidence Level Classification**:
- **High (>90%)**: Clear winner, insensitive to weight changes
- **Medium (70-90%)**: Good choice, some sensitivity to assumptions
- **Low (<70%)**: Marginal selection, requires prototype validation

**Validation Requirements**:
- High confidence: Proceed with design
- Medium confidence: Material testing recommended
- Low confidence: Mandatory prototype validation

### Common Selection Pitfalls and Mitigations

1. **Over-Optimization**: Single property focus ignoring others
   - **Mitigation**: Always use multi-objective analysis

2. **Property Database Errors**: Outdated or incorrect values
   - **Mitigation**: Cross-reference multiple sources

3. **Manufacturing Reality Gap**: Laboratory vs. production properties
   - **Mitigation**: Include manufacturing tolerances

4. **Environmental Condition Neglect**: Lab vs. service conditions
   - **Mitigation**: Environmental testing protocols

5. **Cost Estimation Errors**: Material cost vs. total cost
   - **Mitigation**: Lifecycle cost analysis

### Integration with Agent Workflow

**Input Requirements from Other Agents**:
- **Turing**: Kinematic loads, speeds, duty cycles
- **Tesla**: Power dissipation, electromagnetic fields
- **Edison**: Component thermal profiles, electrical requirements
- **Brunel**: Structural loads, safety factors
- **Gabe**: Manufacturing constraints, tolerances

**Output Specifications to Other Agents**:
- **Material Selection Results**: With properties and uncertainties
- **Thermal Interface Specifications**: For electromagnetic cooling
- **Environmental Compatibility**: For long-term reliability
- **Manufacturing Guidelines**: Material-process interactions

This systematic approach ensures that material selection decisions are quantitative, traceable, and optimized for the specific application requirements while maintaining awareness of manufacturing constraints and sustainability considerations.