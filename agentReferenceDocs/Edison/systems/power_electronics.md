# Power Electronics System Design - Edison Power Systems

## Switch-Mode Power Supply (SMPS) Topologies

### Buck Converter (Step-Down)
```
Vin ---[Switch]---[L]--- Vout
         |         |
       [Diode]    [C]---[Load]
         |
        GND
```

#### Key Characteristics
- **Voltage Relationship**: Vout = D × Vin (D = duty cycle)
- **Current Relationship**: Iin = D × Iout (ideal)
- **Efficiency**: 85-95% typical
- **Applications**: Battery-powered devices, voltage regulators

#### Design Equations
- **Inductor Value**: L = (Vin - Vout) × D / (ΔIL × fs)
- **Output Capacitor**: C = ΔIL / (8 × ΔVout × fs)
- **Peak Switch Current**: Ipk = Iout + ΔIL/2

### Boost Converter (Step-Up)
```
Vin ---[L]---[Diode]--- Vout
        |      |
    [Switch]  [C]---[Load]
        |
       GND
```

#### Key Characteristics
- **Voltage Relationship**: Vout = Vin / (1 - D)
- **Current Relationship**: Iin = Iout / (1 - D)
- **Right Half-Plane Zero**: Complicates control loop design
- **Applications**: LED drivers, battery backup, PFC circuits

### Buck-Boost Converter (Inverting)
```
Vin ---[Switch]---[L]---[Diode]--- Vout
         |              |
        GND            [C]---[Load]
                        |
                       GND
```

#### Key Characteristics
- **Voltage Relationship**: Vout = -D × Vin / (1 - D)
- **Output polarity**: Inverted relative to input
- **Continuous input current**: Good for battery applications
- **Applications**: Negative voltage generation, battery systems

### Flyback Converter (Isolated)
```
Vin ---[Switch]---[Primary]   [Secondary]---[Diode]--- Vout
         |                 ))(                |
        GND                                 [C]---[Load]
                                             |
                                            GND
```

#### Key Characteristics
- **Isolation**: Galvanic isolation through transformer
- **Energy Storage**: In transformer magnetizing inductance
- **Multiple Outputs**: Secondary windings for multiple rails
- **Applications**: AC-DC adapters, isolated supplies

## Motor Drive Electronics

### Brushless DC (BLDC) Motor Control

#### Three-Phase Bridge Configuration
```
    +Vbus
      |
  [Q1][Q3][Q5]  <- High-side switches
   |   |   |
   A   B   C     <- Motor phases
   |   |   |
  [Q2][Q4][Q6]  <- Low-side switches
      |
     GND
```

#### Switching Patterns (120° Conduction)
```
Hall Sensor State | Active Switches | Phase Voltages
001              | Q1, Q4          | A+, B0, C-
011              | Q1, Q6          | A+, B-, C0
010              | Q3, Q6          | A0, B+, C-
110              | Q3, Q2          | A-, B+, C0
100              | Q5, Q2          | A-, B0, C+
101              | Q5, Q4          | A0, B-, C+
```

### Field-Oriented Control (FOC)

#### Clarke Transformation (3-phase to 2-phase)
```
Iα = Ia
Iβ = (2*Ib + Ia) / √3
```

#### Park Transformation (2-phase stationary to rotating)
```
Id = Iα*cos(θ) + Iβ*sin(θ)
Iq = -Iα*sin(θ) + Iβ*cos(θ)
```

#### Control Loop Structure
1. **Speed Controller**: PI controller generates Iq reference
2. **Current Controllers**: Separate PI for Id and Iq
3. **Inverse Park/Clarke**: Convert back to 3-phase PWM
4. **Space Vector Modulation**: Optimal PWM generation

### Gate Driver Design

#### High-Side Gate Drive Challenges
- **Level Shifting**: Bootstrap or isolated supply needed
- **Miller Effect**: Gate-drain capacitance causes turn-on issues
- **dV/dt Immunity**: Prevent false turn-on from switching

#### Bootstrap Gate Driver
```
+15V --[Rboot]--[Dboot]-- Bootstrap Cap
                    |
              Gate Driver IC
                    |
                High-Side Gate
```

**Bootstrap Capacitor Sizing**:
```
Cboot = (Qgate + Iqleakage × ton) / ΔVboot
```

### Power MOSFET Selection

#### Key Parameters
- **Drain-Source Voltage (VDS)**: 2x operating voltage minimum
- **Continuous Current (ID)**: With thermal derating
- **On-Resistance (RDS-on)**: Conduction losses
- **Gate Charge (Qg)**: Switching losses
- **Safe Operating Area (SOA)**: Avalanche energy rating

#### Switching Losses
```
Psw = (Eon + Eoff) × fsw + Qg × Vgate × fsw
```

#### Conduction Losses
```
Pcond = I²rms × RDS-on(θj)
```

## Power Factor Correction (PFC)

### Boost PFC Topology
- **Function**: Shape input current to match voltage waveform
- **Control**: Average current mode control typical
- **THD Target**: <5% for compliance with IEC 61000-3-2

### Critical Conduction Mode (CrM)
- **Operation**: Inductor current returns to zero each cycle
- **Advantages**: Zero-current switching, simple control
- **Frequency Variation**: 2:1 variation over line cycle

## Battery Management Systems (BMS)

### Cell Balancing Methods

#### Passive Balancing
```
Cell ---[Balance Resistor]---[Switch]
```
- **Method**: Dissipate excess energy in weak cells
- **Efficiency**: Energy wasted as heat
- **Implementation**: Simple, low cost
- **Applications**: Low-power applications

#### Active Balancing
- **Method**: Transfer energy between cells
- **Topologies**: Flyback, forward converter, capacitive
- **Efficiency**: Energy recycled, not wasted
- **Complexity**: Higher component count and control

### Protection Functions
- **Overvoltage Protection**: Disconnect on cell overvoltage
- **Undervoltage Protection**: Disconnect on cell undervoltage
- **Overcurrent Protection**: Current limiting or disconnect
- **Overtemperature Protection**: Thermal monitoring and shutdown

## Electromagnetic Interference (EMI) in Power Electronics

### EMI Sources
- **Hard Switching**: High dV/dt and dI/dt create broadband noise
- **Parasitic Ringing**: LC resonances in layout parasitics
- **Common-Mode Currents**: Ground loops and coupling

### EMI Mitigation Techniques

#### Circuit Level
- **Soft Switching**: Zero-voltage or zero-current switching
- **Spread Spectrum**: Dither switching frequency
- **Gate Drive Optimization**: Control dV/dt and dI/dt

#### PCB Level
- **Ground Planes**: Minimize loop areas
- **Layer Stack-up**: Interleaved power and ground
- **Component Placement**: Keep switching loops small

#### System Level
- **Input Filters**: Common-mode and differential-mode chokes
- **Shielding**: Faraday cage around switching circuits
- **Cable Routing**: Minimize coupling between circuits

### Filter Design

#### Common-Mode Choke
```
 L_CM = μ0 × μr × A × N² / l
```
- **μ0**: Permeability of free space
- **μr**: Relative permeability of core
- **A**: Cross-sectional area of core
- **N**: Number of turns
- **l**: Magnetic path length

#### Differential-Mode Filter
- **L-C Configuration**: Series inductor, parallel capacitor
- **Corner Frequency**: fc = 1 / (2π√(LC))
- **Damping**: Critical damping prevents ringing

## Thermal Management in Power Electronics

### Heat Sink Design
- **Thermal Resistance**: Rθ = ΔT / P
- **Heat Sink Selection**: Based on Rθsa requirement
- **Interface Materials**: Thermal pads, compounds, gap fillers

### Power Module Thermal Design
- **Junction-to-Case**: Rθjc from datasheet
- **Case-to-Sink**: Rθcs depends on interface
- **Sink-to-Ambient**: Rθsa depends on heat sink

### Cooling Methods
- **Natural Convection**: Simplest, lowest cost
- **Forced Air**: Fans for higher power density
- **Liquid Cooling**: Highest performance, complexity
- **Heat Pipes**: Intermediate solution for hotspots

*Edison's Power Principle: "Electricity is really just organized lightning." Master the fundamentals of energy conversion, and systematic iteration will reveal the optimal topology for each application.*