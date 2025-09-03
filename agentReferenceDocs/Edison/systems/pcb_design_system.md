# PCB Design as a System - Edison Systems Knowledge

## The PCB as an Engineered System

*"The PCB is not merely a platform for components but a complex, engineered system."*

### Layer Stack-up Architecture

#### 2-Layer Stack-up (Simple Designs)
```
Top Layer (Signal)
FR-4 Core (1.6mm typical)
Bottom Layer (Signal/Ground)
```
- **Applications**: Simple digital circuits, low-speed analog
- **Limitations**: Poor EMI performance, limited routing density
- **Cost**: Minimum cost option

#### 4-Layer Stack-up (Recommended Minimum)
```
Top Layer (Signal)
Prepreg
Ground Plane (Inner Layer 1)
Core
Power Plane (Inner Layer 2)
Prepreg
Bottom Layer (Signal)
```
- **Benefits**: Controlled impedance, good EMI shielding, return path
- **Applications**: Most digital designs, mixed-signal circuits
- **Stack-up Control**: ±10% impedance tolerance achievable

#### 6-Layer Stack-up (High-Performance)
```
Top Layer (Signal)
Prepreg
Ground Plane (Inner Layer 1)
Core
Signal Layer (Inner Layer 2)
Prepreg
Signal Layer (Inner Layer 3)
Core
Power Plane (Inner Layer 4)
Prepreg
Bottom Layer (Signal)
```
- **Advantages**: Dedicated signal layers, multiple power domains
- **Applications**: High-speed digital, RF circuits, power electronics

### Copper Weight and Thickness Selection

#### Standard Copper Weights
- **0.5 oz/ft²**: 17.5μm (0.7 mil) - Light signals, fine pitch
- **1 oz/ft²**: 35μm (1.4 mil) - Standard signal layers
- **2 oz/ft²**: 70μm (2.8 mil) - Power layers, high current
- **3 oz/ft²**: 105μm (4.2 mil) - Heavy power applications

#### Current Carrying Capacity
```
I = k × (dT^0.44) × (A^0.725)
```
- **I**: Current (Amps)
- **k**: Constant (0.048 internal, 0.024 external traces)
- **dT**: Temperature rise (°C)
- **A**: Cross-sectional area (mil²)

**Rule of Thumb**: 1 mil² carries 1A with 10°C rise (external trace)

## High-Speed Design Principles

### Signal Integrity (SI) Fundamentals

#### Transmission Line Theory
- **When traces become transmission lines**: Length > λ/10
- **Characteristic Impedance (Z0)**:
  ```
  Z0 = √(L/C)
  ```
  - **L**: Inductance per unit length
  - **C**: Capacitance per unit length

#### Microstrip Impedance Calculation
```
Z0 = (87/√(εr+1.41)) × ln(5.98h/(0.8w+t))
```
- **εr**: Dielectric constant of substrate
- **h**: Height above ground plane
- **w**: Trace width
- **t**: Trace thickness

#### Stripline Impedance Calculation
```
Z0 = (60/√εr) × ln(4h/(0.67π(0.8w+t)))
```
- **Advantages**: Better noise immunity, symmetric field
- **Disadvantages**: Harder to access, more layers required

### Differential Pair Design

#### Differential Impedance
```
Zdiff = 2 × Z0 × √(1 - (k^2/2))
```
- **k**: Coupling coefficient between traces
- **Target**: Usually 90Ω, 100Ω, or 120Ω

#### Length Matching Requirements
- **High-Speed Digital**: ±0.1mm for signals >1GHz
- **DDR Memory**: ±0.025mm for data, ±0.1mm for address
- **LVDS**: ±0.1mm within pair, ±5mm between pairs
- **PCIe**: ±0.1mm within pair, tight skew control

### Power Integrity (PI) System Design

#### Power Distribution Network (PDN)
- **Target PDN Impedance**: <1mΩ for digital circuits
- **Decoupling Strategy**:
  - Bulk capacitors: 10-100μF (aluminum electrolytic)
  - Mid-frequency: 1-10μF (ceramic or tantalum)
  - High-frequency: 0.01-0.1μF (ceramic, close to IC)

#### Decoupling Capacitor Placement
- **Distance Rule**: <5mm from power pin for high-frequency caps
- **Via Strategy**: Direct connection to power/ground planes
- **ESL Minimization**: Multiple small capacitors vs. single large

#### Power Plane Design
- **Plane Capacitance**: C = εr × ε0 × A / d
  - **εr**: Dielectric constant (~4.3 for FR-4)
  - **A**: Plane area (m²)
  - **d**: Dielectric thickness (m)
- **Resonance Control**: Avoid resonant frequencies matching switching

## Thermal Management System

### Thermal Via Strategy
- **Via Size**: 0.2-0.3mm diameter optimal for thermal transfer
- **Via Array**: Grid pattern under high-power components
- **Fill Strategy**: Via filling vs. tenting based on assembly process

### Copper Pour Optimization
- **Thermal Spreading**: Large copper areas for heat distribution
- **Thermal Interface**: Direct copper connection to heat sinks
- **Keep-out Zones**: Maintain clearance from sensitive components

### Component Thermal Management
- **Power Density Limits**: <2W/cm² for natural convection
- **Thermal Vias**: 1 via per 1W of power dissipation
- **Heat Sink Mounting**: Mechanical considerations in PCB design

## Routing Strategy System

### Manhattan vs. Diagonal Routing
- **Manhattan**: 0° and 90° only, organized appearance
- **Diagonal**: 45° angles, 29.3% shorter traces, 14ps less delay
- **Mixed Strategy**: Critical nets diagonal, others Manhattan

### Via Optimization
- **Via Types**: Through-hole, blind, buried, micro-vias
- **Via Stitching**: Ground/power plane connections every 5mm
- **Via-in-Pad**: For high-density BGA applications

### Critical Net Routing Priority
1. **Power and Ground**: Shortest, widest paths
2. **Clock Signals**: Star topology, matched lengths
3. **High-Speed Differential**: Tight coupling, length matching
4. **Critical Analog**: Isolation from digital switching
5. **General I/O**: Standard routing rules

## EMC/EMI System Design

### Emission Control
- **Rise/Fall Time**: Slower edges reduce high-frequency content
- **Ground Planes**: Minimize loop areas
- **Shielding**: Continuous ground reference

### Susceptibility Control
- **Filtering**: LC filters on power and signal lines
- **Isolation**: Physical and electrical separation
- **Guard Traces**: Driven at same potential as signal

### PCB-Level EMC Techniques
- **Layer Assignment**: High-speed signals between power/ground
- **Via Stitching**: Connect split planes every λ/20
- **Edge Termination**: 20H rule for plane layer setback

## Manufacturing Interface System

### Design Rule Constraints
- **Minimum Trace Width**: 0.1mm (4 mil) for standard processes
- **Minimum Spacing**: 0.1mm (4 mil) between traces
- **Via Size**: 0.15mm (6 mil) minimum drill, 0.35mm pad
- **Annular Ring**: 0.05mm (2 mil) minimum

### Assembly Considerations
- **Component Orientation**: Consistent for pick-and-place
- **Fiducial Placement**: Global and local references
- **Test Points**: 1.27mm (50 mil) minimum pitch
- **Panel Size**: Multiple board optimization

### Quality Control Integration
- **ICT (In-Circuit Test)**: >95% net coverage target
- **Boundary Scan**: JTAG chain for digital testing
- **Flying Probe**: Alternative to ICT for prototypes
- **AOI (Automated Optical Inspection)**: Placement verification

*Edison's System Principle: "The value of an idea lies in the using of it." Every PCB system element must contribute to the overall functional success and manufacturing excellence.*