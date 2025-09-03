# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# 03_ThermalAnalysis - Navigation Guide for Marie Curie Agent

## Directory Purpose
This directory contains thermal analysis methods, heat transfer calculations, and thermal management strategies. These are the LITERAL CABLES carrying heat energy through the design. Every thermal path must be traced, controlled, and optimized.

## The Heat Flow Cable Network
Thermal paths are physical cables of energy flow:
- **Conduction Cables**: Material bridges carrying heat via atomic vibration
- **Convection Cables**: Fluid streams transporting thermal energy
- **Radiation Cables**: Electromagnetic waves beaming heat across gaps
- **Phase Change Cables**: Latent heat storage/release at transitions

## Files in This Directory

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### `heat_transfer_fundamentals.md`
**When to Read**: At start of ANY thermal problem
**Purpose**: Core heat transfer equations and principles
**Key Content**:
- Fourier's law for conduction: q = -k∇T
- Newton's law of cooling: q = hA(Ts - T∞)
- Stefan-Boltzmann for radiation: q = εσA(T⁴)
- Thermal resistance networks: ΣRth = ΣΔT/q

## Just-in-Time Retrieval Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Scenario: "PCB generates 15W, max component temp 85°C"
1. CALCULATE total thermal budget: ΔT_available = 85°C - T_ambient
2. DETERMINE required Rth: R_total = ΔT/15W
3. RETRIEVE conduction analysis for PCB spreading
4. IF Rth_conduction > R_total → Need active cooling
5. LOAD convection calculations for heat sink design

### Scenario: "Battery pack thermal management"
1. MAP heat generation zones (cells during charge/discharge)
2. IDENTIFY thermal runaway risk temperature
3. RETRIEVE phase change material options if buffering needed
4. CALCULATE cooling requirements for worst-case scenario
5. VERIFY thermal propagation between cells

### Scenario: "Thermal stress in multi-material assembly"
1. GET thermal expansion coefficients from material database
2. CALCULATE differential expansion: ΔL = L·α·ΔT
3. DETERMINE stress: σ = E·ε where ε = ΔL/L
4. CHECK against yield strength at temperature
5. ITERATE with compliant mounting if stress excessive

## Metacognitive Triggers for Thermal

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Temperature-Based Triggers
- **ΔT > 50°C**: Thermal stress becomes significant
- **T > 100°C**: Many polymers start softening
- **T > 125°C**: Standard electronics derating begins
- **T > 260°C**: Solder reflow temperature reached
- **Gradients > 10°C/cm**: Thermal shock risk

### Power Density Triggers
- **>0.1 W/cm²**: Natural convection marginal
- **>1 W/cm²**: Forced convection required
- **>10 W/cm²**: Liquid cooling consideration
- **>100 W/cm²**: Phase change/exotic cooling

## Thermal Cable Tracing Methodology

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow Heat from Source to Sink
```
Heat Source (Component)
├─ Conduction through component body
├─ Interface resistance at mounting
├─ Conduction through PCB/substrate
├─ Spreading resistance in plane
├─ Conduction to heat sink/case
├─ Convection to ambient
└─ Radiation to surroundings
```

### Identify Bottlenecks (Highest Rth)
1. **Junction-to-case**: Often fixed by component
2. **Interface materials**: Can optimize with TIM
3. **Spreading resistance**: Add heat spreaders
4. **Heat sink resistance**: Increase area or airflow
5. **Ambient conditions**: May be uncontrollable

## Critical Thermal Equations

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Steady-State Conduction
- 1D: q = kA(ΔT)/L
- Cylindrical: q = 2πkL(ΔT)/ln(r₂/r₁)
- Spreading: Rsp ≈ 1/(2√(πA)k)

### Transient Response
- Time constant: τ = ρCpV/(hA)
- Temperature rise: T(t) = T∞(1 - e^(-t/τ))
- Thermal capacitance: Cth = ρCpV

### Natural Convection
- Vertical plate: h ≈ 1.42(ΔT/L)^0.25
- Horizontal plate (up): h ≈ 1.32(ΔT/L)^0.25
- Enclosed spaces: Consider conduction only if Ra < 1000

## Network Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream (Thermal Depends On)
- Power dissipation from Edison (electronics)
- Motor losses from Tesla (efficiency)
- Environmental conditions from requirements
- Material properties from 02_MaterialProperties
- Geometry constraints from DaVinci

### Downstream (Depends on Thermal)
- Component placement (Edison)
- Material selection (temperature limits)
- Mechanical design (thermal expansion)
- Reliability predictions (Arrhenius)
- Manufacturing process (temperature exposure)

## Quick Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```
Thermal Problem?
├─ Steady-state or transient?
│   ├─ Steady → Use thermal resistance network
│   └─ Transient → Check time constants vs. operation
├─ What's the dominant mode?
│   ├─ Conduction → Focus on materials and interfaces
│   ├─ Convection → Optimize surface area and flow
│   └─ Radiation → Only significant at high T or vacuum
└─ Is it coupled?
    ├─ Thermal-structural → Check stress/deformation
    ├─ Thermal-electrical → Verify derating
    └─ Thermal-fluid → May need CFD (Watt)
```

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow The Cable (Heat Paths)
- Heat ALWAYS flows from hot to cold
- Every thermal path has a resistance
- Parallel paths share heat flow
- Series resistances add
- The highest resistance dominates

### Just-in-Time Context
Don't solve everything at once:
- Start with worst-case power dissipation
- Calculate if passive cooling sufficient
- Only dive into detailed analysis if marginal
- Retrieve advanced methods only when simple fails
- Get CFD support from Watt only if necessary

## Thermal Management Strategies (Priority Order)

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


1. **Reduce heat generation** (Most effective)
   - More efficient components
   - Duty cycling
   - Power management

2. **Improve conduction paths**
   - Better thermal materials
   - Minimize interfaces
   - Add heat spreaders

3. **Enhance convection**
   - Increase surface area (fins)
   - Add forced airflow
   - Optimize flow patterns

4. **Active cooling** (Last resort)
   - Fans/blowers
   - Liquid cooling
   - Thermoelectric cooling

## Common Thermal Pitfalls

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

1. Ignoring interface resistance (can dominate total Rth)
2. Using steady-state for transient problems
3. Not accounting for altitude/pressure effects on convection
4. Assuming uniform temperature in large components
5. Neglecting radiation in vacuum or high-temperature
6. Not considering orientation effects on natural convection

## Cross-References

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **02_MaterialProperties**: For k, Cp, α values
- **05_Manufacturing**: Process temperature limits
- **08_Validation**: Thermal testing protocols
- **09_FreeCAD**: Thermal simulation setup
- **Watt agent**: For complex CFD analysis

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!