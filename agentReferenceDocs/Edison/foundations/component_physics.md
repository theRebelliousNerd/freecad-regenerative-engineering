# Component Physics & Reliability - Edison Foundation Knowledge

## Physical Reality of Electronic Components

### Semiconductor Physics Essentials
- **PN Junction**: Depletion region, built-in potential, forward/reverse bias
- **Temperature Effects**: 
  - Diode forward voltage: -2mV/°C temperature coefficient
  - BJT β increases with temperature
  - MOSFET threshold voltage: -2 to -4mV/°C
- **Avalanche Breakdown**: Electric field exceeds critical value
- **Thermal Runaway**: Positive feedback between current and temperature

### Parasitic Elements - The Hidden Reality

#### Resistor Parasitics
- **Lead Inductance**: ~1nH/mm for wire-wound resistors
- **Distributed Capacitance**: Parallel plates between turns
- **Thermal Coefficient**: PPM/°C specification critical for precision
- **Voltage Coefficient**: Resistance change with applied voltage

#### Capacitor Parasitics
- **Equivalent Series Resistance (ESR)**:
  - Ceramic: 0.01-1Ω depending on size and frequency
  - Electrolytic: 0.1-10Ω, frequency dependent
  - Tantalum: 0.1-1Ω, stable across temperature
- **Equivalent Series Inductance (ESL)**:
  - Package dependent: 0402 ~0.5nH, 1206 ~2nH
  - Limits high-frequency decoupling effectiveness
- **Dielectric Absorption**: "Memory effect" in precision circuits
- **Piezoelectric Effect**: Mechanical stress creates voltage (ceramic capacitors)

#### Inductor Parasitics
- **Distributed Capacitance**: Between wire turns creates self-resonance
- **Core Losses**: Hysteresis and eddy current losses
- **Skin Effect**: Current concentration at conductor surface
- **Proximity Effect**: Current distribution affected by nearby conductors

### Component Reliability Physics

#### Failure Mechanisms
1. **Thermal Cycling**: Coefficient of thermal expansion mismatch
2. **Electromigration**: Metal ion migration under current stress
3. **Corrosion**: Electrochemical reactions in presence of moisture
4. **Mechanical Stress**: Vibration, shock, thermal expansion
5. **Radiation**: Single event effects, total ionizing dose

#### Arrhenius Relationship
```
Failure Rate = A × exp(-Ea/kT)
```
- **A**: Pre-exponential factor
- **Ea**: Activation energy (eV)
- **k**: Boltzmann constant
- **T**: Absolute temperature (K)

**Rule of Thumb**: Every 10°C temperature increase doubles failure rate

#### MTBF Calculation
```
MTBF = 1 / (λbase × πT × πE × πQ × πS)
```
- **λbase**: Base failure rate
- **πT**: Temperature factor
- **πE**: Environment factor
- **πQ**: Quality factor
- **πS**: Stress factor

### Derating Guidelines - Edison's Safety Margins

#### Voltage Derating
- **General Rule**: 80% of maximum rated voltage
- **Critical Applications**: 70% for aerospace, 60% for space
- **Capacitors**: 50% derating recommended for long life
- **Zener Diodes**: 75% of power rating in avalanche mode

#### Current Derating
- **Resistors**: 50% of power rating for general use
- **Inductors**: 80% of saturation current for linear operation
- **Fuses**: 75% of rated current for continuous operation
- **Connectors**: 80% of current rating considering temperature rise

#### Thermal Derating
- **Junction Temperature**: Tj,max - 25°C safety margin
- **Thermal Resistance Calculation**:
  ```
  Tj = Ta + (Rθja × Pd)
  ```
  - **Ta**: Ambient temperature
  - **Rθja**: Thermal resistance junction to ambient
  - **Pd**: Power dissipation

### Component Qualification Standards

#### Military Standards (MIL-STD)
- **MIL-STD-202**: Test methods for electronic components
- **MIL-STD-883**: Microcircuit test methods
- **MIL-STD-1275**: Vehicle electrical system interface
- **MIL-STD-461**: EMI/EMC requirements

#### Automotive Standards (AEC)
- **AEC-Q100**: IC qualification (-40°C to +150°C)
- **AEC-Q101**: Discrete semiconductor qualification
- **AEC-Q200**: Passive component qualification
- **AEC-Q104**: Interface technology qualification

#### Commercial Standards
- **JEDEC**: Semiconductor standards organization
- **IPC**: PCB and assembly standards
- **UL**: Safety standards and certification
- **CE**: European conformity marking

## Edison's Component Selection Methodology

### Phase 1: Functional Requirements
1. **Electrical specifications** with safety margins
2. **Environmental operating conditions**
3. **Reliability targets** (MTBF, qualification level)
4. **Regulatory compliance** requirements

### Phase 2: Parametric Analysis
1. **Performance derating** according to guidelines
2. **Worst-case analysis** across temperature and process
3. **Aging effects** over product lifetime
4. **Supply chain risk** assessment

### Phase 3: Validation Protocol
1. **Simulation verification** with parasitic models
2. **Prototype testing** under stress conditions
3. **Accelerated life testing** for reliability prediction
4. **Second source validation** for supply security

### Component Database Structure
```json
{
  "component_id": "R0603_1K_1%",
  "description": "Resistor 1kΩ ±1% 0603 package",
  "electrical_params": {
    "resistance": "1000Ω",
    "tolerance": "±1%",
    "power_rating": "0.1W",
    "voltage_rating": "75V",
    "temp_coefficient": "±100ppm/°C"
  },
  "physical_params": {
    "package": "0603",
    "dimensions": "1.6×0.8×0.45mm",
    "lead_inductance": "0.6nH",
    "thermal_resistance": "400°C/W"
  },
  "reliability": {
    "qualification": "AEC-Q200",
    "operating_temp": "-55°C to +155°C",
    "failure_rate": "1 FIT at 70°C",
    "mtbf_years": "1000000"
  },
  "supply_chain": {
    "primary_supplier": "Vishay",
    "part_number": "CRCW06031K00FKEA",
    "secondary_sources": ["Yageo", "Panasonic"],
    "availability_status": "Active",
    "lead_time_weeks": "12"
  }
}
```

*Edison's Wisdom: "The value of an idea lies in the using of it." Every component selection must be validated through systematic testing and proven in real-world application.*