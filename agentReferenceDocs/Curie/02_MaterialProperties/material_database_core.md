# Core Material Properties Database
## Systematic Classification for Engineering Applications

*"Every material is a solution to a specific physics problem."* - Curie Design Principle

## Database Organization Philosophy

Materials organized by primary functional behavior rather than traditional chemistry classifications. This enables performance-first selection aligned with engineering requirements.

## Category 1: Structural Load-Bearing Materials

### High-Strength Steels
**Primary Applications**: Structural frameworks, pressure vessels, mechanical components

| Material | σ_y (MPa) | σ_ult (MPa) | E (GPa) | ρ (g/cm³) | k (W/m·K) | α (10⁻⁶/K) | T_max (°C) |
|----------|-----------|-------------|----------|-----------|------------|-------------|------------|
| AISI 4140 (Q&T) | 655-1000 | 850-1200 | 205 | 7.85 | 42.6 | 12.3 | 400 |
| AISI 316L SS | 170-310 | 485-620 | 200 | 8.00 | 16.2 | 15.9 | 870 |
| Maraging 250 | 1720 | 1760 | 186 | 8.00 | 19.5 | 10.1 | 480 |
| HSLA-80 | 550 | 620 | 200 | 7.85 | 50 | 12.0 | 350 |

**Selection Criteria**:
- σ_y/ρ > 70 kN·m/kg for weight-critical applications
- k > 40 W/m·K for thermal management needs
- Stainless grades for corrosive environments

### Advanced Aluminum Alloys
**Primary Applications**: Aerospace, automotive, thermal management

| Material | σ_y (MPa) | σ_ult (MPa) | E (GPa) | ρ (g/cm³) | k (W/m·K) | α (10⁻⁶/K) | T_max (°C) |
|----------|-----------|-------------|----------|-----------|------------|-------------|------------|
| 7075-T6 | 503 | 572 | 71.7 | 2.81 | 130 | 23.2 | 175 |
| 6061-T6 | 276 | 310 | 68.9 | 2.70 | 167 | 23.6 | 200 |
| 2024-T4 | 324 | 469 | 73.1 | 2.78 | 121 | 22.9 | 150 |
| A356-T6 | 205 | 283 | 72.4 | 2.68 | 151 | 21.5 | 200 |

**Selection Criteria**:
- Strength-to-weight champion: 7075-T6
- Best thermal: 6061-T6 for heat sinks
- Castability: A356 for complex geometries

### Engineering Polymers  
**Primary Applications**: Electrical insulation, chemical resistance, lightweight structures

| Material | σ_y (MPa) | σ_ult (MPa) | E (GPa) | ρ (g/cm³) | k (W/m·K) | α (10⁻⁶/K) | T_max (°C) |
|----------|-----------|-------------|----------|-----------|------------|-------------|------------|
| PEEK | 90-100 | 170 | 3.6 | 1.32 | 0.25 | 47 | 250 |
| PEI (Ultem) | 105 | 215 | 3.2 | 1.27 | 0.22 | 56 | 217 |
| PTFE | 15-25 | 20-35 | 0.5 | 2.17 | 0.24 | 135 | 260 |
| Nylon 6,6 | 45-85 | 65-120 | 2.8 | 1.14 | 0.25 | 80 | 150 |

**Selection Criteria**:
- PEEK for extreme chemical resistance
- PEI for electrical applications requiring transparency
- PTFE for ultra-low friction applications

## Category 2: Thermal Management Materials

### High Thermal Conductivity Metals
**Primary Applications**: Heat sinks, thermal interfaces, electronic cooling

| Material | k (W/m·K) @ 20°C | ρ (g/cm³) | C_p (J/kg·K) | α_th (mm²/s) | σ_e (S/m) | Cost Factor |
|----------|-------------------|-----------|--------------|---------------|-----------|-------------|
| Silver | 429 | 10.49 | 235 | 174 | 6.30×10⁷ | 1000× |
| Copper | 401 | 8.96 | 385 | 116 | 5.96×10⁷ | 10× |
| Aluminum | 237 | 2.70 | 897 | 97.1 | 3.77×10⁷ | 1× |
| Gold | 317 | 19.32 | 129 | 127 | 4.52×10⁷ | 2000× |

**Thermal Design Calculations**:
```
Thermal Resistance: R_th = L / (k × A)
Thermal Diffusivity: α = k / (ρ × C_p)  
Heat Sink Efficiency: η = tanh(mL) / (mL), where m = √(hP/kA)
```

### Thermal Interface Materials (TIMs)
**Primary Applications**: CPU/GPU cooling, power electronics, LED thermal management

| Material Type | k (W/m·K) | Contact Resistance (K·cm²/W) | Compliance | T_max (°C) | Cost |
|---------------|-----------|------------------------------|------------|------------|------|
| Thermal Paste | 3-12 | 0.05-0.20 | Excellent | 150-200 | Low |
| Thermal Pads | 1-8 | 0.10-0.50 | Good | 200-300 | Medium |
| Phase Change | 2-4 | 0.02-0.10 | Excellent | 60-80 | Medium |
| Liquid Metal | 20-80 | 0.01-0.03 | Poor | 200+ | High |

**Selection Matrix**:
- **Power < 5W**: Thermal paste sufficient
- **5W < Power < 50W**: High-performance pads
- **Power > 50W**: Phase change or liquid metal
- **Maintenance access limited**: Permanent pads preferred

### Thermal Barrier/Insulation Materials
**Primary Applications**: High-temperature insulation, cryogenic applications

| Material | k (W/m·K) | ρ (g/cm³) | T_max (°C) | T_min (°C) | Compressive Strength (MPa) |
|----------|-----------|-----------|------------|------------|----------------------------|
| Aerogel | 0.013-0.014 | 0.10-0.15 | 650 | -196 | 1-4 |
| Vacuum Panels | 0.004-0.008 | 0.20 | 60 | -200 | Minimal |
| Fiberglass | 0.035-0.040 | 0.10-0.20 | 540 | -196 | 10-25 |
| Ceramic Fiber | 0.12-0.20 | 0.13 | 1260 | N/A | 5-15 |

## Category 3: Electrical/Electronic Materials

### Conductors
**Primary Applications**: Wiring, bus bars, electromagnetic coils

| Material | σ_e (S/m) | ρ_e (Ω·m) | k (W/m·K) | T_coeff (/K) | Max Current Density (A/mm²) |
|----------|-----------|-----------|------------|--------------|----------------------------|
| Silver | 6.30×10⁷ | 1.59×10⁻⁸ | 429 | 0.0038 | 3-4 |
| Copper | 5.96×10⁷ | 1.68×10⁻⁸ | 401 | 0.0039 | 2-3 |
| Gold | 4.52×10⁷ | 2.21×10⁻⁸ | 317 | 0.0034 | 2-3 |
| Aluminum | 3.77×10⁷ | 2.65×10⁻⁸ | 237 | 0.0043 | 1-2 |

### Insulators  
**Primary Applications**: Electrical isolation, high-voltage applications

| Material | Dielectric Strength (kV/mm) | Relative Permittivity | Dissipation Factor | Volume Resistivity (Ω·cm) |
|----------|-----------------------------|-----------------------|-------------------|---------------------------|
| PTFE | 60 | 2.1 | 0.0002 | 10¹⁸ |
| Polyethylene | 50 | 2.3 | 0.0005 | 10¹⁶ |
| Ceramic (Al₂O₃) | 15-35 | 9.8 | 0.0003 | 10¹⁴ |
| Epoxy Glass | 15-20 | 4.5 | 0.02 | 10¹³ |

## Material Selection Decision Trees

### For High-Temperature Applications (>200°C)
```
Temperature Range Assessment:
├─ 200-400°C → Stainless steels, ceramics, PEEK
├─ 400-800°C → Superalloys, refractory metals
├─ 800-1200°C → Ceramics, carbon composites  
└─ >1200°C → Refractory ceramics, tungsten
```

### For Thermal Management Applications  
```
Heat Flux Assessment:
├─ <1 W/cm² → Standard aluminum heat sinks
├─ 1-10 W/cm² → Copper heat sinks + TIMs
├─ 10-100 W/cm² → Advanced cooling (liquid, phase change)
└─ >100 W/cm² → Specialized cooling systems required
```

### For Electrical Applications
```
Voltage Level Assessment:  
├─ <50V → Standard polymers acceptable
├─ 50-1000V → Engineering plastics, enhanced creepage
├─ 1-10 kV → High-grade insulators, air gaps
└─ >10 kV → Specialized high-voltage design required
```

## Property Uncertainty and Safety Factors

### Typical Property Variations
- **Yield Strength**: ±10% for metals, ±20% for polymers
- **Thermal Conductivity**: ±5% for pure metals, ±15% for alloys
- **Electrical Properties**: ±10% typical
- **Temperature Coefficients**: ±20% variation possible

### Recommended Safety Factors by Application
- **Safety-Critical Structure**: 4-8× yield strength
- **General Machine Design**: 2-4× yield strength  
- **Thermal Design**: 20-30% thermal margin
- **Electrical Insulation**: 2-3× dielectric strength

### Material Database Status
- **Verified Properties**: Traceable to standards (ASTM, ISO)
- **Estimated Properties**: Based on similar materials
- **Calculated Properties**: From first principles or correlations
- **Unknown Properties**: Require experimental determination

This database provides the foundation for all Curie material selection decisions, with emphasis on verified, quantitative properties that enable confident engineering analysis.