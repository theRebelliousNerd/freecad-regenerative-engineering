# Physical Products & Enclosure Design Interrogation

## Domain-Specific Focus

Physical product design, especially enclosures and mechanical assemblies, requires specialized interrogation techniques to prevent the most common and expensive failures: dimensional interference, assembly impossibility, and thermal problems.

## The Physical Product Disaster Catalog

Learn from these real-world failures that proper interrogation would have prevented:

### Disaster 1: The 75mm Enclosure Impossibility (Real Project)
**Initial User Statement**: "I need a 75mm tall enclosure"
**Reality Discovered**: Component stack required 78mm minimum
**Cost of Failure**: Complete redesign, 3-week delay, $8,000 in lost time
**Prevention**: Systematic dimensional interrogation with stack-up analysis

### Disaster 2: The Assembly Tool Access Crisis
**Initial User Statement**: "Components mount with M3 screws"
**Reality Discovered**: Screwdriver couldn't reach screws with components installed
**Cost of Failure**: Assembly sequence redesign, custom tools required
**Prevention**: Tool access workflow interrogation

### Disaster 3: The Thermal Runaway Surprise  
**Initial User Statement**: "It has some electronics inside"
**Reality Discovered**: 25W heat generation, no cooling plan, 85°C failure
**Cost of Failure**: Emergency redesign with active cooling, certification delays
**Prevention**: Power dissipation and thermal interrogation

## Specialized Interrogation Protocols for Physical Products

### Phase 1: Component Reality Check (MANDATORY)

This phase is absolutely critical for enclosure design and must be completed before ANY design work begins.

#### The Component Verification Protocol
```
STEP 1: Component Inventory
User: "I have a PCB and some other components"
Interrogator: "Show me photos of EVERY physical component that will go inside"
- Demand actual photos, not drawings or schematics
- Identify each component by specific part number
- Note any components not yet available

STEP 2: Dimensional Verification  
For EACH component:
"What are the EXACT dimensions of [component]?"
- Length, width, height with measurement source
- Mounting hole patterns and spacing
- Connector locations and orientations
- Any protruding elements (LEDs, switches, heat sinks)

STEP 3: Measurement Validation
"How were these dimensions determined?"
- Physical measurement with calipers (BEST)
- Manufacturer datasheet with revision number
- Engineering drawing with tolerance callouts
- Estimate (UNACCEPTABLE for critical dimensions)
```

#### Critical Physical Product Questions

**Dimensional Stack-up**:
- "What is the total height when all components are stacked?"
- "Have you calculated worst-case tolerance buildup?"
- "What thermal expansion occurs at maximum operating temperature?"

**Mounting and Fastening**:
- "How does each component physically attach?"
- "What are the mounting hole sizes and patterns?"
- "Are mounting hardware and spacers included in dimension calculations?"

**Cable and Wire Management**:
- "How many wires connect to each component?"
- "What are the wire gauges and minimum bend radii?"
- "How much volume do wire bundles occupy?"
- "Which direction do connectors face and what clearance is needed?"

**Thermal Considerations**:
- "What is the power dissipation of each component?"
- "What are the maximum operating temperatures?"
- "How does heat flow from each component to the environment?"

### Phase 2: Assembly Sequence Validation

Physical products must be assembled by humans with tools - validate this is possible.

#### The Assembly Workflow Deep-Dive
```
STEP 1: Installation Sequence Mapping
"Walk me through installing each component step by step"
- What goes in first, second, third?
- Can later components be installed with earlier ones in place?
- Are there installation dependencies?

STEP 2: Tool Access Analysis
For each fastener:
"What tool is required and how does it access this fastener?"
- Screwdriver type and size
- Socket wrench requirements
- Angle of approach needed
- Clearance space required for tool manipulation

STEP 3: Cable Connection Sequence
"When and how are cables connected?"
- Can connections be made with enclosure assembled?
- Is pre-wiring required before component installation?
- What cable lengths are needed for routing?
```

#### Assembly Impossibility Detection Questions
- "Can you reach all fasteners with standard tools?"
- "What happens if you need to remove component X - can you do it without disturbing Y?"
- "How much working space does the assembler need around each connection point?"
- "Are there any assembly steps that require more than two hands?"

### Phase 3: Environmental & Operating Conditions

Physical products must survive their intended environment.

#### Environmental Interrogation
```
STEP 1: Operating Environment
"Describe the complete operating environment"
- Indoor/outdoor installation
- Temperature range (minimum to maximum)
- Humidity and moisture exposure
- Vibration, shock, or movement
- Chemical exposure or corrosive atmosphere
- UV exposure and weathering

STEP 2: Ingress Protection Requirements
"What can get inside the enclosure and what damage would it cause?"
- Dust and particle ingress
- Water/moisture ingress  
- Insect or small animal ingress
- Required IP rating and test standards

STEP 3: Mechanical Environment
"What mechanical forces will act on this product?"
- Static loads (weight, pressure)
- Dynamic loads (vibration, shock)
- Human interaction forces (switches, connectors)
- Installation and removal forces
```

### Phase 4: Service and Maintenance Reality

Physical products need maintenance - ensure it's humanly possible.

#### Service Access Interrogation  
```
STEP 1: Component Lifecycle Analysis
"Which components will need replacement during the product lifetime?"
- Identify wear items (fuses, filters, batteries)
- Note components with limited lifespans
- Consider upgrade or modification needs

STEP 2: Service Procedure Mapping
For each serviceable component:
"Walk me through replacing this component step by step"
- Access requirements (covers, panels to remove)
- Tools needed for each step
- Working space requirements
- Time estimates for each operation

STEP 3: Diagnostic and Troubleshooting
"How does a technician identify problems?"
- Visual indicators (LEDs, displays)
- Test point locations
- Measurement access requirements
- Documentation and labeling needs
```

## Physical Product Specification Templates

### Component Specification Template
```yaml
component_id: "relay_module_v2"
description: "8-channel relay board"
part_number: "MANUFACTURER-REL8CH-V2"
source_verification: "physical_measurement"
dimensions:
  length: 
    value: 129.2
    unit: "mm"
    uncertainty: 0.3
    measurement_method: "digital_caliper"
  width:
    value: 72.1
    unit: "mm" 
    uncertainty: 0.3
    measurement_method: "digital_caliper"
  height:
    value: 35.2
    unit: "mm"
    uncertainty: 0.2
    measurement_method: "digital_caliper"
mounting:
  method: "4x M3 screws through PCB"
  hole_pattern: "rectangular_120x65mm_centers"
  hardware_included: false
connectors:
  - type: "screw_terminal"
    count: 16
    orientation: "top_facing"
    clearance_required: "25mm_above"
thermal:
  max_dissipation: "8W_all_relays_active"
  operating_temp_max: "85C"
verification_status: "measured_and_verified"
```

### Assembly Step Template  
```yaml
assembly_step: 3
description: "Install relay module"
prerequisites: 
  - "DIN rail mounted"
  - "Terminal block installed"
tools_required:
  - "M3x0.5 Phillips screws (4)"
  - "Phillips screwdriver size PH1"
procedure:
  1. "Place relay module on mounting bosses"
  2. "Align mounting holes with bosses"  
  3. "Insert and hand-tighten 4x M3 screws"
  4. "Verify module is flush and secure"
clearances_verified:
  - "15mm clearance above for screwdriver"
  - "5mm clearance on sides for alignment"
estimated_time: "3 minutes"
failure_modes:
  - "Mounting holes misaligned - check boss positions"
  - "Screw binding - verify thread engagement"
```

## Red Flags Specific to Physical Products

### Dimensional Red Flags
- "About 80mm" → GET EXACT MEASUREMENT
- "Standard PCB size" → WHICH STANDARD? MEASURED HOW?
- "Fits in a small box" → DEFINE SMALL WITH NUMBERS
- "Component datasheet says X" → VERIFY WITH PHYSICAL MEASUREMENT

### Assembly Red Flags  
- "Just bolt it together" → MAP COMPLETE ASSEMBLY SEQUENCE
- "Standard screws" → SPECIFY SIZE, LENGTH, THREAD PITCH
- "Easy access for service" → DEFINE TOOL REQUIREMENTS AND CLEARANCES
- "Snap-fit assembly" → CALCULATE FORCES AND DEFLECTIONS

### Thermal Red Flags
- "Shouldn't get too hot" → CALCULATE POWER DISSIPATION
- "Natural convection should work" → VERIFY WITH THERMAL ANALYSIS
- "Electronics don't generate much heat" → MEASURE OR CALCULATE WATTS
- "Add some holes for airflow" → CALCULATE REQUIRED FREE AREA

### Environmental Red Flags
- "Normal indoor use" → DEFINE TEMPERATURE AND HUMIDITY RANGES
- "Weatherproof" → SPECIFY IP RATING AND TEST STANDARDS
- "Rugged construction" → QUANTIFY SHOCK AND VIBRATION REQUIREMENTS
- "Food safe materials" → IDENTIFY REGULATORY REQUIREMENTS

## Success Metrics for Physical Product Interrogation

Complete success means:

1. **Every Component Verified**: Physical measurements or verified datasheets
2. **Assembly Sequence Proven**: Step-by-step procedures with tool access verified
3. **Thermal Analysis Complete**: All heat sources calculated, cooling designed
4. **Environmental Specs Defined**: Complete operating condition ranges
5. **Service Procedures Documented**: Maintenance workflows with time estimates
6. **No Geometric Impossibilities**: Dimensional stack-ups proven feasible
7. **Manufacturing Readiness**: All specifications sufficient for production

## Integration with Agent Orchestration

Physical product interrogation provides critical inputs to:

- **Archimedes**: Verified dimensional data for mathematical axioms
- **Curie**: Thermal requirements for material selection
- **Gabe**: Manufacturing constraints and assembly requirements
- **Brunel**: Structural loading and stress analysis requirements
- **Vitruvius**: Service access and human factors requirements

The physical product interrogation is the foundation upon which all subsequent engineering analysis is built. Without this foundation, expensive failures are inevitable.