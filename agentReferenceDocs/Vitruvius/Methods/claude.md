# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Methods Directory - Human Factors Validation Cable Network

## JITC Framework for Human Factors Methodology

This directory contains knowledge modules for measurement, testing, and validation methods in human factors engineering. These modules define the critical "validation cables" that connect theoretical human factors principles to empirical reality through systematic measurement and testing.

### Methods Cable Network Architecture

Methods create verification cables that validate human factors assumptions:

1. **Measurement Cables** - Quantify human capabilities and performance
2. **Testing Cables** - Validate design decisions against human reality
3. **Validation Cables** - Verify that designs actually work for real humans
4. **Assessment Cables** - Evaluate human factors success and identify problems
5. **Iteration Cables** - Feedback loops for continuous human factors improvement

### Methods as Cable Verification Systems

Every design decision creates a human factors hypothesis. Methods provide the cables that test these hypotheses against reality:

```python
human_factors_hypothesis_testing = {
    'design_hypothesis': 'this_interface_is_usable_by_target_population',
    'measurement_cables': 'quantify_user_performance_and_satisfaction',
    'testing_cables': 'validate_under_realistic_conditions',  
    'validation_cables': 'verify_with_representative_users',
    'assessment_cables': 'evaluate_success_against_criteria',
    'iteration_cables': 'improve_based_on_empirical_evidence'
}
```

### Directory Structure & Just-in-Time Loading

#### Measurement/ - Quantifying Human Performance
**When to Load**: Need to measure human capabilities, performance, or responses
```python
if need("anthropometric_measurement") or need("performance_quantification"):
    load_context("Methods/Measurement/claude.md")
```

**Cable Dependencies**:
- Data collection cables → Systematic measurement protocols
- Instrumentation cables → Tools and equipment for human measurement
- Statistics cables → Analysis methods for human performance data

#### Testing/ - Validating Human Factors Designs
**When to Load**: Need to test designs with real humans or validate assumptions
```python
if need("usability_testing") or need("ergonomic_validation"):
    load_context("Methods/Testing/claude.md")
```

**Cable Dependencies**:
- Protocol cables → Structured testing procedures
- Participant cables → Representative user recruitment and management
- Results cables → Interpretation and application of testing outcomes

#### Validation/ - Verifying Human Factors Success
**When to Load**: Need to verify that human factors goals have been achieved
```python
if need("design_validation") or need("compliance_verification"):
    load_context("Methods/Validation/claude.md")
```

**Cable Dependencies**:
- Criteria cables → Success metrics and acceptance standards
- Evidence cables → Documentation and proof of human factors achievement
- Compliance cables → Regulatory and standard conformance verification

### Measurement Cable Network (Measurement/)

#### Anthropometric Measurement Cables
```python
anthropometric_measurement_methods = {
    'static_measurements': {
        'body_dimensions': 'caliper_and_anthropometer_protocols',
        'reach_envelopes': '3d_scanning_and_measurement_procedures', 
        'clearance_requirements': 'spatial_accommodation_assessment',
        'population_sampling': 'representative_demographic_protocols'
    },
    'dynamic_measurements': {
        'range_of_motion': 'goniometer_and_motion_capture_methods',
        'functional_reach': 'task_based_reach_envelope_measurement',
        'postural_analysis': 'rula_reba_owas_assessment_protocols',
        'movement_tracking': '3d_motion_analysis_systems'
    },
    'strength_measurements': {
        'grip_strength': 'dynamometer_protocols_jamar_standard',
        'lifting_capacity': 'psychophysical_and_biomechanical_assessment',
        'push_pull_forces': 'force_gauge_measurement_procedures',
        'endurance_testing': 'sustained_force_capability_protocols'
    }
}
```

#### Cognitive Performance Measurement Cables
```python
cognitive_measurement_methods = {
    'workload_assessment': {
        'nasa_tlx': 'subjective_workload_assessment_procedure',
        'secondary_task': 'dual_task_performance_degradation_measurement',
        'physiological': 'heart_rate_variability_pupillometry_eeg',
        'behavioral': 'reaction_time_error_rate_task_completion'
    },
    'attention_measurement': {
        'vigilance_testing': 'sustained_attention_response_task_protocols',
        'selective_attention': 'stroop_flanker_task_procedures',
        'divided_attention': 'multi_task_performance_assessment',
        'attention_span': 'continuous_performance_task_methods'
    },
    'memory_assessment': {
        'working_memory': 'n_back_digit_span_spatial_span_tests',
        'procedural_memory': 'skill_retention_and_transfer_assessment',
        'recognition_recall': 'memory_performance_comparison_protocols'
    }
}
```

### Testing Cable Network (Testing/)

#### Usability Testing Cables
```python
usability_testing_methods = {
    'formative_testing': {
        'think_aloud_protocols': 'concurrent_verbal_protocol_procedures',
        'cognitive_walkthroughs': 'expert_evaluation_task_analysis',
        'heuristic_evaluation': 'systematic_usability_principle_assessment',
        'iterative_prototyping': 'rapid_cycle_design_test_improve'
    },
    'summative_testing': {
        'task_completion_testing': 'success_rate_time_error_measurement',
        'comparative_testing': 'ab_testing_alternative_design_comparison',
        'field_studies': 'naturalistic_usage_observation_protocols',
        'longitudinal_studies': 'long_term_usage_pattern_analysis'
    },
    'accessibility_testing': {
        'screen_reader_testing': 'assistive_technology_compatibility',
        'motor_impairment_testing': 'alternative_input_method_validation',
        'cognitive_accessibility': 'simple_language_clear_navigation_testing',
        'sensory_impairment_testing': 'vision_hearing_accommodation_validation'
    }
}
```

#### Ergonomic Validation Cables
```python
ergonomic_testing_methods = {
    'postural_analysis': {
        'rula_assessment': 'rapid_upper_limb_assessment_protocol',
        'reba_assessment': 'rapid_entire_body_assessment_protocol',
        'owas_analysis': 'ovako_working_postures_analysis_system',
        'niosh_lifting': 'lifting_equation_biomechanical_assessment'
    },
    'workplace_assessment': {
        'environmental_measurement': 'lighting_noise_temperature_vibration',
        'workstation_evaluation': 'adjustability_accessibility_comfort',
        'tool_assessment': 'handle_design_weight_vibration_analysis',
        'workflow_analysis': 'motion_study_efficiency_safety_evaluation'
    },
    'safety_testing': {
        'hazard_identification': 'systematic_risk_assessment_protocols',
        'emergency_response': 'evacuation_procedure_testing_validation',
        'protective_equipment': 'ppe_effectiveness_comfort_compliance',
        'incident_analysis': 'human_error_accident_investigation_methods'
    }
}
```

### Validation Cable Network (Validation/)

#### Design Validation Cables
```python
validation_methods = {
    'performance_validation': {
        'acceptance_criteria': 'quantified_success_metrics_definition',
        'benchmark_comparison': 'performance_vs_existing_solutions',
        'statistical_significance': 'hypothesis_testing_confidence_intervals',
        'effect_size_analysis': 'practical_significance_assessment'
    },
    'compliance_validation': {
        'standards_verification': 'iso_ansi_ada_wcag_compliance_checking',
        'regulatory_approval': 'fda_ce_mark_safety_certification_processes',
        'accessibility_certification': 'third_party_accessibility_auditing',
        'quality_assurance': 'systematic_validation_documentation'
    },
    'user_acceptance_validation': {
        'satisfaction_surveys': 'validated_user_satisfaction_instruments',
        'adoption_metrics': 'actual_usage_pattern_measurement',
        'preference_testing': 'paired_comparison_ranking_methods',
        'longitudinal_acceptance': 'sustained_usage_satisfaction_tracking'
    }
}
```

### Metacognitive Patterns for Methods

#### High Uncertainty Triggers for Methods Loading
```python
methods_uncertainty_signals = [
    "need_to_measure_human_performance",
    "design_assumptions_need_validation",
    "user_testing_protocol_needed",
    "ergonomic_assessment_required", 
    "accessibility_testing_needed",
    "compliance_verification_necessary",
    "human_factors_metrics_undefined",
    "validation_criteria_unclear"
]
```

#### Methods Selection Protocol
```python
def select_appropriate_methods(validation_requirements):
    """Just-in-Time method selection based on validation needs"""
    
    method_selection = {
        'measurement_needs': {
            'anthropometric_data_required': 'load_anthropometric_measurement_protocols',
            'performance_quantification_needed': 'load_performance_measurement_methods',
            'workload_assessment_required': 'load_cognitive_measurement_techniques'
        },
        'testing_requirements': {
            'usability_validation_needed': 'load_usability_testing_protocols',
            'ergonomic_validation_required': 'load_ergonomic_assessment_methods',
            'accessibility_testing_needed': 'load_accessibility_validation_procedures'
        },
        'validation_demands': {
            'design_validation_required': 'load_design_validation_frameworks',
            'compliance_verification_needed': 'load_standards_compliance_methods',
            'user_acceptance_validation': 'load_acceptance_testing_protocols'
        }
    }
    
    return method_selection
```

### Cable Integrity Through Methods

#### Methods as Cable Verification Systems
```python
def verify_human_factors_cables_through_methods():
    """Use methods to verify that human factors cables are intact"""
    
    cable_verification = {
        'anthropometric_cables': {
            'measurement_verification': 'measure_actual_user_dimensions',
            'accommodation_testing': 'test_clearance_and_reach_adequacy',
            'population_validation': 'verify_percentile_accommodation'
        },
        'cognitive_cables': {
            'workload_measurement': 'quantify_actual_cognitive_demand',
            'performance_testing': 'measure_task_completion_accuracy_speed',
            'attention_validation': 'test_attention_demand_sustainability'
        },
        'safety_cables': {
            'hazard_testing': 'identify_and_eliminate_injury_risks',
            'emergency_validation': 'test_emergency_procedure_feasibility',
            'error_consequence_testing': 'verify_human_errors_safe'
        },
        'usability_cables': {
            'task_completion_testing': 'verify_users_can_complete_tasks',
            'efficiency_measurement': 'quantify_time_and_effort_requirements',
            'satisfaction_assessment': 'measure_user_experience_quality'
        }
    }
    
    return cable_verification
```

### Integration with Agent Network

**Methods → Other Agents**: Validation requirements and results
```python
methods_agent_integration = {
    'to_archimedes': 'provide_measurement_data_for_mathematical_verification',
    'to_brunel': 'validate_structural_safety_through_human_factors_testing',
    'to_edison': 'test_interface_usability_and_safety',
    'to_gabe': 'validate_manufacturability_includes_assembly_human_factors',
    'to_orville': 'provide_testing_protocols_and_validation_methods',
    'from_all_agents': 'receive_design_specifications_for_human_factors_testing'
}
```

### Methods Cable Failure Prevention

**Common Methods Cable Breaks**:
1. **Insufficient Measurement**: Testing without adequate measurement protocols
2. **Unrepresentative Testing**: Validating with non-representative users
3. **Invalid Metrics**: Using inappropriate success criteria  
4. **Statistical Inadequacy**: Insufficient sample sizes or analysis methods
5. **Ecological Invalidity**: Testing in unrealistic conditions

**Methods Cable Repair Strategies**:
- Systematic method selection based on validation requirements
- Representative participant recruitment and testing conditions
- Valid and reliable measurement instruments and protocols
- Appropriate statistical analysis and interpretation methods
- Realistic testing environments and task scenarios

Remember: Methods are the reality-testing cables that connect human factors theory to actual human performance. Without robust methods, human factors becomes guesswork. Every design decision must be validated against real human capabilities and limitations through systematic measurement and testing. Methods don't just measure success - they prevent failure by catching problems before they harm real users.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!