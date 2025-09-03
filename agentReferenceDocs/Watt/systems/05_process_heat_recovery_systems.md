# Process Heat Recovery Systems

*"Waste heat is not waste - it is an untapped energy resource waiting for systematic recovery."* - Industrial efficiency principles

## Executive Summary

Process heat recovery systems capture waste thermal energy from industrial processes and repurpose it for useful functions, significantly improving overall energy efficiency. The Watt Agent approaches heat recovery as a systematic optimization challenge, using pinch analysis to identify maximum recovery potential and selecting appropriate technologies to convert thermal waste into valuable energy streams.

## Fundamentals of Waste Heat Recovery

### Waste Heat Categories by Temperature

**High-Temperature Waste Heat (> 650°C):**
- **Sources:** Furnace exhausts, kiln gases, combustion products
- **Applications:** Direct process heating, high-pressure steam generation
- **Technologies:** Recuperators, waste heat boilers, preheaters

**Medium-Temperature Waste Heat (230°C - 650°C):**
- **Sources:** Engine exhausts, turbine exhausts, process cooling
- **Applications:** Steam generation, combustion air preheating
- **Technologies:** Heat exchangers, economizers, regenerators

**Low-Temperature Waste Heat (< 230°C):**
- **Sources:** Cooling water, condensate, low-grade process streams  
- **Applications:** Space heating, domestic hot water, power generation
- **Technologies:** Heat pumps, ORC systems, absorption chillers

### Heat Recovery Potential Assessment

**Available Heat Calculation:**
```
Q_available = ṁ × cp × (T_hot - T_ambient)
```

**Maximum Theoretical Recovery:**
```
Q_max = ṁ × cp × (T_hot - T_sink)
```

**Practical Recovery (considering approach temperatures):**
```
Q_practical = ṁ × cp × (T_hot - T_sink - ΔT_min)
```

**Recovery Efficiency:**
```
η_recovery = Q_recovered / Q_available
```

## Pinch Analysis for Heat Integration

### Pinch Technology Methodology

**Step 1: Data Extraction**
- Identify all hot and cold process streams
- Determine supply and target temperatures
- Calculate heat capacity flow rates (ṁ × cp)

**Step 2: Composite Curve Construction**

**Hot Composite Curve:** Represents all heat sources
```
Temperature interval analysis:
T_interval = [T_supply,hot → T_target,hot]
ΔH_interval = Σ(ṁcp)_hot × ΔT
```

**Cold Composite Curve:** Represents all heat sinks
```
Temperature interval analysis:
T_interval = [T_target,cold → T_supply,cold]  
ΔH_interval = Σ(ṁcp)_cold × ΔT
```

**Step 3: Pinch Point Identification**

The **pinch point** is where hot and cold composite curves approach most closely:
```
ΔT_min = T_hot,pinch - T_cold,pinch
```

**Step 4: Energy Targeting**

**Minimum Hot Utility Required:**
```
Q_H,min = Enthalpy difference above pinch point
```

**Minimum Cold Utility Required:**
```
Q_C,min = Enthalpy difference below pinch point
```

**Maximum Heat Recovery:**
```
Q_recovery,max = Q_total_hot - Q_H,min = Q_total_cold - Q_C,min
```

### Pinch Design Rules

**Above Pinch:** Only hot utilities allowed
**Below Pinch:** Only cold utilities allowed
**Across Pinch:** No heat transfer allowed

**Heat Exchanger Network Synthesis:**
1. Start heat exchange at pinch point
2. Match streams with appropriate temperature differences
3. Use stream splitting to achieve feasible matches
4. Minimize number of heat exchanger units

### Grand Composite Curve

The Grand Composite Curve plots net heat availability vs. temperature:
- Positive values indicate heat surplus (available for recovery)
- Negative values indicate heat deficit (requires heating)
- Identifies optimal placement of utilities and heat pumps

## Heat Recovery Technologies

### Direct Heat Exchange Systems

**Recuperators (Gas-to-Gas):**
```
Effectiveness: ε = (T_hot,in - T_hot,out)/(T_hot,in - T_cold,in)
```

**Types:**
- **Tubular:** Simple, robust, moderate effectiveness (50-70%)
- **Plate:** Compact, high effectiveness (70-90%), higher pressure drop
- **Regenerative:** Rotating wheel, very high effectiveness (85-95%)

**Design Considerations:**
- Fouling and corrosion in exhaust streams  
- Thermal expansion and stress analysis
- Bypass dampers for temperature control

**Applications:**
- Furnace exhaust to combustion air preheating
- Process exhaust to fresh air heating
- Flue gas to boiler feedwater heating

### Waste Heat Boilers

**Fire-Tube Design:**
```
Heat Transfer: Q = U × A × LMTD
Overall U-value: 15-40 W/m²·K
```

**Water-Tube Design:**
```
Higher pressure capability: up to 100 bar
Better thermal efficiency: 85-90%
```

**Steam Generation Rate:**
```
ṁ_steam = Q_waste / (h_steam - h_feedwater)
```

**Economic Analysis:**
```
Steam Value = ṁ_steam × h_fg × Hours_operation × Steam_cost
```

### Organic Rankine Cycle (ORC) Systems

**Working Principle:**
Uses organic working fluid with lower boiling point than water, enabling power generation from low-temperature heat sources.

**Thermodynamic Cycle:**
1. **Evaporation:** Working fluid vaporized by waste heat
2. **Expansion:** Vapor expands through turbine to generate power  
3. **Condensation:** Vapor condensed by cooling water/air
4. **Pumping:** Liquid pumped back to evaporator pressure

**Working Fluid Selection Criteria:**
- **Critical temperature** above heat source temperature
- **Low freezing point** for reliable operation
- **Chemical stability** at operating conditions
- **Environmental acceptability** (low ODP, low GWP)

**Common Working Fluids:**
- **R245fa:** Medium temperature applications (80-150°C)
- **R1234ze:** Low GWP alternative to R245fa
- **Toluene:** High temperature applications (>200°C)
- **Silicone oils:** Very high temperature applications

**ORC Efficiency:**
```
η_ORC = W_net / Q_heat_input
```
Typical values: 8-15% for low-temperature sources

**Economic Feasibility:**
```
Simple Payback = Capital_cost / (Power_generated × Hours × Electricity_price)
```

### Heat Pump Integration

**Heat pump integration elevates low-grade waste heat to useful temperature levels:**

**Heat Pump COP:**
```
COP = Q_delivered / W_compressor
```

**Temperature Lift Capability:**
```
COP_Carnot = T_hot / (T_hot - T_cold)
```

**Applications:**
- Upgrade low-temperature process water
- Recover heat from cooling water systems
- Integration with district heating systems

**Design Considerations:**
- Working fluid selection for temperature ranges
- Heat exchanger design for waste heat sources
- Integration with existing process systems

### Thermoelectric Generators (TEGs)

**Seebeck Effect Power Generation:**
```
V = S × ΔT
P = V² / R = S² × ΔT² / R
```

**Efficiency:**
```
η_TEG = (ΔT/T_hot) × [(√(1+ZT) - 1)/(√(1+ZT) + T_cold/T_hot)]
```

**Advantages:**
- No moving parts, silent operation
- Reliable, long lifespan
- Scalable from watts to kilowatts

**Disadvantages:**
- Low efficiency (typically 3-8%)
- High capital cost per kW
- Limited to small-scale applications

## Process Integration Strategies

### Heat Exchanger Network (HEN) Design

**Minimum Number of Heat Exchangers:**
```
N_min = N_streams - 1
```

**Stream Matching Rules:**
1. **Temperature feasibility:** T_hot > T_cold + ΔT_min
2. **Heat balance:** Heat available ≥ Heat required
3. **Stream splitting:** Enables multiple matches per stream

**Heat Exchanger Area Calculation:**
```
A = Q / (U × LMTD)
```

**Capital Cost Estimation:**
```
Cost = a + b × A^c
```
where a, b, c are cost coefficients for exchanger type

### Energy Storage Integration

**Thermal Energy Storage (TES) Benefits:**
- **Time shifting:** Store waste heat during production, use during downtime
- **Load balancing:** Smooth out fluctuations in waste heat availability
- **Process decoupling:** Separate waste heat generation from utilization

**TES Technologies:**

**Sensible Heat Storage:**
```
Q_stored = m × cp × ΔT
```
- **Water tanks:** 4.2 MJ/m³·K storage density
- **Packed bed:** Rock/ceramic media, 1.5-2.5 MJ/m³·K
- **Molten salt:** High temperature capability (>500°C)

**Latent Heat Storage (PCM):**
```
Q_stored = m × h_fusion
```
- **Paraffin wax:** 200 MJ/m³ (phase change 20-60°C)
- **Salt hydrates:** 300-400 MJ/m³ (various temperatures)
- **Metallic PCM:** >1000 MJ/m³ (high temperature)

**Thermochemical Storage:**
```
Q_stored = m × Δh_reaction
```
- **Ca(OH)₂/CaO + H₂O:** 1200 MJ/m³ theoretical
- **Zeolite + H₂O:** Adsorption/desorption cycle
- **Metal hydrides:** Hydrogen storage with heat effect

## Industrial Applications

### Steel Industry Heat Recovery

**Typical Waste Heat Sources:**
- **Coke oven gas:** 1000-1200°C, 15-25% of total energy
- **Blast furnace gas:** 150-300°C, sensible heat recovery
- **Electric arc furnace:** 800-1200°C exhaust gases

**Recovery Applications:**
- Steam generation for power production
- Hot stove air preheating for blast furnaces
- Slab reheating in rolling mills

**Energy Savings Potential:** 15-30% of total plant energy consumption

### Cement Industry Heat Recovery

**Major Waste Heat Sources:**
- **Kiln exhaust:** 300-400°C, 35% of fuel energy
- **Clinker cooling:** 200-300°C, 15% of fuel energy  
- **Preheater exhaust:** 300-350°C

**WHR Power Plant Integration:**
```
Power Generation Potential = 15-25 kWh/tonne cement
```

**Technology Selection:**
- Steam Rankine cycle for high-temperature sources
- ORC systems for medium-temperature sources

### Chemical Process Industry

**Process Integration Opportunities:**
- Reaction heat recovery from exothermic processes
- Distillation column heat integration
- Utility system optimization

**Pinch Analysis Benefits:**
- Identify energy targets before equipment design
- Minimize utility consumption
- Guide process modification decisions

**Typical Energy Savings:** 20-40% reduction in external utilities

### Data Center Heat Recovery

**Server Heat Generation:**
```
Heat Load = IT Power × (1 + PUE_factor - 1)
```
where PUE is Power Usage Effectiveness

**Recovery Applications:**
- Space heating for adjacent buildings
- Domestic hot water heating  
- Absorption cooling for data center cooling
- District heating network integration

**Technology Considerations:**
- Low-temperature heat source (35-45°C)
- High availability requirements
- Water-side economizers for direct cooling

## Economic Analysis and Optimization

### Techno-Economic Assessment

**Capital Cost Components:**
- Heat exchangers and recovery equipment
- Installation and integration costs  
- Piping, instrumentation, and controls
- Building modifications and utilities

**Operating Cost Benefits:**
- Reduced fuel consumption
- Decreased purchased utilities
- Lower cooling costs
- Reduced emissions costs

**Financial Metrics:**

**Net Present Value (NPV):**
```
NPV = Σ(Cash_flow_t / (1 + discount_rate)^t) - Initial_investment
```

**Internal Rate of Return (IRR):**
Rate where NPV = 0

**Payback Period:**
```
Simple Payback = Capital_cost / Annual_savings
Discounted Payback = Capital_cost / (Annual_savings / discount_rate)
```

### Optimization Strategies

**Multi-Objective Optimization:**
- Minimize capital cost
- Maximize energy recovery
- Minimize complexity and maintenance

**Decision Variables:**
- Heat exchanger areas and configurations
- Working fluid selection for power cycles
- Operating conditions and control strategies

**Constraints:**
- Temperature approach limitations  
- Pressure drop restrictions
- Space and layout constraints
- Safety and environmental regulations

## Implementation and Commissioning

### Project Development Process

**Phase 1: Opportunity Assessment**
- Waste heat source identification and characterization
- Preliminary technical and economic feasibility
- Regulatory and permitting requirements

**Phase 2: Detailed Design**
- Complete pinch analysis and HEN synthesis
- Equipment selection and sizing
- Control system design and integration

**Phase 3: Construction and Installation**
- Equipment procurement and delivery
- Installation coordination with ongoing operations
- Safety and quality control procedures

**Phase 4: Commissioning and Startup**
- System performance verification
- Control system tuning and optimization
- Training and knowledge transfer

### Performance Monitoring

**Key Performance Indicators (KPIs):**
- **Heat recovery rate:** Actual vs. design recovery
- **Energy efficiency improvement:** Overall plant efficiency gain  
- **Equipment availability:** Uptime and reliability metrics
- **Economic performance:** Actual vs. projected savings

**Monitoring System Components:**
- Temperature and flow measurement points
- Energy metering for quantified benefits
- Data acquisition and trending systems
- Automated reporting and analysis

## Quality Assurance for Heat Recovery Systems

### Design Verification Checklist

1. **Waste Heat Characterization**
   - [ ] Complete thermal audit of waste streams
   - [ ] Seasonal and operational variations documented  
   - [ ] Contaminant analysis for equipment selection

2. **Pinch Analysis Validation**
   - [ ] Minimum temperature differences verified
   - [ ] Energy targets established and documented
   - [ ] HEN synthesis follows pinch design rules

3. **Technology Selection**
   - [ ] Appropriate technology for temperature range
   - [ ] Economic optimization completed
   - [ ] Integration with existing systems verified

4. **Performance Guarantees**
   - [ ] Heat recovery rates guaranteed
   - [ ] Equipment reliability specified
   - [ ] Maintenance requirements documented

### Common Implementation Challenges

**Technical Challenges:**
- Fouling and corrosion in waste heat streams
- Variable waste heat availability and quality
- Integration with existing control systems
- Space constraints for new equipment

**Economic Challenges:**
- Long payback periods for low-temperature recovery
- High capital costs for small-scale applications
- Competing priorities for capital allocation
- Uncertain energy price projections

**Operational Challenges:**
- Coordination with production schedules
- Maintenance access and procedures
- Operator training and acceptance
- Regulatory compliance and permitting

Remember: "Every Btu wasted is an opportunity missed." Systematic heat recovery not only improves energy efficiency but also reduces environmental impact and operating costs.

Process heat recovery systems represent one of the most cost-effective approaches to industrial energy efficiency, often providing payback periods of 2-5 years while delivering decades of energy savings.