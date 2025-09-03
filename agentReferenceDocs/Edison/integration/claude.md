# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Edison Integration - Cross-Domain Cable Handoffs

## What's in This Folder

This directory focuses on how electronics design creates **dependency cables** that extend into other engineering domains, and how systematic cable handoffs maintain design integrity across agent boundaries.

### Core Documents
- `agent_interfaces.md` - Multi-agent system integration protocols

## When to Read These Files (Just-in-Time Context)

### **Cross-Domain Integration Triggers**
Read `agent_interfaces.md` when:
- Electronic design decisions affect mechanical enclosure requirements
- Power dissipation requires thermal management coordination
- PCB constraints affect 3D printing or manufacturing processes
- Component selections create supply chain or cost implications
- Regulatory requirements (EMC, safety) affect circuit design

## The Electronics Integration Cable Network

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Electronics design never exists in isolation - every circuit creates **cables** that extend into other domains:

### **The Thermal Integration Cables**
Every electronic component is a thermal cable node:

**Power → Heat Cable Flow:**
```
Edison Analysis: Component power dissipation calculations
↓ [THERMAL_LOAD Cable]
Watt Analysis: Heat flow paths and cooling requirements  
↓ [COOLING_SOLUTION Cable]
Mechanical Design: Enclosure venting, heat sink mounting
↓ [AIRFLOW_PATH Cable] 
Manufacturing: Assembly process thermal considerations
```

**Critical Handoff Data:**
- Component power dissipation (Watts) at maximum operating conditions
- Junction temperature limits and derating curves
- Thermal resistance models (junction-to-ambient)
- Heat sink mounting requirements and thermal interface materials

### **The Electromagnetic Integration Cables** 
Electronics create electromagnetic cables affecting entire system:

**EMI/EMC Cable Network:**
```
Edison Analysis: Switching circuits, clock frequencies, current loops
↓ [EMI_SOURCE Cable]
Hertz Analysis: Radiated emissions, susceptibility, shielding requirements
↓ [SHIELDING_REQUIREMENT Cable]
Mechanical Design: Conductive enclosure, gaskets, cable shielding
↓ [REGULATORY_COMPLIANCE Cable]
Certification: EMC testing and approval processes
```

**Critical Handoff Data:**
- Switching frequencies and harmonics
- Current loop areas and orientations  
- Cable and connector EMI requirements
- Regulatory limits (FCC Part 15, CE marking)

### **The Mechanical Integration Cables**
Electronic components create mechanical constraint cables:

**Component → Mechanical Cable Flow:**
```
Edison Analysis: Component dimensions, connector orientations, heat sink requirements
↓ [MECHANICAL_CONSTRAINT Cable]
DaVinci Design: Enclosure internal layout, component accessibility
↓ [ASSEMBLY_SEQUENCE Cable] 
Brunel Analysis: Structural support for heavy components, vibration isolation
↓ [MECHANICAL_INTEGRITY Cable]
Manufacturing: Assembly processes, test access, serviceability
```

**Critical Handoff Data:**
- Component envelope dimensions with tolerances
- Connector orientations and mating force requirements
- Heat sink mounting loads and thermal interface requirements
- PCB support requirements for large components

### **The Manufacturing Integration Cables**
PCB design creates manufacturing dependency cables:

**Electronics → Manufacturing Cable Network:**
```
Edison Design: PCB layer count, via types, component packages, trace geometries
↓ [PCB_PROCESS Cable]
Gabe Analysis: Manufacturing process capabilities, yield optimization
↓ [ASSEMBLY_CONSTRAINT Cable]
Process Design: Pick-and-place programs, reflow profiles, test fixtures
↓ [QUALITY_CONTROL Cable]
Production: In-circuit testing, functional validation, quality metrics
```

**Critical Handoff Data:**
- PCB fabrication specifications (layer count, materials, finish)
- Component package types and orientations
- Assembly process requirements (reflow profiles, wave solder)
- Test access requirements for quality control

## Integration Complexity Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Level 1: Simple Electronics Integration**
**Metacognitive Trigger:** Basic circuits with standard components
- Minimal cross-domain dependencies
- Standard thermal and mechanical interfaces
- Basic manufacturing requirements

### **Level 2: Moderate Integration Complexity**
**Metacognitive Trigger:** Power management, wireless, or precision analog
- Thermal management becomes critical
- EMC considerations affect mechanical design
- Manufacturing process optimization needed

### **Level 3: Complex System Integration**
**Metacognitive Trigger:** High-power, high-speed, or safety-critical systems
- Full integration methodology required
- Multiple domains tightly coupled
- Advanced manufacturing processes needed

### **Level 4: System-of-Systems Integration**
**Metacognitive Trigger:** Electronics affect product-level architecture
- All integration documents required
- Cross-domain optimization essential
- Regulatory and certification considerations

## Cable Conflict Resolution Protocols

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Thermal-Electronics Cable Conflicts**
**Conflict Example:** High-performance processor requires heat sink, but enclosure height is constrained

**Resolution Process:**
1. **Edison Analysis:** Quantify thermal cable requirements (heat dissipation, junction temperatures)
2. **Negotiation:** Trade-off analysis between performance and mechanical constraints
3. **Alternative Solutions:** Different processor selection, active cooling, thermal spreading
4. **Validation:** Verify thermal performance meets requirements

### **EMC-Mechanical Cable Conflicts**
**Conflict Example:** Shielding requirements conflict with connector accessibility

**Resolution Process:**
1. **Edison/Hertz Analysis:** Quantify EMI cable requirements and regulatory limits
2. **Mechanical Solutions:** Shielded connectors, gaskets, filtered openings
3. **Cost-Benefit Analysis:** EMC compliance costs vs. design complexity
4. **Regulatory Verification:** Ensure final design meets certification requirements

### **Manufacturing-Performance Cable Conflicts**
**Conflict Example:** Optimal PCB design exceeds manufacturing capabilities

**Resolution Process:**
1. **Performance Analysis:** Identify critical vs. non-critical requirements
2. **Manufacturing Constraints:** Define process capability boundaries  
3. **Design Optimization:** Modify design within manufacturing constraints
4. **Performance Verification:** Validate performance still meets requirements

## Agent Cable Handoff Protocols

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Edison → Watt (Thermal) Handoff**
```yaml
thermal_handoff:
  power_sources:
    - component_id: "U1_Processor"
      power_dissipation: 15.5W
      junction_temp_max: 85C
      package_thermal_resistance: 2.1C/W
  heat_flow_paths:
    - thermal_vias: 64x 0.2mm diameter
    - copper_area: 25mm x 25mm ground plane
    - thermal_interface: TIM required
```

### **Edison → Hertz (EMC) Handoff**  
```yaml
emc_handoff:
  emi_sources:
    - switching_frequency: 2.1MHz
      current_amplitude: 500mA
      loop_area: 15mm²
  sensitive_circuits:
    - circuit_type: "Low-noise analog"
      frequency_range: "DC to 100kHz"
      isolation_required: 60dB
```

### **Edison → DaVinci/Brunel (Mechanical) Handoff**
```yaml
mechanical_handoff:
  component_constraints:
    - connector_type: "USB-C"
      orientation: "Edge-mount horizontal"
      insertion_force: 35N maximum
  pcb_support:
    - board_size: "100mm x 80mm x 1.6mm"
    - support_points: 4x M3 mounting holes
    - component_loads: "15N max on any component"
```

### **Edison → Gabe (Manufacturing) Handoff**
```yaml
manufacturing_handoff:
  pcb_requirements:
    - layer_count: 6
    - via_types: ["through-hole", "blind", "buried"]  
    - minimum_trace: "0.1mm width/space"
    - surface_finish: "ENIG"
  assembly_requirements:
    - component_packages: ["0402", "BGA-144", "QFN-32"]
    - reflow_profile: "Lead-free SAC305"
    - test_access: "In-circuit test points required"
```

## Metacognitive Integration Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**When to recognize cross-domain cable integrity issues:**
- Component thermal limits conflict with performance requirements
- EMC compliance requires design changes affecting other domains
- Manufacturing constraints prevent optimal electrical design
- Mechanical integration creates unexpected electrical constraints

**Integration Failure Analysis Protocol:**
```python
def analyze_integration_failure(domain_conflict):
    cable_systems = identify_affected_cables(domain_conflict)
    for cable in cable_systems:
        integrity_status = verify_cable_integrity(cable)
        if integrity_status.failed:
            root_cause = trace_cable_break(cable)
            resolution = generate_cable_repair_strategy(root_cause)
            validate_solution_across_domains(resolution)
```

**Common Integration Cable Failures:**
- **Broken Thermal Cable:** Component overheating due to inadequate heat removal
- **Broken EMC Cable:** Regulatory non-compliance due to inadequate shielding
- **Broken Mechanical Cable:** Component stress due to inadequate support
- **Broken Manufacturing Cable:** Unmanufacturable design due to process limits

---

Integration success requires understanding that electronics design creates dependency cables extending throughout the entire product system. Managing these cables through systematic handoff protocols ensures that electrical performance, thermal management, mechanical integrity, and manufacturing feasibility are optimized simultaneously rather than in conflict.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!