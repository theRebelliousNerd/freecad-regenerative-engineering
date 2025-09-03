# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Electromagnetic Theory - Tesla's Fundamental Knowledge Base

## Overview
This directory contains the foundational electromagnetic theory that underpins all motor design work. These are Tesla's "Maxwell equations made manifest" - the mathematical principles that govern rotating magnetic fields and energy conversion.

## When to Read These Files (Just-in-Time Principle)

### Immediate Context Needed:
- **maxwells_equations.md** - Read FIRST when starting ANY motor design. These are the immutable physical laws that define what's possible.
- **rotating_magnetic_fields.md** - Read when designing stator windings or analyzing torque production. Tesla's core insight into motion from stationary coils.

### Triggered by Electromagnetic Uncertainty:
- When calculated flux density seems wrong
- When back-EMF predictions don't match requirements  
- When torque constants need validation
- When magnetic circuit reluctance calculations are needed

## Follow the Cable - Electromagnetic Energy Flow

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


In Tesla's vision, magnetic flux lines ARE the "cables" of electromagnetic energy:

### Primary Electromagnetic Cables:
1. **Flux Linkage Cable**: Links winding turns to induced voltage (Faraday's Law)
   - Source: Rotating permanent magnets or electromagnets
   - Destination: Stator coil voltages and currents
   - Criticality: Determines motor's fundamental voltage and speed characteristics

2. **Magnetic Circuit Cable**: The reluctance path through iron and air
   - Source: Magnetomotive force (ampere-turns)  
   - Destination: Flux density in air gap and iron
   - Criticality: Defines torque production capability

3. **Energy Conversion Cable**: Electrical power ↔ Mechanical power
   - Governed by: P_mech = T × ω and P_elec = V × I × cos(φ)
   - Loss nodes: Copper losses (I²R), iron losses, friction

### Dependency Networks:
Every electromagnetic decision creates dependencies:
- **Air gap size** → flux density → torque capability → mechanical requirements
- **Winding configuration** → back-EMF shape → control complexity → power electronics requirements  
- **Magnet choice** → operating temperature → thermal management → housing design

## Critical Files and Their Purpose:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### maxwells_equations.md
- **Purpose**: Mathematical foundation - the axioms that cannot be violated
- **Use When**: Starting any motor analysis, validating flux calculations
- **Key Content**: Field equations, boundary conditions, material properties

### rotating_magnetic_fields.md  
- **Purpose**: Tesla's revolutionary insight - how stationary windings create motion
- **Use When**: Designing stator topology, analyzing torque ripple
- **Key Content**: Three-phase field theory, pole pairs, synchronous rotation

### energy_conversion.md
- **Purpose**: The fundamental energy balance in electromagnetic machines
- **Use When**: Efficiency analysis, loss calculations, thermal planning
- **Key Content**: Power flow, loss mechanisms, efficiency optimization

## Metacognitive Electromagnetic Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**High-Priority Context Retrieval** (Read immediately):
- Calculated torque constant outside expected range (0.01-10 Nm/A)
- Back-EMF waveform doesn't match motor topology
- Magnetic saturation detected in analysis
- Efficiency predictions below 80% for modern motor

**Medium-Priority Context** (Consider reading):
- Unusual material properties encountered
- Non-standard winding configurations
- Complex magnetic circuit geometry
- Multi-physics coupling needed (electromagnetic-thermal)

## Integration with Other Domains

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


This electromagnetic knowledge base creates dependencies with other Tesla agent domains:

**→ Magnetic Materials**: Material properties constrain field solutions
**→ Motor Design**: Topology choices implement electromagnetic theory  
**→ Power Electronics**: Back-EMF waveform determines control complexity
**→ Thermal Integration**: Copper and iron losses create heat sources

Remember: In Tesla's world view, electromagnetic fields are living entities. These files help you see and manipulate those invisible energy patterns that create motion from pure electrical power.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!