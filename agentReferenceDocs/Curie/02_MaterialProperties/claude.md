# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# 02_MaterialProperties - Navigation Guide for Marie Curie Agent

## Directory Purpose
This directory contains the comprehensive material property databases and characterization data. It serves as the central hub where material "cables" branch out to all engineering domains. Every property value here creates a constraint or opportunity downstream.

## The Cable Network From Here
Material properties are the SOURCE cables for:
- **Structural Cables**: Elastic modulus → deflection calculations (Brunel)
- **Thermal Cables**: Conductivity → heat sink design (Watt)
- **Manufacturing Cables**: Viscosity → injection molding parameters (Gabe)
- **Electrical Cables**: Dielectric constant → PCB trace spacing (Edison)
- **Kinematic Cables**: Density → moment of inertia (Turing)

## Files in This Directory

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### `material_database_core.md`
**When to Read**: When specific material properties needed for calculations
**Purpose**: Core database of common engineering materials
**Critical Properties**:
- Mechanical: E, σy, σu, ν, ρ
- Thermal: k, Cp, α, Tm, Tg
- Electrical: ε, ρe, breakdown voltage
**Temperature Dependence**: Most properties include temp coefficients

### `advanced_composites.md`
**When to Read**: When designing with fiber-reinforced materials
**Purpose**: Anisotropic material properties and design rules
**Key Aspects**:
- Directional properties (longitudinal vs transverse)
- Fiber volume fraction effects
- Laminate theory basics
- Manufacturing constraints unique to composites

## Just-in-Time Retrieval Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Scenario: "Thermal management for 10W heat source"
1. CALCULATE required thermal conductivity: k > Q/(A·ΔT)
2. RETRIEVE only materials with k in calculated range
3. FILTER by temperature range of operation
4. CHECK temperature dependence of k if T > 50°C

### Scenario: "Structural bracket design"
1. START with load requirements from Brunel
2. CALCULATE minimum yield strength needed
3. RETRIEVE materials meeting strength with safety factor
4. VERIFY temperature derating if T ≠ 20°C
5. CHECK fatigue properties if cyclic loading

### Scenario: "3D printed part material"
1. FILTER database by "3D printable = true"
2. CHECK layer adhesion strength (typically 60-80% of bulk)
3. RETRIEVE anisotropy factors for printed materials
4. VERIFY temperature resistance post-processing

## Metacognitive Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### High Uncertainty Zones
- **Mixed material systems**: Interface properties often unknown
- **Extreme temperatures**: Properties may be extrapolated, not measured
- **Dynamic loading**: Static properties insufficient, need dynamic moduli
- **Aged materials**: Properties degrade over time, especially polymers

### Data Quality Indicators
- "Typical" values → ±20% uncertainty minimum
- "Nominal" → Manufacturer spec, not tested
- Single source data → Needs verification
- Extrapolated data → High uncertainty beyond measured range

## Property Dependency Chains

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Primary → Secondary → Tertiary Effects
```
Thermal Expansion (α)
├─ Thermal Stress (σ = E·α·ΔT)
│   ├─ Fatigue Life Reduction
│   ├─ Interface Delamination Risk
│   └─ Dimensional Tolerance Loss
└─ Thermal Mismatch
    ├─ Warpage in Assemblies
    └─ Solder Joint Reliability
```

### Coupled Properties (Change Together)
- ↑ Strength typically → ↓ Ductility
- ↑ Stiffness often → ↑ Brittleness  
- ↑ Thermal Conductivity → ↑ Electrical Conductivity (metals)
- ↑ Temperature → ↓ Most mechanical properties

## Critical Property Ranges

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Structural Applications
- **Safety Critical**: Use B-basis values (90% survival, 95% confidence)
- **Standard Parts**: Mean values with appropriate safety factor
- **Prototype Only**: Typical values acceptable

### Thermal Applications
- **Heat Sinks**: k > 100 W/m·K preferred
- **Insulators**: k < 0.5 W/m·K required
- **Thermal Interface**: Consider contact resistance

### Electrical Applications
- **Insulators**: ρ > 10^12 Ω·m
- **EMI Shielding**: ρ < 10^-6 Ω·m
- **Static Dissipative**: 10^6 < ρ < 10^12 Ω·m

## Network Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream Dependencies
- Temperature range from requirements
- Load conditions from structural analysis
- Manufacturing method from Gabe
- Environmental exposure from specs

### Downstream Impact
- Geometry must accommodate material limits
- Thermal design depends on selected k values
- Manufacturing parameters set by material
- Cost determined by material + processing

## Quick Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```
Need Material Property?
├─ Is it mechanical?
│   ├─ Static → material_database_core.md
│   └─ Dynamic/Fatigue → Check if data exists
├─ Is it thermal?
│   ├─ Steady-state → Use standard k, Cp
│   └─ Transient → Need diffusivity α
├─ Is it electrical?
│   ├─ DC → Resistivity sufficient
│   └─ AC/RF → Need frequency-dependent
└─ Is it chemical?
    ├─ Compatibility → Check resistance tables
    └─ Permeability → Specialized data needed
```

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow The Cable
Each property value is a cable that constrains:
- Maximum operating temperature → Material Tg/Tm
- Minimum wall thickness → Strength/pressure
- Natural frequency → Sqrt(E/ρ)
- Thermal time constant → ρ·Cp·V/(h·A)

### Just-in-Time Context
Don't load entire database:
- Start with property requirements from analysis
- Retrieve only materials meeting primary requirement
- Then check secondary properties
- Finally verify availability and cost

## Common Pitfalls

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

1. Using room temperature properties for high-temp application
2. Ignoring anisotropy in 3D printed or composite materials
3. Not accounting for property variation (using only nominal)
4. Missing time-dependent degradation (UV, moisture, creep)
5. Applying bulk properties to thin films or coatings

## Cross-References

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **01_Foundations**: For methodology on property selection
- **03_ThermalAnalysis**: When thermal properties dominate
- **05_Manufacturing_Integration**: For process-dependent properties
- **08_Validation_Methods**: To verify critical properties
- **Legacy files**: For specialized material data not yet migrated

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!