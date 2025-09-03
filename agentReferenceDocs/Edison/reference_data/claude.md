# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Edison Reference Data - Just-in-Time Component Knowledge

## What's in This Folder

This directory contains reference databases and lookup tables for electronics design, organized for **Just-in-Time Context (JITC)** retrieval based on circuit complexity and dependency cascades.

### Core Documents
- `component_database.md` - Systematic component classification and selection data

## When to Read These Files (Just-in-Time Context)

### **Component Selection Uncertainty Triggers**
Read `component_database.md` when:
- Multiple components meet electrical specs but have different dependency profiles
- Component availability affects design schedule or cost targets  
- Parameter tolerance stack-up analysis needed
- Cross-domain impacts (thermal, mechanical, manufacturing) need evaluation
- Supply chain risk mitigation requires alternative component analysis

## The Component Dependency Database Structure

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Component Cable Mapping**
Every component creates multiple dependency cables that must be tracked:

**Electrical Performance Cables:**
- Voltage/current ratings define power delivery requirements
- Frequency response affects system bandwidth and signal integrity
- Input/output impedances affect interface design
- Noise characteristics couple to sensitive system nodes

**Thermal Dependency Cables:**
- Power dissipation creates heat flow requirements
- Junction temperature limits define operating boundaries
- Thermal resistance models affect cooling system design
- Package thermal properties determine heat spreading

**Mechanical Interface Cables:**
- Package dimensions affect PCB routing density and enclosure design
- Pin pitch determines PCB manufacturing requirements
- Mounting requirements affect mechanical support systems
- Orientation constraints affect assembly processes

**Supply Chain Dependency Cables:**
- Availability affects production scheduling
- Lead times affect inventory management
- Cost variations affect product economics
- Alternative sources affect design validation requirements

## Circuit Complexity-Based Data Retrieval

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Level 1: Basic Passive Components (R, L, C)**
**Metacognitive Trigger:** Standard values, minimal system interaction
**Retrieve:** Basic electrical parameters, standard package options
**Dependency Analysis:** Minimal - focus on electrical matching

### **Level 2: Active Components (Op-amps, Regulators)**
**Metacognitive Trigger:** Performance specifications affect system behavior
**Retrieve:** Detailed electrical specs, thermal characteristics, package thermal data
**Dependency Analysis:** Thermal and supply chain considerations

### **Level 3: Complex ICs (Microprocessors, FPGAs, Power Management)**
**Metacognitive Trigger:** Component choice affects entire system architecture
**Retrieve:** Complete component profile including all dependency cables
**Dependency Analysis:** Full multi-domain impact assessment required

### **Level 4: System-Critical Components (Safety, RF, Precision Analog)**
**Metacognitive Trigger:** Component failure affects product functionality or compliance
**Retrieve:** Comprehensive reliability data, qualification standards, supply chain diversity
**Dependency Analysis:** Risk assessment across all domains

## Component Database Schema

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Electrical Parameter Cables**
```yaml
electrical_cables:
  power_delivery:
    voltage_range: {min: 3.0V, max: 5.5V, nominal: 3.3V}
    current_capability: {continuous: 500mA, peak: 1A, surge_duration: 100ms}
    efficiency: {typical: 85%, load_range: "10% to 90%"}
  
  signal_integrity:
    bandwidth: {-3dB: 100MHz, slew_rate: "10V/µs"}
    input_impedance: {typical: 1MΩ, frequency: "DC to 1kHz"}
    noise: {input_referred: "10nV/√Hz at 1kHz"}
```

### **Thermal Dependency Cables**
```yaml
thermal_cables:
  power_dissipation:
    quiescent: 50mW
    active: {typical: 250mW, maximum: 400mW}
    conditions: "At 25°C ambient, typical load"
  
  thermal_limits:
    junction_temp_max: 150C
    operating_range: {min: -40C, max: 85C}
    storage_range: {min: -55C, max: 150C}
  
  thermal_resistance:
    junction_to_ambient: {no_airflow: "45°C/W", with_heatsink: "15°C/W"}
    junction_to_case: "8°C/W"
    case_to_ambient: "37°C/W"
```

### **Mechanical Interface Cables**
```yaml
mechanical_cables:
  package:
    type: "QFN-32"
    dimensions: {length: 5.0mm, width: 5.0mm, height: 0.9mm}
    pitch: 0.5mm
    thermal_pad: {size: "3.2mm x 3.2mm", connection: "required"}
  
  mounting:
    orientation: "any"
    keep_out: {top: 1.0mm, sides: 0.5mm}
    assembly_force: {insertion: "N/A", extraction: "N/A"}
```

### **Supply Chain Dependency Cables**
```yaml
supply_chain_cables:
  availability:
    primary_source: {vendor: "TI", part_number: "TPS54331", availability: "active"}
    secondary_sources: ["Analog Devices AD9544", "Linear LTC3406"]
    lead_time: {sample: "2 weeks", production: "12 weeks"}
  
  cost:
    unit_cost: {qty_1k: "$2.50", qty_10k: "$1.85", qty_100k: "$1.45"}
    price_stability: "high"  # high/medium/low based on market conditions
    
  lifecycle:
    introduction_date: "2018-03-15"
    lifecycle_stage: "mature"  # new/growth/mature/declining/obsolete
    estimated_eol: "2030+"
```

## Context Utility Score (CUS) for Component Data

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Retrieval Decision Model**
Following the JITC framework, component data retrieval follows economic principles:

**Benefits:**
- **Relevance (R):** How well component addresses current design requirements
- **Freshness (F):** How current the component data is (pricing, availability)  
- **Credibility (C):** Source reliability (manufacturer datasheet vs. third-party)
- **Value (V):** Impact on resolving current design uncertainty

**Costs:**
- **Token Cost (T):** Cognitive load of processing component data
- **Latency Cost (L):** Time to retrieve and analyze data
- **Processing Cost (P):** Effort required to integrate data into design

### **Adaptive Retrieval Thresholds**

**Design Phase Adaptivity:**
- **Concept Phase:** Low threshold - explore many options broadly
- **Detail Phase:** Medium threshold - focus on promising candidates
- **Validation Phase:** High threshold - only retrieve critical missing data
- **Production Phase:** Very high threshold - only retrieve for critical issues

**Component Criticality Adaptivity:**
- **Non-critical components:** High threshold - basic specs sufficient
- **Performance-critical:** Medium threshold - detailed characterization needed
- **Safety-critical:** Low threshold - comprehensive data required
- **Single-source:** Very low threshold - all data needed for risk assessment

## Metacognitive Component Selection Triggers

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Uncertainty Recognition Signals**
**When component data retrieval is needed:**
- Performance margins are unclear with current data
- Thermal analysis shows potential junction temperature issues
- Supply chain risks threaten production schedule
- Cost analysis shows component is major cost driver
- Alternative components needed due to availability issues

### **Multi-Domain Cascade Detection**
**Component change impact analysis:**
```python
def assess_component_change_impact(old_component, new_component):
    impact_domains = []
    
    if power_dissipation_changed():
        impact_domains.append("thermal_management")
        trigger_watt_agent_consultation()
    
    if package_changed():
        impact_domains.append("mechanical_design") 
        trigger_davinci_agent_consultation()
        
    if frequency_response_changed():
        impact_domains.append("signal_integrity")
        trigger_high_speed_design_review()
        
    if cost_changed():
        impact_domains.append("product_economics")
        trigger_requirements_interrogator()
    
    return impact_domains
```

### **Component Database Update Protocol**
**Continuous database improvement:**
- Document component performance vs. datasheet specifications
- Track supply chain changes and their impact on designs
- Record cross-domain dependencies discovered during integration
- Build predictive models for component lifecycle and availability

## Integration with Other Agent Domains

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Thermal Integration (Watt Agent)**
Component thermal models flow to thermal analysis:
- Power dissipation maps for thermal simulation
- Junction temperature limits for cooling system design
- Thermal resistance models for heat spreading analysis

### **Mechanical Integration (DaVinci/Brunel Agents)**
Component mechanical data affects enclosure design:
- Package dimensions and orientations
- Heat sink and cooling requirements  
- Assembly access and serviceability

### **Manufacturing Integration (Gabe Agent)**
Component package data affects manufacturing:
- PCB land pattern requirements
- Assembly process compatibility
- Test and inspection access

---

The reference data system recognizes that component selection creates cascading dependencies across multiple domains. Just-in-Time retrieval ensures that the right level of detail is accessed when uncertainty triggers indicate it's needed, while managing cognitive load and decision-making efficiency.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!