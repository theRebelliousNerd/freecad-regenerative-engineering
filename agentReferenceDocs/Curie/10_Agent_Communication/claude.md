# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# 10_Agent_Communication - Navigation Guide for Marie Curie Agent

## Directory Purpose
This directory defines how materials science information flows between agents in the engineering swarm. It establishes the protocol cables that ensure material constraints, thermal requirements, and property data propagate correctly across all domains.

## The Inter-Agent Cable Network
Material information creates dependency cables across all agents:
- **To Brunel**: Material properties → structural analysis parameters
- **To Tesla**: Magnetic permeability, conductivity → motor design
- **To Edison**: Dielectric properties, thermal resistance → PCB design  
- **To Gabe**: Processability, surface finish → manufacturing optimization
- **To Watt**: Thermal properties, fluid compatibility → thermal system design
- **To Turing**: Density, friction → kinematic calculations
- **To Carson**: Environmental impact, recyclability → sustainability assessment

## Files in This Directory

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### `interface_specifications.md`
**When to Read**: When coordinating with other agents on material decisions
**Purpose**: Standardized formats for material data exchange
**Key Protocols**:
- Material property data structures
- Thermal analysis result formats
- Manufacturing constraint communication
- Performance requirement propagation

## Just-in-Time Communication Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Scenario: "Provide thermal properties to Watt"
1. IDENTIFY thermal analysis requirements from Watt
2. RETRIEVE temperature-dependent thermal properties
3. FORMAT data with uncertainty bounds
4. INCLUDE manufacturing effects if processed material
5. DOCUMENT assumptions and limitations

### Scenario: "Receive structural loads from Brunel"
1. PARSE load conditions (magnitude, frequency, temperature)
2. TRANSLATE to material property requirements
3. CHECK temperature effects on properties
4. VERIFY material selection still valid
5. FEEDBACK any property limitations

### Scenario: "Coordinate with Gabe on manufacturability"
1. RECEIVE proposed manufacturing process
2. RETRIEVE process-specific material properties
3. IDENTIFY property modifications due to process
4. CALCULATE final component properties
5. VALIDATE thermal/structural performance maintained

## Metacognitive Triggers for Communication

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### High-Priority Information Exchange
- **Material temperature limits**: Critical for all thermal agents
- **Process-dependent properties**: Manufacturing changes material behavior
- **Failure modes and limits**: Safety-critical information
- **Supply chain constraints**: Availability affects design decisions
- **Regulatory requirements**: Compliance affects material selection

### Information Quality Indicators
- **High confidence**: Measured data, certified properties
- **Medium confidence**: Handbook values, supplier data
- **Low confidence**: Estimated, extrapolated, or calculated
- **Uncertain**: Conflicting sources, untested conditions
- **Unknown**: Property not available, needs testing

## Communication Protocols by Agent

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### With Brunel (Structural Engineer)
**Curie Provides:**
- Mechanical properties (E, σy, σu, ν, ρ)
- Temperature effects on properties
- Fatigue and creep data
- Failure modes and criteria
- Safety factors for material uncertainty

**Curie Receives:**
- Load conditions (static, dynamic, fatigue)
- Operating temperature range
- Safety requirements
- Geometric constraints
- Stress concentration factors

### With Tesla (Electric Motor Designer)
**Curie Provides:**
- Magnetic properties (μr, coercivity)
- Electrical conductivity and resistivity
- Thermal properties for heat dissipation
- Insulation breakdown voltages
- Core loss characteristics

**Curie Receives:**
- Magnetic field strength requirements
- Current density limitations
- Operating frequency
- Temperature rise predictions
- Efficiency targets

### With Edison (Electronics Designer)
**Curie Provides:**
- Dielectric properties (εr, tan δ)
- Thermal interface material properties
- Coefficient of thermal expansion
- Glass transition temperatures
- Flame retardancy ratings

**Curie Receives:**
- Heat generation maps
- Component operating temperatures
- Signal frequency requirements
- EMI shielding needs
- Reliability targets

### With Gabe (Manufacturing Optimizer)
**Curie Provides:**
- Processing temperature windows
- Material flow properties
- Shrinkage and warpage data
- Layer adhesion characteristics
- Post-processing requirements

**Curie Receives:**
- Manufacturing process selection
- Process parameter ranges
- Quality control requirements
- Production volume targets
- Cost constraints

## Data Exchange Standards

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Material Property Format
```json
{
  "material_id": "string",
  "property_name": "string",
  "value": number,
  "unit": "string",
  "temperature": number,
  "uncertainty": number,
  "confidence_level": "high|medium|low",
  "source": "string",
  "test_method": "string",
  "date_validated": "ISO8601",
  "notes": "string"
}
```

### Thermal Analysis Result Format
```json
{
  "analysis_id": "string",
  "component_temperatures": {
    "location": "string",
    "temperature": number,
    "unit": "celsius"
  },
  "heat_flow_paths": [
    {
      "from": "string",
      "to": "string", 
      "thermal_resistance": number,
      "power_flow": number
    }
  ],
  "hot_spots": [
    {
      "location": "string",
      "temperature": number,
      "risk_level": "high|medium|low"
    }
  ]
}
```

## Network Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream Communication (Curie Receives)
- Design requirements from Requirements Interrogator
- Geometric constraints from DaVinci
- Load conditions from Brunel
- Thermal generation from Edison/Tesla
- Manufacturing process from Gabe
- Environmental conditions from Carson

### Downstream Communication (Curie Provides)
- Material properties to all agents
- Thermal analysis results
- Manufacturing compatibility
- Performance limitations
- Cost implications
- Sustainability metrics

## Quick Communication Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```
Need to Communicate Material Info?
├─ What type of information?
│   ├─ Properties → Use standardized property format
│   ├─ Analysis results → Include methodology and assumptions
│   ├─ Constraints → Clearly state limits and consequences
│   └─ Recommendations → Provide rationale and alternatives
├─ What's the urgency?
│   ├─ Critical → Immediate priority communication
│   ├─ Important → Include in next design iteration
│   └─ Information → Document for future reference
├─ What's the confidence level?
│   ├─ High → Proceed with confidence
│   ├─ Medium → Flag uncertainty, recommend validation
│   └─ Low → Clearly state limitations, suggest testing
└─ Who needs this information?
    ├─ All agents → Broadcast critical constraints
    ├─ Specific agent → Direct targeted communication
    └─ Documentation → Update shared knowledge base
```

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow The Cable
Material properties create information cables:
- Thermal conductivity value → thermal analysis accuracy → design confidence
- Manufacturing process → property modification → performance change
- Cost constraint → material selection → design optimization requirement
- Temperature limit → operating envelope → safety margin

### Just-in-Time Context
Progressive information sharing:
1. Share critical constraints immediately
2. Provide detailed properties when needed for analysis
3. Include uncertainty information for important decisions
4. Full documentation for critical design reviews
5. Validation data only when required for certification

## Communication Quality Assurance

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Information Verification
- Cross-check property values with multiple sources
- Validate units and temperature ranges
- Confirm test method applicability
- Verify manufacturing process effects
- Document any assumptions made

### Uncertainty Propagation
- Include confidence bounds on all values
- Propagate uncertainty through calculations
- Flag high-uncertainty decisions for validation
- Recommend additional testing when needed
- Document sensitivity to uncertain parameters

## Common Communication Pitfalls

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


1. **Units confusion**: Always specify and verify units
2. **Temperature dependence**: Room temp values for high-temp application
3. **Manufacturing effects**: Bulk properties vs. processed
4. **Statistical representation**: Mean vs. minimum vs. characteristic
5. **Applicability limits**: Using data outside validated range
6. **Uncertainty underestimation**: Overconfidence in property values
7. **Context loss**: Property value without application context

## Documentation Standards

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


All inter-agent communication should include:
- Clear identification of sender and receiver
- Timestamp and version control
- Property values with units and uncertainties
- Source of information and validation level
- Assumptions and limitations
- Impact on receiving agent's analysis
- Required actions or responses

## Cross-References

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **01_Foundations**: Communication methodology basis
- **02_MaterialProperties**: Data sources for communication
- **09_FreeCAD_Integration**: CAD system data exchange
- **All other directories**: Domain-specific communication needs

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!