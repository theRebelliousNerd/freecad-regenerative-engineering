# Agent Coordination Protocols

## The Requirements Interrogator's Role in Agent Orchestration

The Requirements Interrogator serves as the **foundational agent** in the Universal Workflow Pattern, operating at **Phase -0.5** to establish the complete requirements foundation that enables all subsequent agent coordination.

## Universal Workflow Integration

### Phase -0.5: Requirements Interrogation (MANDATORY FIRST)
**Requirements Interrogator PRIMARY ROLE**:
- Extract complete functional and non-functional requirements
- Generate comprehensive Requirements Blueprint  
- Validate stakeholder alignment and success criteria
- Establish measurable acceptance criteria
- Surface assumptions and validate constraints

**Critical Outputs for Agent Coordination**:
- Requirements Blueprint (complete specification)
- Component Database (for physical products)
- Stakeholder Matrix (with decision authorities)
- Constraint Hierarchy (with negotiability analysis)
- Success Metrics (with measurement methods)

### Integration with Phase 0: Multi-Domain Foundation

The Requirements Blueprint feeds directly into Phase 0 parallel foundation establishment:

#### To Archimedes (Mathematical Verifier)
```yaml
handoff_package:
  component_specifications:
    - component_id: "relay_module"
      dimensions: {length: 129.2, width: 72.1, height: 35.2}
      uncertainty: {length: 0.3, width: 0.3, height: 0.2}
      measurement_source: "digital_caliper_verified"
      confidence_level: 0.95
  
  constraints:
    - type: "dimensional"
      constraint: "max_height <= 75mm"
      negotiable: false
      violation_impact: "installation_impossible"
  
  axiom_establishment_required:
    - "component_dimensional_database"
    - "assembly_sequence_constraints"
    - "thermal_expansion_calculations"
    - "tolerance_stack_analysis"
```

#### To Carson (Planetary Boundaries)
```yaml
handoff_package:
  sustainability_requirements:
    material_constraints:
      - prohibited: ["single_use_plastics", "conflict_minerals"]
      - preferred: ["recyclable_materials", "local_sourcing"]
    
    lifecycle_requirements:
      design_lifespan: "10 years minimum"
      end_of_life: "95% recyclable components"
      carbon_footprint: "net_neutral_by_2030"
    
    regulatory_compliance:
      - standard: "RoHS directive"
        applicability: "all_electronic_components"
      - standard: "WEEE directive"  
        applicability: "end_of_life_handling"
```

#### To Vitruvius (Human Factors)
```yaml
handoff_package:
  human_factors_requirements:
    user_personas:
      - persona_id: "field_technician"
        physical_constraints: "gloved_hands", "helmet_worn"
        tool_availability: "standard_electrical_tools"
        environment: "outdoor", "temperature_extremes"
    
    safety_requirements:
      - hazard: "electrical_shock"
        mitigation: "NEMA_4X_enclosure_rating"
        verification: "UL_508A_compliance"
      - hazard: "sharp_edges"
        mitigation: "rounded_corners_min_2mm_radius"
        verification: "tactile_inspection"
    
    ergonomic_requirements:
      - requirement: "service_access"
        specification: "all_components_accessible_15min_MTTR"
        tools: "standard_phillips_screwdriver"
        clearances: "minimum_100mm_working_space"
```

## Agent-Specific Handoff Protocols

### To Turing (Kinematic Analysis)
**Triggered when**: Motion, mechanisms, or kinematic systems identified
```yaml
kinematic_requirements:
  motion_specifications:
    - joint_type: "revolute"
      range_of_motion: "0_to_180_degrees"
      angular_velocity: "max_30_rpm"
      torque_requirement: "5_Nm_continuous"
      precision: "plus_minus_0.1_degree"
  
  mechanism_constraints:
    backlash: "max_0.1_degree"
    efficiency: "min_85_percent"
    lifecycle: "1M_cycles_minimum"
    lubrication: "maintenance_free_preferred"
  
  control_requirements:
    feedback_type: "absolute_encoder"
    resolution: "0.01_degree"
    update_rate: "1000_Hz"
    communication: "EtherCAT_preferred"
```

### To Tesla (Electromagnetic Systems)
**Triggered when**: Motors, electromagnetics, or power systems identified
```yaml
electromagnetic_requirements:
  power_specifications:
    input_power: "120VAC_60Hz_single_phase"
    power_consumption: "max_150W_continuous"
    power_factor: "min_0.9"
    efficiency: "min_90_percent"
  
  motor_requirements:
    - application: "positioning_actuator"
      torque: "5_Nm_continuous_10_Nm_peak"
      speed: "max_3000_rpm"
      control_type: "servo_with_encoder_feedback"
      environment: "IP54_outdoor_rated"
  
  emc_requirements:
    emissions: "FCC_Part_15_Class_B"
    immunity: "IEC_61000-4_industrial"
    safety: "UL_508C_motor_control"
```

### To Edison (Electronics Design)
**Triggered when**: Electronic circuits, PCBs, or control systems identified
```yaml
electronics_requirements:
  control_system:
    processor: "ARM_Cortex_M4_minimum"
    memory: "512KB_flash_128KB_RAM_minimum"
    interfaces: ["CAN_bus", "RS485", "Ethernet"]
    operating_system: "real_time_preferred"
  
  io_requirements:
    digital_inputs: 16
    digital_outputs: 8
    analog_inputs: 4
    communication_ports: ["USB", "Ethernet"]
  
  environmental_requirements:
    operating_temperature: "-20C_to_60C"
    humidity: "95_percent_non_condensing"
    vibration: "IEC_60068-2-6"
    ingress_protection: "IP54_minimum"
```

### To Hertz (RF/Wireless Systems)
**Triggered when**: Wireless communication or RF systems identified
```yaml
wireless_requirements:
  communication_specifications:
    protocol: "WiFi_802.11ac_preferred"
    frequency: "2.4GHz_and_5GHz_dual_band"
    range: "100m_outdoor_line_of_sight"
    data_rate: "min_10Mbps_sustained"
  
  regulatory_requirements:
    certification: ["FCC_ID", "IC_certification"]
    sar_compliance: "required_if_handheld"
    frequency_coordination: "ISM_band_only"
  
  antenna_requirements:
    gain: "2dBi_minimum"
    polarization: "vertical_or_circular"
    mounting: "internal_preferred"
    environmental: "IP54_rated"
```

### To Curie (Materials Science)
**Triggered when**: Material properties are critical or environmental conditions are harsh
```yaml
materials_requirements:
  environmental_conditions:
    temperature_range: "-40C_to_85C"
    humidity: "0_to_95_percent_condensing"
    uv_exposure: "outdoor_10_year_minimum"
    chemical_exposure: ["salt_spray", "industrial_solvents"]
  
  mechanical_properties:
    tensile_strength: "min_50_MPa"
    impact_resistance: "5_joule_minimum"
    thermal_expansion: "max_70_ppm_per_C"
    fatigue_resistance: "1M_cycles_at_design_stress"
  
  manufacturing_constraints:
    process: "injection_molding_preferred"
    color: "UV_stable_gray_RAL_7035"
    surface_finish: "textured_for_grip"
    secondary_operations: "minimal_preferred"
```

### To Gabe (Manufacturing Optimization)
**Triggered when**: Manufacturing method affects design or cost is critical
```yaml
manufacturing_requirements:
  production_volume: "10000_units_initial_order"
  cost_targets:
    material_cost: "max_15_dollars_per_unit"
    manufacturing_cost: "max_25_dollars_per_unit" 
    tooling_amortization: "5000_units_breakeven"
  
  manufacturing_constraints:
    process: "3D_printing_PETG_or_ABS"
    tolerances: "plus_minus_0.3mm_general"
    surface_finish: "as_printed_acceptable"
    assembly: "snap_fit_preferred_no_fasteners"
  
  quality_requirements:
    dimensional_inspection: "100_percent_critical_dims"
    functional_testing: "sample_based_AQL_2.5"
    packaging: "anti_static_protection_required"
```

### To Watt (Thermal/Fluid Systems)
**Triggered when**: Thermal management or fluid systems are involved
```yaml
thermal_requirements:
  heat_generation:
    sources:
      - component: "power_supply"
        dissipation: "15W_continuous"
        hotspot_temperature: "max_85C"
      - component: "relay_module"
        dissipation: "8W_max_all_active"
        hotspot_temperature: "max_70C"
  
  thermal_management:
    ambient_conditions: "40C_max_still_air"
    internal_temperature: "max_60C"
    cooling_method: "natural_convection_preferred"
    airflow_requirements: "minimum_10_CFM_if_forced"
  
  thermal_analysis_required:
    - "steady_state_temperature_mapping"
    - "transient_thermal_response"
    - "thermal_expansion_compatibility"
```

### To Brunel (Systems Engineering)
**Triggered when**: System integration, structural analysis, or multiple subsystems
```yaml
systems_requirements:
  integration_architecture:
    subsystems: ["power", "control", "communication", "user_interface"]
    interfaces: ["CAN_bus", "power_distribution", "Ethernet"]
    fault_tolerance: "graceful_degradation_preferred"
  
  structural_requirements:
    loads:
      static: "equipment_weight_plus_50_percent"
      dynamic: "vibration_per_IEC_60068-2-6"
      environmental: "wind_load_120_mph_equivalent"
    
    safety_factors: "minimum_2.0_ultimate_strength"
    failure_modes: "ductile_preferred_no_brittle_failure"
  
  system_validation:
    - "interface_compatibility_testing"
    - "end_to_end_system_verification"
    - "failure_mode_testing"
```

### To Khan (Optimization)
**Triggered when**: Multiple competing requirements need optimization
```yaml
optimization_requirements:
  objective_functions:
    primary: "minimize_total_cost"
    secondary: ["minimize_weight", "maximize_reliability"]
    constraints: ["performance_requirements_must_be_met"]
  
  design_variables:
    - variable: "enclosure_wall_thickness"
      range: [2.0, 5.0]
      units: "mm"
      impact: "cost_weight_strength"
    
    - variable: "cooling_fan_size"
      options: ["40mm", "60mm", "80mm"]
      impact: "thermal_performance_noise_cost"
  
  optimization_criteria:
    pareto_frontier: "cost_vs_performance"
    sensitivity_analysis: "required_for_top_3_variables"
    robustness: "monte_carlo_1000_iterations"
```

### To Orville (Testing & Validation)
**Triggered when**: Validation protocols need establishment
```yaml
validation_requirements:
  test_protocols:
    - test_type: "environmental_qualification"
      standards: ["IEC_60068", "MIL_STD_810"]
      duration: "1000_hour_accelerated"
      acceptance: "zero_failures_allowed"
    
    - test_type: "electromagnetic_compatibility"
      standards: ["FCC_Part_15", "IEC_61000"]
      test_lab: "certified_third_party"
      report: "required_for_certification"
  
  performance_validation:
    - metric: "response_time"
      target: "less_than_100ms"
      test_method: "automated_system_test"
      sample_size: "100_operations_minimum"
  
  reliability_testing:
    mtbf_target: "50000_hours"
    test_method: "accelerated_life_testing"
    confidence_level: "90_percent"
```

## Critical Success Factors for Agent Coordination

### 1. Complete Requirements Blueprint
Every agent must receive complete information in their domain:
- No "TBD" entries for critical parameters
- All assumptions explicitly stated
- Measurement methods and uncertainty bounds included
- Success criteria and acceptance tests defined

### 2. Constraint Hierarchy Respected
Agent coordination must respect the constraint priority system:
```
1. Requirements Alignment (Requirements Interrogator findings)
2. Human Safety (Vitruvius requirements)
3. Planetary Boundaries (Carson constraints)
4. Mathematical Truth (Archimedes axioms)
5. [Other domain constraints by priority]
```

### 3. Handoff Validation
Each agent handoff must be validated:
- Receiving agent confirms requirements completeness
- Interface specifications verified
- Integration points tested
- Success criteria agreed upon

### 4. Change Control Integration
When requirements change:
- Requirements Interrogator updates blueprint
- Impact analysis across all affected agents
- Coordinated requirement updates
- Stakeholder notification and approval

## Agent Coordination Success Metrics

Successful requirements integration means:
- **Zero Requirements Clarification Requests**: Agents have complete information
- **No Scope Surprises**: All requirements surfaced during interrogation
- **Seamless Handoffs**: Clean interfaces between agent domains
- **Consistent Specifications**: No conflicts between agent requirements
- **Traceable Decisions**: Clear rationale for all requirements

The Requirements Interrogator's success is measured by the smooth operation of all subsequent agents working from a complete, consistent, and implementable requirements foundation.