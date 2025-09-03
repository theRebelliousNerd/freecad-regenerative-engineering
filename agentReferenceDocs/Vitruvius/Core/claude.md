# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Core Directory - Foundational Human Factors Cable Network

## JITC Framework for Core Human Factors Knowledge

This directory contains the foundational knowledge modules for human factors engineering. These modules define the fundamental "human cables" - the immutable connections between human biology, psychology, and engineering design that form the basis of all human-centered design decisions.

### Core Human Factors Cable Architecture

The Core directory establishes three primary cable networks that underpin all human factors work:

1. **Biological Cables** - Physical human characteristics (anthropometry, strength, sensory capabilities)
2. **Cognitive Cables** - Mental processing capabilities (attention, memory, decision-making)  
3. **Philosophical Cables** - Design principles that ensure human flourishing (Firmitas, Utilitas, Venustas)

### Universal Human Constraint Network

#### The Sacred Triad - Vitruvian Principles Applied to Human Factors
```python
vitruvian_human_factors = {
    'firmitas': {  # Structural integrity for human interaction
        'safety_cables': 'design_must_not_harm_human_users',
        'strength_cables': 'forces_within_human_biomechanical_limits',
        'durability_cables': 'repeated_use_without_cumulative_trauma'
    },
    'utilitas': {  # Functional accessibility  
        'capability_cables': 'functions_accessible_to_human_abilities',
        'efficiency_cables': 'tasks_completed_within_human_performance_limits',
        'effectiveness_cables': 'goals_achieved_with_acceptable_error_rates'
    },
    'venustas': {  # Aesthetic invitation to proper use
        'intuitive_cables': 'form_naturally_guides_proper_interaction',
        'comfort_cables': 'pleasant_non_threatening_interaction_experience',
        'dignity_cables': 'design_respects_human_agency_and_capability'
    }
}
```

### Directory Structure & Just-in-Time Loading

#### Assessment/ - Human Performance Measurement
**When to Load**: Need to quantify human capabilities or performance
```python
if need("cognitive_workload_measurement") or uncertainty_about("human_performance_limits"):
    load_context("Core/Assessment/claude.md")
```

**Cable Dependencies**:
- Measurement cables → Quantified human performance data
- Validation cables → Scientific assessment methodologies  
- Limit cables → Human capability boundaries and thresholds

#### Foundations/ - Fundamental Human Data
**When to Load**: Need basic human measurements, population data, or anthropometric information
```python
if need("human_body_dimensions") or uncertainty_about("population_characteristics"):
    load_context("Core/Foundations/claude.md")
```

**Cable Dependencies**:
- Anthropometric cables → Body dimension design constraints
- Population cables → Demographic variation requirements
- Statistical cables → Percentile-based design accommodation

#### Principles/ - Core Design Philosophy  
**When to Load**: Always load first - fundamental to all human factors work
```python
# ALWAYS load first in any human factors analysis
load_context("Core/Principles/claude.md")  # The Vitruvian foundation
```

**Cable Dependencies**:
- Philosophy cables → Human-centered design principles
- Ethics cables → Moral obligations in design
- Authority cables → Non-negotiable human factors requirements

### Fundamental Human Cables

#### Anthropometric Cable Network (Foundations)
```python
anthropometric_cables = {
    'stature_cables': {
        'seated_height': {'5th_percentile_female': 795, '95th_percentile_male': 965},  # mm
        'standing_height': {'5th_percentile_female': 1475, '95th_percentile_male': 1905},
        'eye_height_standing': {'5th_percentile_female': 1370, '95th_percentile_male': 1790}
    },
    'reach_cables': {
        'forward_reach': {'5th_percentile_female': 660, '95th_percentile_male': 830},
        'overhead_reach': {'5th_percentile_female': 1930, '95th_percentile_male': 2500},
        'lateral_reach': {'5th_percentile_female': 580, '95th_percentile_male': 750}
    },
    'clearance_cables': {
        'shoulder_width': {'5th_percentile_female': 325, '95th_percentile_male': 465},
        'hip_width_seated': {'5th_percentile_female': 310, '95th_percentile_male': 395},
        'head_clearance': {'5th_percentile_female': 2030, '95th_percentile_male': 2135}  # standing + margin
    }
}
```

#### Cognitive Performance Cable Network (Assessment)
```python
cognitive_cables = {
    'attention_cables': {
        'focused_attention_duration': {'optimal': '20_minutes', 'acceptable': '45_minutes'},
        'divided_attention_tasks': {'maximum_simultaneous': 3, 'optimal_simultaneous': 2},
        'vigilance_detection': {'degradation_after': '30_minutes', 'critical_after': '2_hours'}
    },
    'memory_cables': {
        'working_memory_capacity': {'items': '7_plus_minus_2', 'duration': '15_30_seconds'},
        'procedural_steps': {'maximum_without_aid': 7, 'complex_procedures': 3},
        'recognition_vs_recall': {'recognition_superior': True, 'recall_error_prone': True}
    },
    'decision_cables': {
        'simple_reaction_time': {'visual': '190ms', 'auditory': '140ms', 'tactile': '155ms'},
        'choice_reaction_time': {'2_choices': '300ms', '4_choices': '500ms', '8_choices': '750ms'},
        'decision_complexity': {'maximum_factors': 5, 'optimal_factors': 3}
    }
}
```

### Core Cable Validation Protocol

```python
def validate_core_human_factors_cables():
    """Fundamental verification that core human capabilities are respected"""
    
    core_validation = {
        'anthropometric_accommodation': {
            'clearance_verification': verify_human_body_clearances(),
            'reach_validation': verify_control_accessibility(),
            'strength_limits': verify_force_requirements_within_capability(),
            'postural_support': verify_sustainable_working_postures()
        },
        'cognitive_accommodation': {
            'workload_assessment': verify_cognitive_demand_within_limits(),
            'attention_design': verify_attention_demand_manageable(),
            'memory_support': verify_memory_aids_provided(),
            'decision_support': verify_decision_complexity_appropriate()
        },
        'sensory_accommodation': {
            'visual_requirements': verify_visual_display_adequacy(),
            'auditory_requirements': verify_audio_signal_adequacy(),
            'tactile_requirements': verify_haptic_feedback_adequacy()
        },
        'safety_cables': {
            'injury_prevention': verify_no_hazardous_human_system_interactions(),
            'error_tolerance': verify_human_error_does_not_cause_harm(),
            'emergency_response': verify_emergency_procedures_human_executable()
        }
    }
    
    # Core validation must pass completely - no compromises on fundamentals
    critical_failures = []
    for category, checks in core_validation.items():
        for check_name, check_result in checks.items():
            if not check_result:
                critical_failures.append(f"{category}.{check_name}")
    
    return {
        'core_validation_passed': len(critical_failures) == 0,
        'critical_failures': critical_failures,
        'human_factors_foundation_sound': len(critical_failures) == 0
    }
```

### Metacognitive Patterns for Core Knowledge

#### Always Load Core Principles
```python
def initialize_human_factors_analysis():
    """Every human factors analysis begins with core principles"""
    
    # MANDATORY - Always load first
    load_context("Core/Principles/claude.md")
    print("[CORE] Vitruvian principles loaded - Human dignity and safety prioritized")
    
    # Context-dependent core loading
    if project.involves_physical_interaction():
        load_context("Core/Foundations/claude.md")
        print("[CORE] Anthropometric foundation loaded")
    
    if project.involves_cognitive_demands():
        load_context("Core/Assessment/claude.md") 
        print("[CORE] Cognitive assessment capabilities loaded")
```

#### High Uncertainty Triggers for Core Loading
```python
core_uncertainty_signals = [
    "human_body_dimensions_unknown",
    "population_demographics_unclear", 
    "cognitive_workload_assessment_needed",
    "human_performance_limits_questioned",
    "fundamental_design_principles_needed",
    "anthropometric_accommodation_uncertain",
    "human_capabilities_vs_requirements_mismatch"
]
```

### Core Cable Dependencies to Other Agents

**From Core to All Agents**: Fundamental human constraints
```python
core_cable_propagation = {
    'to_archimedes': {
        'anthropometric_constraints': 'mathematical_verification_of_human_accommodation',
        'strength_limits': 'force_calculations_within_human_capability',
        'clearance_requirements': 'geometric_constraints_for_human_access'
    },
    'to_brunel': {
        'structural_safety': 'human_injury_prevention_structural_requirements',
        'load_limits': 'human_applied_forces_and_structural_response',
        'access_requirements': 'maintenance_and_service_human_accessibility'
    },
    'to_edison': {
        'interface_requirements': 'human_machine_interface_specifications',
        'safety_interlocks': 'electrical_safety_for_human_protection',
        'control_specifications': 'human_operated_control_requirements'
    },
    # ... continues for all agents
}
```

### Core Knowledge Hierarchy

#### Level 1: Universal Human Constants (Always Applicable)
- Basic anthropometric ranges (5th-95th percentile accommodation)
- Fundamental safety requirements (injury prevention)  
- Core cognitive limitations (working memory, attention span)
- Sensory capability ranges (vision, hearing, touch)

#### Level 2: Population-Specific Variables (Context Dependent)  
- Demographic-specific anthropometric data
- Age-related capability changes
- Cultural interaction preferences
- Disability-specific accommodations

#### Level 3: Task-Specific Applications (Situation Dependent)
- Workload assessment for specific tasks
- Performance measurement for particular contexts
- Specialized population considerations
- Domain-specific safety requirements

### Core Cable Integrity Monitoring

```python
def monitor_core_cable_integrity():
    """Continuous verification that core human factors remain intact"""
    
    integrity_checks = {
        'anthropometric_cables': {
            'clearances_maintained': True,  # All human body clearances preserved
            'reach_envelopes_respected': True,  # All controls within reach
            'strength_limits_observed': True   # All forces within capability
        },
        'cognitive_cables': {
            'workload_within_limits': True,     # Cognitive demand manageable  
            'information_processing_adequate': True,  # Information rate appropriate
            'decision_complexity_appropriate': True   # Choices within capability
        },
        'safety_cables': {
            'injury_risk_eliminated': True,     # No harm to humans possible
            'error_consequences_safe': True,    # Human errors non-catastrophic  
            'emergency_response_feasible': True # Emergency procedures executable
        }
    }
    
    # Any broken core cable requires immediate attention
    broken_cables = [cable for category in integrity_checks.values() 
                     for cable, intact in category.items() if not intact]
    
    if broken_cables:
        return {
            'status': 'CRITICAL_FAILURE',
            'broken_cables': broken_cables,
            'action_required': 'IMMEDIATE_DESIGN_REVISION'
        }
    else:
        return {
            'status': 'CABLES_INTACT',
            'human_factors_foundation': 'SOUND'
        }
```

Remember: The Core directory contains the non-negotiable foundation of all human factors work. These cables represent biological and psychological realities that cannot be designed around - only designed with. Every other human factors consideration builds upon this core foundation. When core cables break, humans get injured, excluded, or overwhelmed. The core is sacred and inviolable.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!