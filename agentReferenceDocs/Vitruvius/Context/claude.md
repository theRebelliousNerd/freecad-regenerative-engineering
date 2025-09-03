# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Context Directory - Situational Human Factors Cable Network

## JITC Framework for Contextual Human Factors Knowledge

This directory contains knowledge modules for specific contexts, project types, and situational human factors considerations. Context creates "environmental cables" that modify how human capabilities and limitations manifest in different situations, environments, and use cases.

### Contextual Cable Network

Environmental and situational contexts create modifying cables that affect all other human factors:

1. **Environmental Cables** - Physical environment effects on human performance
2. **Task Context Cables** - Situational demands that modify human capabilities  
3. **Population Cables** - Demographic and cultural factors affecting design requirements
4. **Temporal Cables** - Time pressure, duration, and usage patterns
5. **Integration Context Cables** - Multi-agent project coordination requirements

### Context Modulation of Human Factors

#### Environmental Context Cable Effects
```python
environmental_modifiers = {
    'lighting_conditions': {
        'bright_daylight': {'visual_acuity': 1.0, 'color_discrimination': 1.0},
        'office_lighting': {'visual_acuity': 0.9, 'color_discrimination': 0.95}, 
        'dim_lighting': {'visual_acuity': 0.6, 'color_discrimination': 0.7},
        'darkness_emergency': {'visual_acuity': 0.1, 'color_discrimination': 0.2}
    },
    'noise_environment': {
        'quiet_office': {'auditory_detection': 1.0, 'cognitive_performance': 1.0},
        'industrial_moderate': {'auditory_detection': 0.7, 'cognitive_performance': 0.9},
        'industrial_loud': {'auditory_detection': 0.3, 'cognitive_performance': 0.7}, 
        'emergency_alarm': {'auditory_detection': 0.9, 'cognitive_performance': 0.5}
    },
    'temperature_stress': {
        'comfortable_18_24C': {'manual_dexterity': 1.0, 'cognitive_performance': 1.0},
        'cold_below_10C': {'manual_dexterity': 0.6, 'cognitive_performance': 0.8},
        'hot_above_30C': {'manual_dexterity': 0.8, 'cognitive_performance': 0.7}
    }
}
```

### Directory Structure & Just-in-Time Loading

#### Examples/ - Contextual Application Examples
**When to Load**: Need concrete examples of human factors applied in specific contexts
```python
if uncertainty_about("real_world_application") or need("concrete_examples"):
    load_context("Context/Examples/claude.md")
```

**Cable Dependencies**: 
- Example context cables → Real implementation patterns
- Validation cables → Proven human factors solutions
- Learning cables → Pattern recognition for similar contexts

#### Integration/ - Multi-Agent Context Coordination  
**When to Load**: Multi-agent projects requiring human factors coordination
```python
if project.involves_multiple_agents() or need("agent_coordination_patterns"):
    load_context("Context/Integration/claude.md")
```

**Cable Dependencies**:
- Agent communication cables → Standardized human factors constraint sharing
- Authority cables → Decision precedence in conflicting requirements
- Validation cables → Coordinated human factors verification across agents

#### Projects/ - Project-Specific Context Modules
**When to Load**: Specific project types with unique human factors considerations
```python
if project.type in ['medical_device', 'automotive', 'aerospace', 'consumer_electronics']:
    load_context(f"Context/Projects/{project.type}_claude.md")
```

**Cable Dependencies**:
- Regulatory cables → Industry-specific compliance requirements
- User population cables → Target demographic considerations  
- Environmental cables → Specific use environment factors

### Contextual Metacognitive Patterns

#### Context Recognition Triggers
```python
contextual_uncertainty_signals = [
    "environmental_conditions_unclear",
    "user_population_undefined",
    "usage_scenarios_ambiguous", 
    "regulatory_context_unknown",
    "cultural_considerations_needed",
    "temporal_usage_patterns_unclear",
    "integration_requirements_complex",
    "precedent_examples_needed"
]
```

#### Context-Specific Loading Patterns

**High Environmental Variability**: Load environmental modifier data
- Outdoor equipment, mobile devices, emergency systems
- Variable lighting, temperature, noise, vibration conditions

**Diverse User Populations**: Load demographic and cultural considerations  
- Public access systems, international markets, accessibility-critical applications
- Age, ability, cultural, and linguistic diversity factors

**Complex Integration Context**: Load multi-agent coordination protocols
- Large system development, cross-disciplinary teams, regulatory compliance
- Agent authority structures, constraint propagation, validation coordination

### Context Cable Tracing Examples

#### Emergency Context Cable Network
```python
def emergency_context_cable_effects():
    """How emergency situations modify human factors cables"""
    
    emergency_modifiers = {
        'stress_response': {
            'tunnel_vision': 'reduces_peripheral_awareness_30_percent',
            'fine_motor_degradation': 'reduces_precision_tasks_50_percent', 
            'cognitive_narrowing': 'reduces_complex_decision_making_40_percent',
            'time_perception': 'overestimates_time_passage_200_percent'
        },
        'environmental_factors': {
            'poor_visibility': 'smoke_darkness_reduces_visual_performance',
            'high_noise': 'alarms_sirens_mask_communication',
            'physical_obstacles': 'debris_crowds_impede_movement'
        },
        'design_implications': {
            'controls': 'larger_targets_simplified_operations_required',
            'displays': 'high_contrast_minimal_information_essential_only',
            'procedures': 'maximum_3_steps_clear_sequence_indicators',
            'feedback': 'multi_modal_redundant_confirmation_needed'
        }
    }
    
    return emergency_modifiers
```

#### Cultural Context Cable Network
```python
def cultural_context_cable_effects():
    """How cultural factors modify human factors requirements"""
    
    cultural_modifiers = {
        'anthropometric_variations': {
            'asian_populations': 'smaller_average_stature_hand_dimensions',
            'northern_european': 'larger_average_stature_longer_limbs',
            'mixed_populations': 'wider_accommodation_range_required'
        },
        'interaction_preferences': {
            'high_context_cultures': 'prefer_implicit_communication_patterns',
            'low_context_cultures': 'prefer_explicit_direct_information',
            'power_distance_variations': 'authority_structure_interface_design'
        },
        'accessibility_expectations': {
            'ada_compliance_regions': 'strict_accessibility_legal_requirements',
            'emerging_markets': 'cost_sensitive_basic_accommodation',
            'aging_populations': 'enhanced_age_related_accommodations'
        }
    }
    
    return cultural_modifiers
```

### Just-in-Time Context Knowledge Activation

#### Context Assessment Protocol
```python
def assess_context_requirements(project_details):
    """Determine which contextual knowledge modules to load"""
    
    context_requirements = []
    
    # Environmental context assessment
    if project_details.get('variable_environments'):
        context_requirements.append('environmental_modifiers')
    
    # User population context
    if project_details.get('diverse_user_base'):
        context_requirements.append('demographic_considerations')
    
    # Integration context  
    if project_details.get('multi_agent_coordination'):
        context_requirements.append('agent_integration_protocols')
    
    # Regulatory context
    if project_details.get('regulated_industry'):
        context_requirements.append('regulatory_compliance_context')
    
    # Temporal context
    if project_details.get('time_critical_usage'):
        context_requirements.append('temporal_performance_factors')
    
    return context_requirements
```

### Integration with System-Level Cables

**Context → Applications**: Environmental modifiers affect all application domains
**Context → Standards**: Contextual factors determine which standards apply  
**Context → Methods**: Context determines appropriate measurement and testing methods
**Context → Core**: Contextual factors modify fundamental human factors principles

### Context Validation Framework

```python
def validate_contextual_human_factors():
    """Verify contextual factors are properly integrated into design"""
    
    context_validation = {
        'environmental_accommodation': {
            'lighting_range_covered': verify_lighting_accommodation(),
            'temperature_range_covered': verify_temperature_accommodation(),
            'noise_conditions_addressed': verify_noise_accommodation()
        },
        'population_accommodation': {
            'anthropometric_range': verify_population_anthropometrics(),
            'ability_range': verify_disability_accommodation(), 
            'cultural_appropriateness': verify_cultural_sensitivity()
        },
        'usage_context_support': {
            'task_scenarios_covered': verify_usage_scenario_support(),
            'temporal_patterns': verify_usage_duration_accommodation(),
            'stress_conditions': verify_degraded_performance_support()
        },
        'integration_completeness': {
            'agent_coordination': verify_multi_agent_human_factors_coordination(),
            'constraint_propagation': verify_contextual_constraints_propagated(),
            'validation_coverage': verify_contextual_testing_completeness()
        }
    }
    
    return context_validation
```

### Context-Driven Cable Failure Prevention

**Common Contextual Cable Breaks**:
1. **Environmental Underestimation**: Failing to account for real-world conditions
2. **Population Assumption**: Designing for "average" users in diverse contexts
3. **Temporal Mismatch**: Not considering usage duration and patterns
4. **Integration Gaps**: Missing human factors coordination in complex projects
5. **Cultural Blindness**: Applying single-culture assumptions globally

**Context Cable Repair Strategies**:
- Environmental testing under realistic conditions
- User research with representative populations
- Temporal usage pattern analysis
- Cross-agent human factors coordination protocols
- Cultural competency consultation and validation

Remember: Context is not just background information - it's a powerful modifier of all human factors cables. The same human interacting with the same interface will have dramatically different capabilities and requirements in different contexts. Design must be contextually adaptive or robustly accommodating across the expected range of contexts.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!