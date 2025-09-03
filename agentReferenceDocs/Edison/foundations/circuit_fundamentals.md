# Circuit Fundamentals - Edison Knowledge Base Foundation

## Passive Components - The Universal Building Blocks

### Resistors - Current Flow Impedance
- **Function**: Impede current flow according to Ohm's Law (V = IR)
- **Power Rating**: Must be derated to 50% of maximum rating
- **Temperature Coefficient**: Critical for precision circuits
- **Tolerance**: ±1% for precision, ±5% for general use
- **Package Selection**: 0402, 0603, 0805, 1206 for SMD; through-hole for high power

### Capacitors - Voltage Change Opposition
- **Function**: Store charge in electric field, resist voltage changes
- **Dielectric Types**:
  - Ceramic (X7R, C0G) - stable, low loss
  - Electrolytic - high capacitance, polarized
  - Tantalum - stable, compact, higher cost
- **Voltage Derating**: Minimum 2x working voltage for reliability
- **ESR Considerations**: Critical for power supply decoupling

### Inductors - Current Change Opposition
- **Function**: Store energy in magnetic field, resist current changes
- **Core Materials**:
  - Air core - no saturation, linear
  - Ferrite core - high permeability, frequency dependent
  - Iron powder - distributed gap, high current
- **Saturation Current**: Critical design parameter
- **Self-Resonant Frequency**: Limits high-frequency operation

## Active Components - Amplification and Control

### Diodes - One-Way Current Gates
- **Silicon**: 0.7V forward drop, general purpose
- **Schottky**: 0.3V forward drop, fast recovery
- **Zener**: Voltage regulation, avalanche breakdown
- **TVS**: Transient voltage suppression, clamping

### Transistors - Current Amplification
- **BJT (Bipolar Junction Transistor)**:
  - Current controlled current source
  - Beta (hFE) defines current gain
  - Saturation voltage critical for switching
- **MOSFET (Metal-Oxide-Semiconductor FET)**:
  - Voltage controlled current source
  - Gate threshold voltage (Vth)
  - On-resistance (RDS-on) for switching efficiency

### Operational Amplifiers - Precision Amplification
- **Key Parameters**:
  - Input offset voltage
  - Slew rate
  - Gain-bandwidth product
  - Common-mode rejection ratio (CMRR)
- **Stability**: Compensation for unity-gain operation
- **Power Supply Rejection Ratio (PSRR)**

## Digital Logic Fundamentals

### Logic Families
- **TTL (Transistor-Transistor Logic)**: 5V, high current drive
- **CMOS**: Low power, rail-to-rail operation
- **LVTTL**: 3.3V version of TTL
- **LVCMOS**: 3.3V/2.5V/1.8V CMOS variants

### Sequential Logic Elements
- **Flip-Flops**: State storage elements
- **Counters**: Event counting and frequency division
- **Shift Registers**: Serial-to-parallel conversion
- **State Machines**: Complex control logic implementation

## Circuit Analysis Theorems

### Kirchhoff's Laws
- **Current Law (KCL)**: Sum of currents entering node = 0
- **Voltage Law (KVL)**: Sum of voltages around closed loop = 0

### Network Theorems
- **Thevenin's Theorem**: Complex network → voltage source + series resistance
- **Norton's Theorem**: Complex network → current source + parallel resistance
- **Superposition**: Response to multiple sources = sum of individual responses
- **Maximum Power Transfer**: Load resistance = source resistance for maximum power

## Mixed-Signal Design Principles

### Analog-to-Digital Conversion
- **SAR ADC**: Successive approximation, medium speed, good precision
- **Delta-Sigma ADC**: Oversampling, high resolution, audio applications
- **Pipeline ADC**: High speed, video applications
- **Flash ADC**: Fastest conversion, limited resolution

### Digital-to-Analog Conversion
- **R-2R Ladder**: Simple implementation, moderate accuracy
- **Current Steering**: High speed, good accuracy
- **Delta-Sigma DAC**: High resolution, audio applications

### Phase-Locked Loops (PLLs)
- **Components**: Phase detector, loop filter, VCO, feedback divider
- **Applications**: Clock generation, frequency synthesis, clock recovery
- **Loop Dynamics**: Bandwidth, damping factor, settling time

## Edison's Analysis Protocol

### Systematic Circuit Analysis Steps
1. **Identify topology**: Series, parallel, complex network
2. **Apply appropriate theorem**: KCL/KVL, Thevenin, Superposition
3. **Calculate steady-state response**: DC operating point
4. **Analyze frequency response**: AC small-signal analysis
5. **Verify with simulation**: SPICE validation
6. **Physical implementation considerations**: Parasitics, thermal effects

### Component Selection Hierarchy
1. **Electrical requirements**: Voltage, current, frequency, accuracy
2. **Environmental requirements**: Temperature, humidity, vibration
3. **Reliability requirements**: MTBF, qualification standards
4. **Manufacturing requirements**: Package, assembly method
5. **Supply chain requirements**: Availability, second sources
6. **Cost optimization**: BOM cost, assembly cost

*Remember Edison's principle: "There's a way to do it better - find it" through systematic iteration and validation.*