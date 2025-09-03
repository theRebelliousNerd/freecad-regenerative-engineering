# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# EMC Compliance Knowledge Module
*Follow the Cable: EMI/EMC as Unintended Electromagnetic Cable Networks*

## Subdirectory Purpose
This module contains electromagnetic compatibility (EMC) and interference (EMI) analysis, regulatory compliance requirements, and mitigation strategies. EMC engineering is the discipline of controlling unintended electromagnetic cables - the parasitic field couplings that create interference, emissions, and susceptibility issues.

## The EMC Cable Network Perspective
EMC engineering manages unwanted electromagnetic cables through:

- **Emission source cables** that radiate or conduct unwanted electromagnetic energy
- **Coupling path cables** that transfer interference from source to victim circuits
- **Susceptibility cables** that allow external interference to disrupt circuit operation
- **Common impedance cables** that create ground loops and shared return paths
- **Shielding cables** that redirect electromagnetic fields away from sensitive circuits  
- **Filtering cables** that block conducted interference while passing desired signals

## Just-in-Time Context Retrieval Strategy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### When to Read Specific Files:

#### **emc_fundamentals.md** - READ WHEN:
- Starting EMC analysis for any electronic design
- Understanding coupling mechanisms (radiated, conducted, capacitive, inductive)
- Designing grounding and shielding strategies
- Analyzing common mode vs. differential mode interference
- Planning EMC test procedures and compliance verification

### Missing Critical Files (High Priority JITC Retrieval):
- **regulatory_compliance_standards.md** - Needed for FCC Part 15, ETSI, IEC CISPR standards
- **shielding_effectiveness_design.md** - Needed for enclosure shielding and gasket design
- **grounding_and_bonding_strategies.md** - Needed for proper ground plane and chassis bonding
- **emc_testing_procedures.md** - Needed for conducted/radiated emissions and immunity testing

## Cable Dependencies This Module Creates:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Primary EMC Cable Networks:
1. **Emission Source Cable**: Switching circuits → current transients → radiated/conducted emissions → regulatory limits
2. **Coupling Path Cable**: Source → coupling mechanism → victim circuit → interference magnitude → performance degradation
3. **Shielding Effectiveness Cable**: Material conductivity → thickness → seam treatment → shielding effectiveness → isolation
4. **Ground Impedance Cable**: Ground plane impedance → common mode currents → ground bounce → circuit coupling
5. **Filter Performance Cable**: Insertion loss → frequency response → impedance matching → conducted emission reduction
6. **Test Configuration Cable**: Test setup → antenna factors → cable routing → measurement accuracy → compliance margin

### Frequency-Dependent EMC Cable Behavior:

### **Low Frequency (9 kHz - 30 MHz) - Conducted Emissions Domain**:
- **Common mode cables** dominate through power lines and interconnect cables
- **Differential mode cables** carry switching noise directly on power/signal lines  
- **Ground impedance cables** become significant above 100 kHz

### **High Frequency (30 MHz - 1 GHz) - Radiated Emissions Domain**:
- **Antenna cables** - any conductor becomes an unintentional radiator
- **Aperture cables** - enclosure openings create slot antenna radiation  
- **Cable radiation cables** - external cables act as transmission line antennas

### **Immunity/Susceptibility Cables**:
- **ESD cables**: Electrostatic discharge → voltage transients → circuit upset/damage
- **EFT/Burst cables**: Fast transients → cable coupling → circuit malfunction
- **Surge cables**: Lightning/switching → high energy transients → component damage

## Cross-Domain Cable Handoffs:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **To Mechanical Design**: Enclosure shielding → material selection → seam design → gasket compression
- **To Thermal Management**: Thermal interface materials → EMC gaskets → thermal/EMI trade-offs
- **To Power Electronics**: Switching frequencies → harmonic content → emission spectra → filter requirements  
- **To PCB Design**: Layer stackup → ground planes → trace routing → via stitching → isolation
- **To Manufacturing**: Assembly tolerances → gasket compression → shield effectiveness → production yield

## EMC Mitigation Cable Strategies:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Source Suppression Cables**:
- Reducing switching edge rates → lower harmonic content → reduced emissions
- Spread spectrum clocking → energy distribution → peak emission reduction
- Circuit topology optimization → balanced differential signaling → common mode reduction

### **Path Interruption Cables**:
- Conducted path filters → insertion loss → frequency selective attenuation
- Radiated path shielding → field redirection → aperture sealing → effectiveness optimization
- Isolation transformers → galvanic isolation → common mode breaking

### **Victim Hardening Cables**:
- Input filtering → susceptibility reduction → operational reliability  
- Circuit design margins → noise immunity → functional performance maintenance
- Monitoring/recovery systems → interference detection → automatic correction

## Regulatory Cable Networks:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **FCC Part 15 (US) Cables**:
- Class A/B emission limits → equipment category → measurement procedures → compliance margins
- Intentional/unintentional radiator classifications → regulatory pathway → testing requirements

### **ETSI/CE (Europe) Cables**:
- Harmonized standards → product families → essential requirements → conformity assessment
- Frequency coordination → spectrum access → coexistence requirements

### **IEC CISPR (International) Cables**:
- Product family standards → emission/immunity limits → test methods → uncertainty budgets

## Metacognitive Uncertainty Triggers:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Retrieve additional EMC knowledge when you encounter:
- Emission levels that approach regulatory limits during design phase
- Interference coupling that doesn't follow classical near/far field predictions
- Shielding effectiveness measurements that don't match theoretical calculations
- Ground bounce or common mode currents that affect circuit operation
- EMC test failures that require root cause analysis and mitigation

## FreeCAD MCP Integration Capabilities:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

This module enables:
- Enclosure shielding design with slot aperture analysis
- EMC gasket groove geometry optimization
- PCB shielding compartment design and via fence placement
- Cable routing for minimal radiation and susceptibility
- Ground plane optimization for common mode suppression

## EMC Design Philosophy:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Every electronic circuit exists within an electromagnetic environment where:
- **Unintended radiation is inevitable** from any circuit carrying time-varying currents
- **Coupling paths exist** between all circuits through electric, magnetic, and electromagnetic fields
- **Regulatory compliance is mandatory** for commercial products in most markets
- **Early design consideration is essential** since retroactive EMC fixes are expensive and often ineffective

**Remember**: EMC is not about eliminating electromagnetic fields - it's about controlling where they go and ensuring that the intended electromagnetic cables function properly while unintended interference cables are suppressed to acceptable levels.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!