# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# 01_Foundations - Navigation Guide for Marie Curie Agent

## Directory Purpose
This directory contains the foundational philosophical and methodological framework for materials science and thermal analysis. It represents the starting point of the material selection "cable" that propagates through all design decisions.

## The Cable Network Starting Here
Material foundations create dependencies that flow through:
- **To Manufacturing (Gabe)**: Material properties determine printability, machinability
- **To Structural (Brunel)**: Yield strength, elastic modulus define load capacity
- **To Thermal (Watt)**: Thermal conductivity, specific heat govern heat flow
- **To Electronics (Edison)**: Dielectric properties, thermal resistance affect PCB design
- **To Verification (Archimedes)**: Material axioms constrain geometric possibilities

## Files in This Directory

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### `curie_methodology.md`
**When to Read**: ALWAYS at project start before any material selection
**Purpose**: Core methodology for systematic material investigation
**Dependencies Created**: 
- Establishes the scientific rigor required for all subsequent material decisions
- Sets uncertainty quantification standards used throughout analysis
**Key Concepts**:
- Multi-objective optimization framework
- Coupled field environment analysis
- Material-process interaction principles

## Just-in-Time Retrieval Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Scenario: "Select material for enclosure"
1. START with `curie_methodology.md` for framework
2. THEN retrieve material database from 02_MaterialProperties
3. IF thermal critical → Pull 03_ThermalAnalysis
4. IF manufacturing constrained → Get 05_Manufacturing_Integration

### Scenario: "Material failure investigation"
1. Check methodology for failure mode classification
2. Follow cable to 08_Validation_Methods for test protocols
3. Trace back through process history in 05_Manufacturing

## Metacognitive Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### High Uncertainty Indicators
- "About" or "approximately" in material specs → STOP, get exact data
- Temperature range spans phase transition → Retrieve phase behavior
- Multi-physics coupling present → Load coupled analysis framework
- New material class → Check if methodology covers this domain

### Knowledge Gap Signals
- Missing material property for critical calculation
- Conflicting data from different sources
- Environmental conditions outside standard ranges
- Manufacturing process not in database

## Critical Temperature Ranges

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cryogenic (<-150°C)
- Material brittleness becomes primary concern
- Special methodology required, not standard selection

### Standard Operating (-40°C to +85°C)
- Most consumer electronics range
- Standard material database applicable

### High Temperature (>150°C)
- Creep becomes significant
- Time-dependent properties must be considered
- Pull specialized high-temp methodology

### Phase Transition Zones
- ANY temperature range crossing phase transition
- Requires detailed thermal cycling analysis
- Properties become highly non-linear

## Network Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream (What This Depends On)
- Requirements from Requirements Interrogator
- Constraints from Archimedes axioms
- Environmental conditions from project specs

### Downstream (What Depends on This)
- ALL material selection decisions
- Thermal management strategies
- Manufacturing process selection
- Failure mode predictions
- Cost optimization

## Quick Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```
Is this first material contact in project?
├─ YES → Read curie_methodology.md COMPLETELY
├─ NO → Is uncertainty >15%?
│   ├─ YES → Review methodology section on uncertainty
│   └─ NO → Is this a new material class?
│       ├─ YES → Check if methodology covers domain
│       └─ NO → Proceed to specific property lookup
```

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow The Cable
The methodology established here is the SOURCE cable for:
- Material property requirements flowing to suppliers
- Thermal constraints propagating to system design
- Manufacturing limits defining geometry
- Environmental resistance determining lifecycle

### Just-in-Time Context
Don't load entire material science knowledge upfront:
- Retrieve specific property data only when needed
- Load test methods only when validation required
- Pull manufacturing interactions only for selected processes
- Get environmental degradation data only for service conditions

## Common Pitfalls to Avoid

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

1. Starting material selection without methodology review
2. Using generic properties without temperature dependence
3. Ignoring manufacturing effects on final properties
4. Treating materials as isolated rather than coupled systems
5. Not quantifying uncertainty in material data

## References to Other Directories

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **02_MaterialProperties**: Detailed property databases
- **03_ThermalAnalysis**: When thermal is primary concern
- **04_Selection_Frameworks**: For complex trade-offs
- **05_Manufacturing_Integration**: Process-property relationships
- **08_Validation_Methods**: To verify selections

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!