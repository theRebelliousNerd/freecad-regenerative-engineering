# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Systems Directory - Complex System Integration Cables

## JITC Framework for Human Factors System Integration

This directory contains knowledge modules for complex system integration, FreeCAD human factors implementation, system-level design validation, and the critical "system cables" that propagate human factors constraints across multiple subsystems and agent domains.

### System-Level Cable Network

Complex systems create hierarchical cable networks where human factors requirements propagate across multiple levels:

1. **Integration Cables** - How human constraints affect system architecture
2. **Scaling Cables** - How human factors propagate from component to system level  
3. **Validation Cables** - Systematic testing of human-system interactions
4. **Interface Cables** - System-to-system human interaction boundaries
5. **Lifecycle Cables** - Human factors across system development phases

### Critical System Cable Dependencies

#### Human-System Boundary Definition
**Cable Sources**: Human capabilities and limitations (physical, cognitive, sensory)
**Cable Destinations**: System functional requirements, interface specifications, safety margins

**System Integration Points**:
```python
human_system_boundaries = {
    'information_input': {
        'visual_channel': 'display_specifications', 
        'auditory_channel': 'alarm_audio_requirements',
        'tactile_channel': 'haptic_feedback_design'
    },
    'control_output': {
        'manual_control': 'interface_force_limits',
        'cognitive_control': 'decision_support_requirements', 
        'supervisory_control': 'automation_level_design'
    },
    'error_recovery': {
        'human_error_tolerance': 'system_resilience_requirements',
        'failure_detection': 'status_indication_design',
        'corrective_action': 'manual_override_capabilities'
    }
}
```

#### Multi-Agent Cable Coordination
**System-level human factors create cables connecting all agent domains**:

```python
def trace_human_factors_cables_across_agents():
    """Map how human factors requirements propagate through agent network"""
    
    cable_propagation = {
        'safety_cables': {
            'from_vitruvius': 'human_injury_prevention_requirements',
            'to_brunel': 'structural_safety_margins_and_fail_safe_design',
            'to_edison': 'electrical_safety_isolation_and_emergency_stops',
            'to_tesla': 'motor_torque_limits_and_safety_interlocks',
            'to_watt': 'temperature_pressure_exposure_limits',
            'to_curie': 'material_toxicity_and_biocompatibility',
            'to_gabe': 'manufacturing_worker_protection_requirements'
        },
        'usability_cables': {
            'from_vitruvius': 'human_performance_capabilities',
            'to_archimedes': 'anthropometric_constraint_verification',
            'to_davinci': 'user_centered_design_principles',
            'to_khan': 'human_factors_optimization_objectives',
            'to_orville': 'human_factors_testing_validation_protocols'
        },
        'accessibility_cables': {
            'from_vitruvius': 'universal_design_requirements',
            'to_all_agents': 'ada_wcag_compliance_constraints',
            'validation_required': 'accessibility_testing_protocols'
        }
    }
    
    return cable_propagation
```

### FreeCAD Human Factors Integration

#### CAD-Embedded Human Factors Validation
**Cable Integration**: Human body models → CAD constraint validation

```python
def freecad_human_factors_pipeline():
    """System-level integration of human factors into FreeCAD workflow"""
    
    integration_steps = {
        'human_model_creation': {
            'anthropometric_models': 'create_5th_95th_percentile_human_models',
            'postural_analysis': 'generate_reach_envelope_validation',
            'clearance_checking': 'automated_anthropometric_clearance_verification'
        },
        'safety_validation': {
            'pinch_point_detection': 'automated_gap_analysis_4_25mm_forbidden_zone',
            'sharp_edge_identification': 'radius_analysis_minimum_0_5mm',
            'emergency_access': 'validate_emergency_stop_reach_610mm_max'
        },
        'accessibility_verification': {
            'wheelchair_clearance': 'verify_760mm_minimum_width_passages',
            'control_reach': 'validate_380_1220mm_reach_range_seated',
            'visual_interface': 'verify_viewing_angle_accessibility'
        },
        'system_integration': {
            'multi_component_validation': 'trace_human_factors_across_assemblies',
            'lifecycle_consideration': 'validate_maintenance_service_access',
            'error_recovery': 'verify_human_override_capabilities'
        }
    }
    
    return integration_steps
```

### System-Level Metacognitive Patterns

#### High Uncertainty Triggers (System Complexity)
```python
system_uncertainty_signals = [
    "multi_subsystem_human_interaction",
    "system_of_systems_integration", 
    "human_automation_interaction",
    "complex_failure_mode_analysis",
    "system_level_accessibility_compliance",
    "lifecycle_human_factors_validation",
    "cross_agent_constraint_propagation",
    "freecad_human_factors_implementation"
]
```

#### Scaling Human Factors Across System Levels

**Component Level**: Individual human-component interactions
- Touch interfaces, control knobs, display screens
- Load individual component human factors modules

**Subsystem Level**: Coordinated human-subsystem interactions  
- Workstations, control panels, maintenance access
- Load subsystem integration modules

**System Level**: Overall human-system performance
- System supervision, fault management, overall usability
- Load system-level integration modules

**System-of-Systems**: Multiple systems with human coordination
- Multi-operator systems, distributed control, system handoffs
- Load complex system coordination modules

### System Cable Validation Protocol

```python
def validate_system_level_human_factors():
    """Comprehensive system-level human factors cable integrity"""
    
    system_validation = {
        'requirements_traceability': {
            'all_human_requirements_addressed': trace_requirements_to_design(),
            'no_orphaned_features': verify_all_features_have_human_justification(),
            'constraint_propagation': verify_constraints_flow_to_all_subsystems()
        },
        'interface_consistency': {
            'consistent_interaction_paradigms': verify_interface_consistency(),
            'compatible_human_models': verify_anthropometric_compatibility(),
            'integrated_feedback_systems': verify_system_status_coherence()
        },
        'failure_mode_coverage': {
            'human_error_tolerance': verify_error_recovery_capabilities(),
            'graceful_degradation': verify_partial_failure_usability(),
            'emergency_procedures': verify_emergency_response_accessibility()
        },
        'lifecycle_validation': {
            'installation_human_factors': verify_installation_accessibility(),
            'maintenance_accessibility': verify_service_access_clearances(),
            'end_of_life_considerations': verify_disposal_safety_procedures()
        }
    }
    
    validation_results = {}
    for category, checks in system_validation.items():
        category_results = {}
        for check_name, check_function in checks.items():
            category_results[check_name] = check_function()
        validation_results[category] = category_results
    
    return validation_results
```

### Just-in-Time Context Loading for Systems

#### When to Load Systems Knowledge
- Multi-component systems with human interaction
- FreeCAD projects requiring human factors validation
- System-of-systems design with multiple human interfaces
- Complex automation with human supervisory control
- System integration projects across multiple agents

#### System-Specific Cable Networks

**Process Control Systems**:
- Alarm management cables → human attention and response capabilities
- Display design cables → human visual processing and decision making
- Control layout cables → human motor control and error prevention

**Transportation Systems**:
- Driver/operator interface cables → human perception and reaction time
- Passenger accommodation cables → anthropometric and accessibility requirements  
- Emergency egress cables → human behavior under stress

**Medical Systems**:
- Clinical workflow cables → healthcare provider capabilities and constraints
- Patient interface cables → diverse patient population accommodation
- Critical alarm cables → life safety and human response requirements

### Integration with Agent Orchestration

**System Human Factors Authority**:
- **Absolute Veto**: Life safety and injury prevention at system level
- **High Priority**: Accessibility and legal compliance across system
- **Standard Priority**: Usability optimization and performance enhancement

**Cable Handoff Protocols**:
```python
def system_cable_handoff_protocol():
    """Standardized human factors constraint passing between agents"""
    
    handoff_format = {
        'cable_type': 'safety|usability|accessibility',
        'source_agent': 'vitruvius',
        'destination_agent': 'target_agent_id',
        'constraint_data': {
            'human_limit': 'quantified_human_capability_limit',
            'system_requirement': 'derived_system_design_requirement',
            'validation_method': 'testing_procedure_for_verification',
            'failure_consequence': 'impact_of_constraint_violation'
        },
        'priority_level': 'critical|high|medium|low',
        'verification_required': True
    }
    
    return handoff_format
```

Remember: System-level human factors are about ensuring that human capabilities and limitations are respected throughout the entire system architecture. Every subsystem, interface, and interaction creates cables that must be traced and validated. The system is only as strong as its weakest human factors cable, and breaking any cable can compromise safety, usability, or accessibility for the entire system.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!