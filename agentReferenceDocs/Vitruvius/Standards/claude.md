# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Standards Directory - Regulatory and Compliance Cable Network

## JITC Framework for Human Factors Standards and Compliance

This directory contains knowledge modules for regulatory standards, compliance requirements, and industry guidelines that govern human factors engineering. These modules define the critical "compliance cables" that connect design decisions to legal, regulatory, and industry requirements for human safety, accessibility, and performance.

### Standards Cable Network Architecture

Standards create mandatory and recommended cables that must be satisfied:

1. **Safety Standards Cables** - Legal requirements for human protection from harm
2. **Accessibility Standards Cables** - Legal requirements for universal access and inclusion
3. **Ergonomics Standards Cables** - Industry best practices for human factors design
4. **Performance Standards Cables** - Required human performance capabilities and limitations
5. **Compliance Verification Cables** - Methods for demonstrating standard conformance

### Standards as Immutable Constraint Networks

Standards are not suggestions - they are constraint cables that cannot be broken:

```python
standards_constraint_hierarchy = {
    'legal_mandatory': {
        'authority_level': 'ABSOLUTE_VETO',
        'override_capability': None,
        'violation_consequences': 'legal_liability_product_recall_injury_lawsuits',
        'examples': ['ADA_compliance', 'OSHA_safety_requirements', 'FDA_medical_device_standards']
    },
    'industry_required': {
        'authority_level': 'HIGH_PRIORITY', 
        'override_capability': 'documented_risk_acceptance_only',
        'violation_consequences': 'market_rejection_insurance_issues_professional_liability',
        'examples': ['ISO_ergonomics_standards', 'ANSI_guidelines', 'IEC_safety_standards']
    },
    'best_practice_recommended': {
        'authority_level': 'STANDARD_PRIORITY',
        'override_capability': 'justified_alternative_approach',
        'violation_consequences': 'suboptimal_human_factors_performance',
        'examples': ['industry_guidelines', 'professional_recommendations', 'research_findings']
    }
}
```

### Directory Structure & Just-in-Time Loading

#### Accessibility/ - Legal Access Requirements
**When to Load**: Public access, workplace design, consumer products, digital interfaces
```python
accessibility_triggers = [
    'public_accommodation_design',
    'workplace_accessibility_required', 
    'consumer_product_development',
    'digital_interface_compliance',
    'government_facility_design'
]

if any(trigger in project_context for trigger in accessibility_triggers):
    load_context("Standards/Accessibility/claude.md")
```

**Cable Dependencies**:
- Legal compliance cables → ADA, WCAG, Section 508, EN 301 549
- Universal design cables → Design for broadest range of users
- Accommodation cables → Specific disability accommodations

#### Ergonomics/ - Human Factors Design Standards  
**When to Load**: Workplace design, product ergonomics, industrial systems
```python
ergonomics_triggers = [
    'workstation_design_needed',
    'repetitive_task_analysis',
    'manual_handling_requirements',
    'display_interface_design',
    'industrial_human_factors'
]

if any(trigger in project_context for trigger in ergonomics_triggers):
    load_context("Standards/Ergonomics/claude.md")
```

**Cable Dependencies**:
- ISO ergonomics cables → International ergonomics standards
- ANSI guidelines cables → American national standards
- Industry-specific cables → Domain-specific ergonomic requirements

#### Safety/ - Human Safety Protection Standards
**When to Load**: Machinery, electrical systems, hazardous environments, safety-critical systems
```python
safety_triggers = [
    'machinery_human_interaction',
    'electrical_system_human_contact',
    'hazardous_environment_design', 
    'emergency_system_design',
    'safety_critical_human_factors'
]

if any(trigger in project_context for trigger in safety_triggers):
    load_context("Standards/Safety/claude.md")
```

**Cable Dependencies**:
- OSHA safety cables → Occupational safety requirements
- ISO 12100 cables → Machinery safety standards  
- IEC safety cables → Electrical and electronic safety
- Emergency response cables → Life safety system requirements

### Critical Standards Cable Networks

#### Accessibility Standards Cables
```python
accessibility_standards = {
    'ada_americans_with_disabilities_act': {
        'scope': 'public_accommodations_commercial_facilities_state_local_government',
        'key_requirements': {
            'physical_accessibility': 'wheelchair_access_760mm_min_clear_width',
            'communication_accessibility': 'visual_auditory_accommodation_required',
            'program_accessibility': 'services_programs_activities_accessible',
            'employment_accessibility': 'workplace_reasonable_accommodation'
        },
        'critical_dimensions': {
            'doorway_clear_width': '815mm_minimum_920mm_preferred',
            'ramp_slope': '1_20_maximum_8_3_percent_grade',
            'reach_ranges': '380mm_to_1220mm_seated_position_limits',
            'knee_clearance': '685mm_minimum_height_760mm_width'
        }
    },
    'wcag_web_content_accessibility_guidelines': {
        'scope': 'digital_interfaces_websites_software_applications',
        'conformance_levels': ['A', 'AA_required_most_organizations', 'AAA_highest_level'],
        'key_principles': {
            'perceivable': 'information_presentable_in_ways_users_can_perceive',
            'operable': 'interface_components_navigable_by_all_users',
            'understandable': 'information_ui_operation_comprehensible',
            'robust': 'content_interpretable_by_wide_variety_user_agents'
        },
        'critical_requirements': {
            'contrast_ratios': '4_5_to_1_normal_text_3_to_1_large_text',
            'keyboard_accessibility': 'all_functionality_keyboard_accessible',
            'time_limits': 'adjustable_extendable_or_eliminatable',
            'seizure_prevention': 'no_content_flashes_more_than_3_times_per_second'
        }
    }
}
```

#### Safety Standards Cables
```python
safety_standards = {
    'iso_12100_machinery_safety': {
        'scope': 'design_and_construction_of_machinery',
        'risk_reduction_hierarchy': [
            '1_inherently_safe_design_elimination_of_hazards',
            '2_engineering_safeguarding_guards_safety_devices', 
            '3_information_for_use_warnings_training'
        ],
        'human_factors_requirements': {
            'control_systems': 'fail_safe_design_manual_override_capability',
            'emergency_stops': '600mm_maximum_reach_readily_identifiable',
            'guarding': 'prevent_access_to_danger_zones_during_operation',
            'ergonomics': 'reduce_physical_and_mental_stress_on_operators'
        }
    },
    'osha_general_industry_safety': {
        'scope': 'workplace_safety_and_health_standards',
        'key_human_factors_areas': {
            'walking_working_surfaces': 'slip_trip_fall_prevention_requirements',
            'personal_protective_equipment': 'ppe_selection_training_maintenance',
            'hazard_communication': 'chemical_hazard_information_worker_training',
            'machine_guarding': 'point_of_operation_nip_point_protection'
        },
        'critical_requirements': {
            'emergency_exits': 'minimum_2_exits_maximum_23m_travel_distance',
            'lighting_levels': 'minimum_540_lux_general_work_areas',
            'noise_exposure': '85_dBA_8_hour_TWA_hearing_conservation',
            'lifting_guidelines': 'niosh_lifting_equation_application'
        }
    }
}
```

#### Ergonomics Standards Cables
```python
ergonomics_standards = {
    'iso_9241_ergonomics_human_system_interaction': {
        'scope': 'human_centered_design_interactive_systems',
        'part_400_physical_input_devices': {
            'keyboard_requirements': 'key_force_0_25_to_1_5N_displacement_2_to_4mm',
            'pointing_devices': 'mouse_trackball_touchpad_design_requirements',
            'touch_interfaces': 'minimum_target_size_9mm_separation_2mm'
        },
        'part_420_selection_input_methods': {
            'input_method_selection': 'task_user_environment_appropriate_matching',
            'multi_modal_input': 'redundant_input_methods_accessibility_enhancement'
        }
    },
    'iso_11228_manual_handling_ergonomics': {
        'scope': 'lifting_lowering_pushing_pulling_carrying',
        'lifting_guidelines': {
            'maximum_recommended_weights': '23kg_frequent_35kg_occasional',
            'lifting_zones': 'preferred_zone_knuckle_to_shoulder_height',
            'team_lifting': 'coordination_communication_load_sharing_requirements'
        },
        'pushing_pulling_limits': {
            'initial_forces': '250N_male_150N_female_maximum',
            'sustained_forces': '100N_male_70N_female_maximum',
            'handle_heights': '950_to_1150mm_optimal_range'
        }
    }
}
```

### Just-in-Time Standards Loading Protocol

#### Standards Context Assessment
```python
def assess_standards_requirements(project_details):
    """Determine which standards apply based on project characteristics"""
    
    applicable_standards = []
    
    # Legal accessibility requirements
    if any([
        project_details.get('public_access'),
        project_details.get('workplace_design'), 
        project_details.get('government_facility'),
        project_details.get('consumer_product')
    ]):
        applicable_standards.extend([
            'Standards/Accessibility/ada_compliance.md',
            'Standards/Accessibility/universal_design_principles.md'
        ])
    
    # Digital accessibility requirements  
    if project_details.get('digital_interface'):
        applicable_standards.append('Standards/Accessibility/wcag_compliance.md')
    
    # Safety standards requirements
    if any([
        project_details.get('machinery_interaction'),
        project_details.get('electrical_systems'),
        project_details.get('hazardous_operations')
    ]):
        applicable_standards.extend([
            'Standards/Safety/iso_12100_machinery_safety.md',
            'Standards/Safety/osha_requirements.md'
        ])
    
    # Ergonomics standards requirements
    if any([
        project_details.get('workstation_design'),
        project_details.get('manual_handling'),
        project_details.get('repetitive_tasks')
    ]):
        applicable_standards.extend([
            'Standards/Ergonomics/iso_ergonomics_suite.md',
            'Standards/Ergonomics/anthropometric_standards.md'
        ])
    
    return applicable_standards
```

### Standards Compliance Verification Protocol

```python
def verify_standards_compliance():
    """Systematic verification of all applicable standards compliance"""
    
    compliance_verification = {
        'accessibility_compliance': {
            'ada_physical_requirements': verify_ada_physical_accessibility(),
            'wcag_digital_requirements': verify_wcag_aa_compliance(),
            'universal_design_principles': verify_universal_design_implementation()
        },
        'safety_compliance': {
            'machinery_safety_standards': verify_iso_12100_compliance(),
            'workplace_safety_standards': verify_osha_compliance(),
            'electrical_safety_standards': verify_iec_safety_compliance()
        },
        'ergonomics_compliance': {
            'workstation_standards': verify_workstation_ergonomics_standards(),
            'manual_handling_standards': verify_manual_handling_compliance(),
            'interface_design_standards': verify_interface_ergonomics_standards()
        },
        'documentation_requirements': {
            'compliance_documentation': verify_compliance_documentation_complete(),
            'testing_evidence': verify_testing_evidence_adequate(),
            'certification_requirements': verify_required_certifications_obtained()
        }
    }
    
    # Standards compliance is often legally required
    non_compliant_items = []
    for category, checks in compliance_verification.items():
        for check_name, compliant in checks.items():
            if not compliant:
                non_compliant_items.append(f"{category}.{check_name}")
    
    return {
        'fully_compliant': len(non_compliant_items) == 0,
        'non_compliant_items': non_compliant_items,
        'legal_risk_level': 'HIGH' if non_compliant_items else 'LOW',
        'action_required': len(non_compliant_items) > 0
    }
```

### Metacognitive Patterns for Standards

#### High Certainty Standards Knowledge (Well-Established)
- Basic ADA requirements for common situations
- Standard WCAG AA digital accessibility requirements
- Common OSHA workplace safety requirements  
- Basic ISO ergonomics principles

#### Uncertainty Triggers (Require Standards Knowledge Retrieval)
```python
standards_uncertainty_signals = [
    "regulatory_compliance_requirements_unclear",
    "accessibility_standards_applicability_unknown",
    "safety_standards_for_specific_industry_needed",
    "ergonomics_standards_for_specific_application",
    "international_standards_harmonization_needed",
    "certification_requirements_unknown",
    "legal_liability_implications_unclear"
]
```

### Integration with Agent Network

**Standards → Agent Constraint Propagation**:
```python
def propagate_standards_constraints_to_agents():
    """Distribute standards requirements as immutable constraints"""
    
    standards_constraints = {
        'to_archimedes': {
            'dimensional_constraints': 'ada_dimensional_requirements_mathematical_verification',
            'clearance_calculations': 'wheelchair_accessibility_geometric_constraints'
        },
        'to_brunel': {
            'structural_safety': 'machinery_safety_structural_requirements',
            'load_requirements': 'handrail_guard_rail_load_bearing_standards'
        },
        'to_edison': {
            'electrical_safety': 'human_electrical_safety_isolation_requirements',
            'interface_standards': 'control_panel_accessibility_requirements'
        },
        'to_gabe': {
            'manufacturing_safety': 'worker_safety_during_production_requirements',
            'assembly_accessibility': 'service_maintenance_accessibility_standards'
        }
        # Continue for all agents...
    }
    
    return standards_constraints
```

### Critical Standards Cable Failure Prevention

**Common Standards Cable Breaks**:
1. **Ignorance of Applicable Standards**: Not identifying which standards apply
2. **Partial Compliance**: Meeting some but not all standard requirements
3. **Outdated Standards**: Using superseded versions of standards
4. **Misinterpretation**: Incorrect understanding of standard requirements
5. **Documentation Gaps**: Inadequate evidence of compliance

**Standards Cable Repair Strategies**:
- Systematic standards applicability assessment for each project
- Complete compliance verification across all applicable standards
- Regular standards update monitoring and implementation
- Professional standards interpretation and consultation
- Comprehensive compliance documentation and evidence collection

### Standards Authority and Veto Power

```python
standards_authority_levels = {
    'ABSOLUTE_VETO': [
        'life_safety_standards_violations',
        'legal_accessibility_requirement_violations',
        'mandatory_regulatory_standard_violations'
    ],
    'HIGH_PRIORITY_OVERRIDE_REQUIRES_DOCUMENTED_JUSTIFICATION': [
        'industry_standard_ergonomics_violations',
        'best_practice_guideline_deviations',
        'professional_recommendation_conflicts'
    ],
    'STANDARD_CONSIDERATION': [
        'emerging_standards_not_yet_mandatory',
        'research_recommendations_not_yet_standardized',
        'optional_enhancement_guidelines'
    ]
}
```

Remember: Standards are not bureaucratic obstacles - they are the crystallized wisdom of human factors experts, distilled from decades of research, accidents, lawsuits, and human suffering. Standards cables protect both users and designers. Breaking a standards cable doesn't just risk poor design - it risks legal liability, human injury, and exclusion of people with disabilities. Standards compliance is not optional when human safety and accessibility are at stake.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!