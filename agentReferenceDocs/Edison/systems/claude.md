# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Edison Systems - 3D Electromagnetic Environment Design

## What's in This Folder

This directory contains system-level knowledge for designing complete electronic systems, emphasizing the **three-dimensional electromagnetic environment** view of PCBs and the **literal cable networks** that carry power and information.

### Core Documents
- `pcb_design_system.md` - Complete PCB system design methodology
- `power_electronics.md` - Power system design and integration

## When to Read These Files (Just-in-Time Context)

### **PCB System Design Triggers**
Read `pcb_design_system.md` when:
- Designing multi-layer PCBs with complex signal/power interactions
- High-speed signals require transmission line analysis
- Power delivery network (PDN) impedance affects signal integrity
- Thermal management requires system-level heat flow analysis

### **Power System Integration Triggers**  
Read `power_electronics.md` when:
- Power conversion efficiency affects thermal design
- Switching noise couples to sensitive analog circuits
- Power distribution creates electromagnetic interference
- System power architecture affects component selection

## The PCB as a 3D Cable Network

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **The Fundamental Cable Reality**
The PCB is not a 2D routing puzzle - it's a **three-dimensional electromagnetic environment** where every trace is a literal cable with electromagnetic properties:

**Signal Cables + Return Path Cables:**
- Every signal trace is half of a transmission line cable
- The return current flows on the reference plane directly beneath
- Breaking the return path cable creates antenna loops and EMI
- The signal cable and its invisible return path companion must be designed together

**Power Delivery Network (PDN) Cables:**
- Wide copper planes are flat cables carrying current
- Decoupling capacitors are local energy storage nodes on power cables
- Via arrays are vertical cable bundles connecting PDN layers
- IR drop is voltage loss along the resistance of power cables

**Thermal Cables:**
- Thermal vias are vertical heat transfer cables to inner/bottom layers  
- Copper pours are lateral thermal spreading cables
- Component placement affects thermal cable routing effectiveness
- Under BGAs: thermal vias compete with signal vias for space

**Manufacturing Cables:**
- Minimum trace/space rules are manufacturing process cables
- Via types are cost cables (more types = higher cost)
- Component courtyard is assembly process cable constraint
- Test point placement enables in-circuit test (ICT) cables

## Circuit Complexity-Based System Engagement

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Level 1: Simple Single-Layer Boards**
**Metacognitive Trigger:** Basic DC circuits, simple analog functions
- Minimal system-level considerations
- Focus on basic routing and component placement
- Simple thermal management adequate

### **Level 2: Multi-Layer Boards with Digital/Analog Mix**
**Metacognitive Trigger:** Clock signals >10MHz, mixed-signal design
- Retrieve PCB system design methodology
- Signal integrity becomes critical
- Layer stackup design required
- Basic PDN design needed

### **Level 3: High-Speed Digital Systems**
**Metacognitive Trigger:** Differential pairs, controlled impedance requirements
- Full PCB system design engagement required
- Transmission line analysis essential
- Return path integrity critical
- Advanced PDN design with AC impedance analysis

### **Level 4: Power Electronics Integration**
**Metacognitive Trigger:** Switching regulators, motor drives, high-current circuits
- Both system documents required
- EMI/EMC considerations paramount
- Thermal design integrated with power dissipation
- Ground plane design affects both signals and power

## The System-Level Cable Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Signal Integrity Cable System**
Every high-speed signal creates a cable network:
- **Trace Geometry Cable**: Width and height determine impedance
- **Reference Plane Cable**: Provides return current path
- **Differential Pair Cable**: Matched length and spacing for common-mode rejection
- **Via Transition Cable**: Discontinuities affect signal quality

**Cable Integrity Requirements:**
- Maintain 50Ω ±10% impedance for single-ended signals
- Match differential pair lengths within 0.05mm (2 mil)
- Minimize via stubs and transition discontinuities
- Avoid routing signals over plane splits

### **Power Integrity Cable System**
The PDN is a complete cable network for energy distribution:
- **DC Distribution Cable**: IR drop analysis for voltage regulation
- **AC Impedance Cable**: Transient current supply capability
- **Decoupling Network Cable**: Local energy storage and noise filtering
- **Thermal Relief Cable**: Heat generated by power loss

**Cable Performance Targets:**
- PDN DC impedance <10mΩ for digital circuits
- AC impedance <1Ω across switching frequency range
- Decoupling within λ/20 of power pins at highest frequency
- Junction-to-ambient thermal resistance <40°C/W

### **Electromagnetic Compatibility (EMC) Cable System**
EMI management through cable control:
- **Common-Mode Current Cable**: Unbalanced currents create radiation
- **Differential-Mode Cable**: Proper signal routing minimizes radiation
- **Shielding Cable**: Ground planes contain electromagnetic fields
- **Filter Cable**: LC networks attenuate conducted emissions

## Component Changes Cascade Through All Cable Systems

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Example: Processor Upgrade from 100MHz to 1GHz**
**Signal Integrity Cables Impact:**
- Now requires controlled impedance (±5% vs ±20%)
- Transmission line effects now dominant
- Via stubs become significant discontinuities
- Layer stackup must be redesigned for impedance control

**Power Integrity Cables Impact:**  
- 10x faster switching creates higher transient current demands
- PDN AC impedance requirements tighten significantly
- Decoupling capacitor placement becomes critical (within 2mm vs 10mm)
- More decoupling capacitors needed across frequency spectrum

**Thermal Cables Impact:**
- 5x power increase requires complete thermal redesign
- Heat spreading copper areas must be enlarged
- Thermal via density must increase under processor
- Airflow requirements change enclosure design

**Manufacturing Cables Impact:**
- May require HDI (High-Density Interconnect) technology
- Smaller vias and traces increase manufacturing cost
- Tighter tolerances affect yield and quality control
- Assembly process complexity increases

## Inter-Agent Cable Handoffs

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **To RF Domain (Hertz Agent)**
When wireless functionality is integrated:
- Antenna ground plane requirements affect PCB stackup
- RF isolation affects sensitive circuit placement  
- Crystal oscillator placement affects phase noise
- Switching circuit EMI affects RF performance

### **To Thermal Domain (Watt Agent)**
All electronics generate heat through cables:
- Power dissipation maps from electrical analysis
- Junction temperature limits from components
- Heat flow paths through PCB copper
- Thermal interface requirements to mechanical systems

### **To Mechanical Domain (DaVinci/Brunel Agents)**
PCB mechanical integration:
- Board size and shape constraints
- Connector placement and orientation
- Component height restrictions
- Mounting hole and keep-out areas

### **To Manufacturing Domain (Gabe Agent)**
Electronics manufacturability cables:
- PCB fabrication capabilities and constraints
- Assembly process requirements
- Test access and probe points
- Quality control and inspection requirements

## Metacognitive System-Level Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**When to recognize you need system-level analysis:**
- Component changes affect multiple cable systems simultaneously
- Signal quality degrades despite meeting individual design rules
- Power delivery issues appear unrelated to local decoupling
- EMI problems emerge during integration testing
- Thermal hotspots appear in unexpected locations

**System Failure Mode Analysis:**
```
FAILURE MODE: Ground bounce on digital circuits
CABLE ANALYSIS:
- Signal Integrity Cable: High-speed switching creates transient currents
- Power Integrity Cable: Inadequate PDN impedance allows voltage droop  
- Reference Cable: Ground plane discontinuities create impedance
- Thermal Cable: Power loss from inefficient switching compounds problem
SOLUTION: Simultaneous SI/PI/thermal optimization required
```

---

The systems approach recognizes that modern electronics are complex 3D electromagnetic environments where every design decision affects multiple cable networks simultaneously. System-level thinking is essential when component changes, frequency increases, or power levels create interactions that transcend traditional circuit analysis boundaries.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!