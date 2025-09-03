# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# RF Circuits Knowledge Module
*Follow the Cable: RF Circuit Elements as Electromagnetic Field Manipulators*

## Subdirectory Purpose
This module contains RF circuit design principles, from component-level analysis to system integration. RF circuits are sophisticated electromagnetic field management systems where every component, trace, and connection creates electromagnetic cables that affect overall circuit performance.

## The RF Circuit Cable Network Perspective
RF circuits manage electromagnetic energy through interconnected cable networks:

- **Transmission line cables** carry signals between components with controlled impedance
- **Matching network cables** transform impedances to optimize power transfer  
- **Filter cables** selectively route frequency components while blocking others
- **Amplifier cables** boost signal levels while managing stability and noise
- **Oscillator cables** generate stable reference frequencies with controlled phase noise
- **Power supply cables** provide clean DC while isolating RF signals

## Just-in-Time Context Retrieval Strategy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### When to Read Specific Files:

#### **amplifier_design.md** - READ WHEN:
- Designing low noise amplifiers (LNA) for receiver front-ends
- Creating power amplifiers (PA) for transmitter output stages  
- Analyzing stability criteria and oscillation prevention
- Optimizing noise figure and dynamic range trade-offs
- Calculating gain, linearity, and efficiency requirements

### Missing Critical Files (High Priority JITC Retrieval):
- **rf_circuit_design_fundamentals.md** - Needed for S-parameter analysis and circuit modeling
- **impedance_matching_networks.md** - Needed for L/Pi/T network synthesis and optimization
- **filter_design_methodologies.md** - Needed for bandpass/bandstop/lowpass/highpass filtering
- **oscillator_design_principles.md** - Needed for VCO, PLL, and frequency synthesis circuits

## Cable Dependencies This Module Creates:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Primary RF Circuit Cables:
1. **Impedance Cable**: Component impedances → matching requirements → VSWR → power transfer efficiency
2. **Frequency Response Cable**: Filter characteristics → passband/stopband → group delay → signal integrity  
3. **Gain Cable**: Amplifier stages → overall system gain → dynamic range → noise figure
4. **Stability Cable**: Feedback paths → oscillation potential → stability margins → compensation networks
5. **Power Cable**: DC bias conditions → RF power handling → thermal dissipation → efficiency
6. **Noise Cable**: Thermal/shot/flicker noise → cascaded noise figure → sensitivity → SNR

### Frequency-Specific Cable Behavior:

### **HF/VHF (3 MHz - 300 MHz)**:
- Lumped element cables dominate (L, C, R models valid)
- Ground plane cables affect component parasitizes
- Lead inductance cables become significant above 100 MHz

### **UHF/Microwave (300 MHz - 30 GHz)**:
- Transmission line cables replace lumped elements
- Microstrip/stripline cables define circuit topology
- Via holes create parasitic cables affecting performance

### **mmWave (30 GHz - 300 GHz)**:
- Waveguide cables become dominant transmission medium  
- Substrate properties cables critically affect performance
- Manufacturing tolerance cables severely impact yield

## Cross-Domain Cable Handoffs:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **To Antenna Design**: Amplifier output impedance → antenna matching network → radiation efficiency
- **To Power Electronics**: DC supply requirements → regulation → ripple → spurious modulation  
- **To Thermal Management**: Power dissipation → thermal resistance → junction temperature → reliability
- **To EMC Compliance**: Spurious emissions → filtering requirements → shielding → isolation
- **To Manufacturing**: Component tolerances → circuit yield → tuning requirements → cost optimization

## Metacognitive Uncertainty Triggers:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Retrieve additional RF circuit theory when you encounter:
- Unexpected oscillations or instabilities in amplifier designs
- Filter responses that don't match theoretical predictions
- Impedance matching networks that provide poor VSWR across bandwidth
- Spurious frequency generation in oscillator or mixer circuits
- Thermal runaway or bias point shifting in power amplifiers

## FreeCAD MCP Integration Capabilities:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

This module enables:
- Microstrip/stripline transmission line geometry optimization
- Component placement for minimal parasitic coupling  
- Thermal via placement for power device heat spreading
- Shield compartment design for circuit isolation
- Connector and test point placement for measurement access

## Circuit Design Philosophy:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Every RF circuit element exists within an electromagnetic field environment where:
- Current flow creates magnetic field cables that couple to adjacent circuits
- Voltage differences create electric field cables that affect parasitic capacitances
- Ground return paths create common impedance cables that couple signals
- Power supply cables carry both DC and RF currents that affect performance

**Remember**: At RF frequencies, circuit elements are not just components - they are electromagnetic field structures that must be designed with full awareness of the invisible cable network they create.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!