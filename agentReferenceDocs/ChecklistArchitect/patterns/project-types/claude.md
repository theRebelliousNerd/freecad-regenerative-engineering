# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Project Types Patterns - Domain-Specific Cable Network Architectures

## Overview: Project Types as Network Architecture Templates  
This directory contains proven quality assurance cable network architectures for different categories of engineering projects. Each project type has characteristic requirements, failure modes, and optimal validation strategies that inform standardized network topologies.

## Just-in-Time Context Access
Load project type patterns when:
- **Starting projects** similar to documented types for proven network architectures
- **Adapting validation approaches** from one project type to hybrid/novel projects  
- **Optimizing network topology** based on domain-specific requirements and failure patterns
- **Establishing coordination protocols** between agents based on project type characteristics

## Follow the Cable: Project-Type-Driven Network Design

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Project Type as Network Architecture Driver
Different project types require fundamentally different cable network topologies:
- **Electronics Projects**: Dense integration cables for electromagnetic, thermal, and signal integrity
- **Mechanical Systems**: Structural load path cables with kinematic validation networks
- **Mechatronic Systems**: Hybrid networks spanning mechanical, electrical, and control domains
- **Software Systems**: Logic flow cables with interface validation networks
- **Human Interface Systems**: Safety and ergonomic validation cables with user experience networks

### Network Architecture Mapping by Domain

#### Electronics Enclosure Projects
**Network Characteristics**: High integration density with electromagnetic-thermal coupling
```
Requirements Analysis
    ↓ (component reality cable)
Physical Component Verification (MANDATORY)
    ↓ (dimensional integration cable)
Mechanical Fit Analysis (DaVinci ↔ Archimedes)
    ↓ (electromagnetic integration cable)
EMC Analysis (Tesla ↔ Hertz)
    ↓ (thermal integration cable) 
Thermal Management (Tesla ↔ Watt)
    ↓ (manufacturing integration cable)
Production Feasibility (Gabe)
    ↓ (validation cable)
Performance Testing (Orville)
```

**Critical Cable Requirements**:
- **Foundation**: Component verification must be physical, not estimated
- **Integration**: Tesla↔Watt thermal-electromagnetic coupling essential
- **Manufacturing**: Gabe early involvement for DFM validation
- **Safety**: EMC compliance cables for regulatory requirements

**Common Failure Patterns**: Component Surprise, Thermal Runaway, EMC Issues

#### Motor Control Systems
**Network Characteristics**: Kinematic-electromagnetic-control integration triangle
```
Motion Requirements Definition
    ↓ (kinematic analysis cable)
Motion Analysis (Turing)
    ↓ (electromagnetic specification cable)
Motor Selection/Design (Tesla)
    ↓ (structural integration cable)
Mechanical Integration (Brunel)
    ↓ (control system cable)
Control Electronics (Edison)
    ↓ (system validation cable)
Integrated Testing (Orville)
```

**Critical Cable Requirements**:
- **Kinematic Foundation**: Turing analysis drives all downstream requirements
- **Electromagnetic Integration**: Tesla motor specs must match Turing torque/speed requirements
- **Control Coupling**: Edison control system must coordinate with Tesla and Turing
- **Structural Validation**: Brunel ensures mechanical system handles forces

**Common Failure Patterns**: Torque/Speed Mismatches, Control Instability, Structural Failures

#### IoT/Sensor Devices
**Network Characteristics**: Power-optimized with wireless integration
```
Sensing Requirements
    ↓ (sensor specification cable)
Sensor Selection/Integration
    ↓ (power analysis cable)
Power Budget Analysis (Edison)
    ↓ (wireless integration cable)
Communication System (Hertz)
    ↓ (packaging cable)
Physical Design (DaVinci)
    ↓ (environmental cable)
Environmental Testing (Orville)
```

**Critical Cable Requirements**:
- **Power Budget**: Edison power analysis drives all design decisions
- **Wireless Integration**: Hertz antenna/RF design integrated with mechanical
- **Environmental Resilience**: Robust validation for deployment conditions
- **Manufacturing Scale**: Gabe optimization for volume production

**Common Failure Patterns**: Power Budget Overruns, RF Performance Issues, Environmental Failures

## Domain-Specific Network Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Multi-Physics System Networks

#### Thermal-Electromagnetic Coupling Pattern
**When to Use**: Any project with >5W power consumption in enclosed space
```
Power Analysis (Edison)
    ↓ (thermal handoff cable)
Heat Generation Calculation (Tesla)
    ↓ (thermal management cable)
Cooling/Dissipation Design (Watt)  
    ↓ (electromagnetic feedback cable)
Thermal Impact on Performance (Tesla)
    ↓ (design integration cable)
Mechanical Heat Management (DaVinci)
```

**Network Strength Requirements**:
- **Bidirectional Cables**: Tesla ↔ Watt must be bidirectional feedback
- **Real-Time Integration**: Thermal constraints affect electromagnetic design
- **Manufacturing Integration**: Thermal solutions must be manufacturable (Gabe)

#### Kinematic-Structural Coupling Pattern  
**When to Use**: Any system with motion and significant structural loads
```
Motion Requirements (User)
    ↓ (kinematic analysis cable)
Mechanism Design (Turing)
    ↓ (force analysis cable) 
Force/Torque Calculation (Turing)
    ↓ (structural handoff cable)
Structural Analysis (Brunel)
    ↓ (design feedback cable)
Structural Constraints on Motion (Brunel → Turing)
```

**Network Strength Requirements**:
- **Load Path Verification**: All forces traced through structural elements
- **Dynamic Analysis**: Motion-induced forces verified for all operating conditions
- **Material Selection**: Curie materials analysis integrated with structural requirements

### Human Interface System Networks

#### Ergonomic-Safety Validation Pattern
**When to Use**: Any system with human interaction or safety implications
```
User Requirements Analysis
    ↓ (ergonomic analysis cable)
Human Factors Analysis (Vitruvius)
    ↓ (safety assessment cable)
Safety Hazard Analysis (Vitruvius)
    ↓ (design integration cable)
Safe Design Implementation
    ↓ (validation cable)
Human Testing/Validation (Orville)
```

**Network Strength Requirements**:
- **Safety Priority**: Vitruvius safety requirements override all other considerations
- **User Testing**: Orville validation must include actual human subjects
- **Regulatory Compliance**: Carson regulatory cables for applicable standards

## Network Architecture Selection Algorithm

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Project Type Classification
```python
def classify_project_type(project_characteristics):
    type_indicators = {
        "electronics_enclosure": {
            "components": ["PCB", "electronic", "enclosure"],
            "domains": ["electrical", "thermal", "mechanical"],
            "power_consumption": ">1W"
        },
        "motor_control": {
            "components": ["motor", "drive", "control"],
            "domains": ["kinematic", "electromagnetic", "control"],
            "motion_requirements": True
        },
        "iot_device": {
            "components": ["sensor", "wireless", "battery"],
            "domains": ["electrical", "RF", "power"],
            "connectivity": "wireless"
        },
        "safety_critical": {
            "human_interaction": True,
            "safety_implications": True,
            "regulatory_requirements": True
        }
    }
    
    matches = []
    for project_type, indicators in type_indicators.items():
        if matches_indicators(project_characteristics, indicators):
            matches.append(project_type)
    
    return determine_primary_type(matches)
```

### Network Architecture Selection
```python  
def select_network_architecture(project_type, complexity_level):
    base_network = PROJECT_TYPE_NETWORKS[project_type]
    
    if complexity_level == "simple":
        return simplify_network(base_network)
    elif complexity_level == "complex":
        return enhance_network(base_network)
    elif any(safety_critical_indicators):
        return add_safety_networks(base_network)
    else:
        return base_network
```

## Project-Specific Agent Coordination Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Electronics Project Agent Orchestra
**Primary Agents**: Edison (electrical), Tesla (electromagnetic), Watt (thermal)
**Supporting Agents**: Hertz (EMC), DaVinci (mechanical), Gabe (manufacturing)
**Coordination Pattern**: Dense integration with thermal-electromagnetic coupling priority

### Mechanical Project Agent Orchestra  
**Primary Agents**: Brunel (structural), Turing (kinematic), Curie (materials)
**Supporting Agents**: DaVinci (design), Khan (optimization), Gabe (manufacturing)
**Coordination Pattern**: Load path validation with kinematic-structural coupling priority

### Mechatronic Project Agent Orchestra
**Primary Agents**: Tesla (motors), Edison (control), Turing (kinematics), Brunel (structure)
**Supporting Agents**: All agents with complex integration requirements
**Coordination Pattern**: Multi-physics mesh network with all agent coordination

## Network Adaptation Strategies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Hybrid Project Type Networks
When projects span multiple types, combine network architectures:

#### Electronics + Mechanical Hybrid
```python
def create_hybrid_network(primary_type, secondary_type):
    primary_network = PROJECT_TYPE_NETWORKS[primary_type]
    secondary_network = PROJECT_TYPE_NETWORKS[secondary_type]
    
    return merge_networks(
        primary_network, 
        secondary_network,
        integration_priority="primary_drives_secondary"
    )
```

#### Safety Critical Overlay
Any project type can have safety criticality overlay:
```python
def add_safety_critical_overlay(base_network):
    safety_network = SAFETY_CRITICAL_NETWORK_TEMPLATE
    return overlay_networks(
        base_network,
        safety_network, 
        safety_priority=True
    )
```

## Project Evolution Network Adaptation

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Network Scaling with Project Growth
Projects often evolve beyond initial type classification:

#### Type Escalation Patterns
- **Simple → Complex**: Increase network density and integration cables
- **Single Domain → Multi-Domain**: Add cross-domain integration cables  
- **Standard → Safety Critical**: Add safety validation overlay
- **Prototype → Production**: Add manufacturing and quality cables

#### Network Migration Strategies
```python
def migrate_network_architecture(current_network, new_project_type):
    migration_plan = analyze_network_gaps(current_network, new_project_type)
    
    return {
        "additional_cables": migration_plan.required_additions,
        "enhanced_integrations": migration_plan.strengthened_connections,
        "new_agents": migration_plan.agent_additions,
        "migration_sequence": migration_plan.implementation_order
    }
```

## Practical Application Guidelines

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Project Type Selection Checklist
- [ ] **Primary Domain Identification**: What engineering discipline is central?
- [ ] **Multi-Domain Assessment**: What other disciplines are significantly involved?
- [ ] **Human Interface Assessment**: Any human safety or interaction considerations?
- [ ] **Regulatory Assessment**: Any compliance requirements or standards?
- [ ] **Complexity Assessment**: Simple, moderate, complex, or safety-critical?
- [ ] **Novel Elements**: Any aspects not covered by standard project types?

### Network Architecture Implementation
1. **Select Base Architecture**: Choose primary project type network template
2. **Add Domain Networks**: Include secondary domain networks as needed
3. **Apply Complexity Scaling**: Adjust network density for project complexity
4. **Add Safety Overlays**: Include safety networks if human safety implications
5. **Customize Integration**: Adapt agent coordination for specific project needs

Remember: **Project types provide proven network architecture templates that have been validated through experience. Start with established patterns and adapt them to your specific requirements rather than designing networks from scratch. The goal is to leverage accumulated knowledge while customizing for your unique project characteristics.**

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!