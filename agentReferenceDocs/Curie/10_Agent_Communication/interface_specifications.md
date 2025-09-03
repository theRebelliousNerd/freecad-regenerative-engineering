# Agent Communication Interface Specifications
## Systematic Information Exchange for Multi-Agent Thermal and Materials Analysis

*"Science is built upon the foundation of precise communication."* - Curie Communication Principle

## Communication Protocol Overview

The Curie agent operates within a multi-agent ecosystem where materials and thermal analysis must be coordinated with structural, electromagnetic, manufacturing, and other engineering domains. Communication occurs through structured data files and shared FreeCAD model annotations.

## Input Interface Specifications

### From Turing Agent (Kinematics/Mechanisms)

**File**: `kinematic_thermal_requirements.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "turing_agent_v2.1",
  "mechanisms": [
    {
      "mechanism_id": "main_drive_gearbox",
      "type": "planetary_gear",
      "operating_conditions": {
        "speed_range": {"min": 100, "max": 5000, "units": "rpm"},
        "torque_range": {"min": 10, "max": 200, "units": "Nm"},
        "duty_cycle": {"continuous": true, "peak_duration": null},
        "precision_requirements": {"backlash_max": 0.1, "units": "degrees"}
      },
      "bearing_requirements": [
        {
          "bearing_id": "input_bearing",
          "load_radial": {"value": 1500, "units": "N", "uncertainty": 0.15},
          "load_axial": {"value": 800, "units": "N", "uncertainty": 0.20},
          "speed": {"value": 5000, "units": "rpm"},
          "life_requirement": {"value": 10000, "units": "hours"}
        }
      ],
      "lubrication_requirements": {
        "method": "grease",
        "relubrication_interval": {"value": 2000, "units": "hours"},
        "operating_temp_range": {"min": -20, "max": 80, "units": "celsius"}
      },
      "material_preferences": {
        "gear_materials": ["carburized_steel", "case_hardened_steel"],
        "bearing_materials": ["bearing_steel", "ceramic_hybrid"],
        "housing_materials": ["aluminum_alloy", "cast_iron"]
      }
    }
  ],
  "thermal_considerations": {
    "heat_generation_sources": [
      {
        "source": "gear_meshing_losses",
        "power_loss": {"value": 150, "units": "W", "uncertainty": 0.25}
      },
      {
        "source": "bearing_friction", 
        "power_loss": {"value": 75, "units": "W", "uncertainty": 0.30}
      }
    ],
    "cooling_constraints": {
      "natural_convection_only": true,
      "max_surface_temperature": {"value": 70, "units": "celsius"},
      "ambient_temperature": {"value": 25, "units": "celsius"}
    }
  }
}
```

**Curie Processing Protocol**:
1. Extract bearing load requirements for material selection
2. Analyze heat generation for thermal management
3. Evaluate material compatibility with kinematic constraints
4. Validate operating temperature ranges

### From Tesla Agent (Electromagnetic)

**File**: `electromagnetic_thermal_specifications.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "tesla_agent_v2.1", 
  "electromagnetic_systems": [
    {
      "system_id": "main_drive_motor",
      "type": "BLDC_motor",
      "power_rating": {"rated": 5000, "peak": 8000, "units": "W"},
      "thermal_analysis": {
        "power_losses": [
          {
            "loss_type": "copper_losses",
            "power": {"value": 200, "units": "W", "temperature_coefficient": 0.004}
          },
          {
            "loss_type": "iron_losses", 
            "power": {"value": 150, "units": "W", "frequency_dependent": true}
          },
          {
            "loss_type": "mechanical_losses",
            "power": {"value": 50, "units": "W"}
          }
        ],
        "hotspot_locations": [
          {
            "location": "stator_windings",
            "peak_temperature": {"limit": 155, "units": "celsius"},
            "thermal_time_constant": {"value": 300, "units": "seconds"}
          },
          {
            "location": "rotor_magnets",
            "peak_temperature": {"limit": 120, "units": "celsius"},
            "demagnetization_risk": "high_above_100C"
          }
        ]
      },
      "material_requirements": {
        "magnetic_materials": {
          "stator_core": {"material": "electrical_steel", "grade": "M19_29G"},
          "rotor_magnets": {"material": "NdFeB", "grade": "N42", "temperature_grade": "H"}
        },
        "electrical_materials": {
          "windings": {"material": "copper", "insulation_class": "H"},
          "insulation": {"material": "polyimide", "temperature_rating": 220}
        },
        "thermal_interfaces": [
          {
            "interface": "stator_to_housing",
            "requirement": "high_thermal_conductivity",
            "target_resistance": {"value": 0.1, "units": "K_per_W"}
          }
        ]
      }
    }
  ],
  "cooling_requirements": {
    "method": "liquid_cooling",
    "coolant_specifications": {
      "type": "50_50_ethylene_glycol",
      "flow_rate": {"min": 5, "units": "L_per_min"},
      "inlet_temperature": {"max": 65, "units": "celsius"}
    }
  }
}
```

**Curie Processing Protocol**:
1. Calculate heat generation from electromagnetic losses
2. Select thermal interface materials for motor cooling
3. Analyze magnet temperature stability
4. Design cooling jacket materials and geometry

### From Edison Agent (Electronics)

**File**: `electronics_thermal_specifications.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z", 
  "analyst": "edison_agent_v2.1",
  "pcb_assemblies": [
    {
      "pcb_id": "motor_controller_main",
      "dimensions": {"length": 120, "width": 80, "thickness": 1.6, "units": "mm"},
      "layer_count": 4,
      "power_components": [
        {
          "component_id": "IGBT_module_U1",
          "package": "TO247",
          "location": {"x": 30, "y": 40, "units": "mm"},
          "thermal_characteristics": {
            "power_dissipation": {"typical": 25, "max": 40, "units": "W"},
            "junction_to_case": {"value": 0.5, "units": "K_per_W"},
            "max_junction_temp": {"value": 150, "units": "celsius"}
          },
          "mounting": {
            "thermal_pad": {"required": true, "area": 100, "units": "mm2"},
            "heat_sink": {"required": true, "min_area": 2000, "units": "mm2"}
          }
        },
        {
          "component_id": "gate_driver_U5", 
          "package": "SOIC16",
          "power_dissipation": {"typical": 2, "max": 3, "units": "W"},
          "thermal_derating": {"start": 70, "max": 125, "units": "celsius"}
        }
      ],
      "thermal_zones": [
        {
          "zone_id": "high_power_zone",
          "components": ["IGBT_module_U1", "IGBT_module_U2", "IGBT_module_U3"],
          "total_power": {"typical": 75, "max": 120, "units": "W"},
          "cooling_method": "heat_sink_required"
        }
      ]
    }
  ],
  "enclosure_requirements": {
    "ingress_protection": "IP65",
    "operating_temperature": {"min": -20, "max": 70, "units": "celsius"},
    "vibration_resistance": {"frequency_range": "10-2000Hz", "amplitude": "5G"}
  }
}
```

**Curie Processing Protocol**:
1. Calculate component junction temperatures
2. Select thermal interface materials for power electronics
3. Design heat sink geometries for high-power components
4. Analyze PCB thermal management strategies

### From Gabe Agent (Manufacturing)

**File**: `manufacturing_constraints.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "gabe_agent_v2.1",
  "manufacturing_processes": [
    {
      "process": "3D_printing_FDM",
      "materials_compatible": [
        {
          "material": "PETG",
          "print_temperature": {"nozzle": 240, "bed": 80, "units": "celsius"},
          "thermal_properties": {
            "max_service_temp": 70,
            "thermal_expansion": 75e-6,
            "thermal_conductivity": 0.2,
            "units": {"temp": "celsius", "expansion": "1/K", "conductivity": "W/m/K"}
          },
          "mechanical_properties": {
            "yield_strength": 50,
            "youngs_modulus": 2100,
            "units": {"strength": "MPa", "modulus": "MPa"}
          },
          "manufacturability": {
            "overhang_angle_max": 45,
            "minimum_feature_size": 0.2,
            "surface_finish": "Ra_12.5_micron",
            "dimensional_tolerance": "±0.2mm"
          }
        }
      ]
    }
  ],
  "post_processing": {
    "annealing": {
      "temperature": {"value": 60, "units": "celsius"},
      "duration": {"value": 4, "units": "hours"},
      "stress_relief": "partial"
    },
    "machining": {
      "operations": ["drilling", "threading"],
      "tool_access_requirements": "standard_tooling"
    }
  },
  "quality_control": {
    "dimensional_inspection": "CMM_measurement",
    "thermal_testing": {
      "temperature_cycling": {
        "range": {"min": -20, "max": 80, "units": "celsius"},
        "cycles": 100
      }
    }
  }
}
```

## Output Interface Specifications

### To Brunel Agent (Structural Analysis)

**File**: `material_thermal_properties.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "curie_agent_v2.1",
  "materials_database": [
    {
      "material_id": "aluminum_6061_T6_verified",
      "classification": "structural_aluminum_alloy",
      "mechanical_properties": {
        "yield_strength": {
          "value": 276, "units": "MPa", "uncertainty": 0.10,
          "temperature_dependence": [
            {"temperature": 20, "value": 276, "units": "celsius_MPa"},
            {"temperature": 100, "value": 241, "units": "celsius_MPa"},
            {"temperature": 200, "value": 152, "units": "celsius_MPa"}
          ]
        },
        "ultimate_strength": {
          "value": 310, "units": "MPa", "uncertainty": 0.08,
          "temperature_dependence": [
            {"temperature": 20, "value": 310, "units": "celsius_MPa"},
            {"temperature": 100, "value": 289, "units": "celsius_MPa"},
            {"temperature": 200, "value": 186, "units": "celsius_MPa"}
          ]
        },
        "youngs_modulus": {
          "value": 68.9e9, "units": "Pa", "uncertainty": 0.05,
          "temperature_coefficient": -0.0004
        },
        "fatigue_properties": {
          "endurance_limit": {"value": 96, "units": "MPa", "cycles": "1e7"},
          "fatigue_strength_coefficient": 758,
          "fatigue_strength_exponent": -0.12
        }
      },
      "thermal_properties": {
        "thermal_conductivity": {"value": 167, "units": "W/m/K", "uncertainty": 0.05},
        "thermal_expansion": {"value": 23.6e-6, "units": "1/K", "uncertainty": 0.08},
        "specific_heat": {"value": 897, "units": "J/kg/K", "uncertainty": 0.03},
        "melting_point": {"value": 652, "units": "celsius"}
      },
      "validation_status": {
        "data_source": "ASM_Metals_Handbook_verified",
        "last_updated": "2025-09-01",
        "confidence_level": 0.95
      }
    }
  ],
  "thermal_analysis_results": [
    {
      "component_id": "heat_sink_base",
      "steady_state_temperatures": {
        "max_temperature": {"value": 65.2, "units": "celsius", "location": "base_center"},
        "min_temperature": {"value": 45.8, "units": "celsius", "location": "fin_tips"},
        "thermal_gradient": {"value": 19.4, "units": "K", "direction": "vertical"}
      },
      "thermal_stresses": {
        "max_stress": {"value": 12.5, "units": "MPa", "location": "base_junction"},
        "stress_type": "thermal_expansion_constraint",
        "safety_factor": 22.1
      }
    }
  ]
}
```

### To Tesla Agent (Electromagnetic Systems)

**File**: `thermal_interface_specifications.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "curie_agent_v2.1",
  "thermal_interfaces": [
    {
      "interface_id": "motor_stator_housing",
      "application": "BLDC_motor_thermal_management",
      "recommended_tim": {
        "material_type": "phase_change_material",
        "product_specification": {
          "name": "High_Performance_PCM_TIM",
          "thermal_conductivity": {"value": 4.2, "units": "W/m/K"},
          "phase_change_temperature": {"value": 45, "units": "celsius"},
          "operating_temperature": {"min": -40, "max": 125, "units": "celsius"},
          "thermal_resistance": {"value": 0.05, "units": "K_cm2/W", "thickness": "0.1mm"}
        },
        "application_method": {
          "thickness": {"recommended": 0.1, "tolerance": "±0.02", "units": "mm"},
          "surface_preparation": "clean_degrease_apply_primer",
          "cure_conditions": {"time": 24, "temperature": 25, "units": "hours_celsius"}
        },
        "performance_prediction": {
          "thermal_resistance": {"calculated": 0.048, "units": "K_cm2/W"},
          "heat_transfer_rate": {"max": 2100, "units": "W", "area_dependent": true},
          "reliability": {
            "thermal_cycling": {"cycles": 10000, "temp_range": "-40_to_125C"},
            "expected_life": {"value": 15, "units": "years", "confidence": 0.90}
          }
        }
      }
    }
  ],
  "cooling_system_recommendations": [
    {
      "system_type": "liquid_cooling_jacket",
      "coolant_path_design": {
        "material": "aluminum_6061_T6",
        "channel_geometry": "rectangular_spiral",
        "hydraulic_diameter": {"value": 6, "units": "mm"},
        "channel_count": 8,
        "flow_path_length": {"value": 2.4, "units": "m"}
      },
      "thermal_performance": {
        "thermal_resistance": {"value": 0.02, "units": "K/W"},
        "coolant_pressure_drop": {"value": 15, "units": "kPa", "flow_rate": "5_L_per_min"},
        "heat_transfer_coefficient": {"value": 3500, "units": "W/m2/K"}
      }
    }
  ]
}
```

### To Gabe Agent (Manufacturing Integration)

**File**: `material_selection_results.json`
```json
{
  "analysis_timestamp": "2025-09-03T14:30:00Z",
  "analyst": "curie_agent_v2.1", 
  "component_materials": [
    {
      "component_id": "enclosure_housing",
      "selected_material": {
        "primary": "PETG_modified",
        "specification": "PETG_with_15%_glass_fiber",
        "supplier": "multiple_sources_available",
        "cost_factor": 1.8
      },
      "selection_rationale": {
        "thermal_requirements": "max_service_temp_85C_meets_70C_requirement",
        "mechanical_requirements": "yield_strength_75MPa_exceeds_45MPa_required",
        "manufacturing_compatibility": "FDM_printable_with_standard_settings",
        "environmental_factors": "excellent_chemical_resistance_UV_stable"
      },
      "manufacturing_considerations": {
        "print_settings": {
          "nozzle_temperature": {"value": 250, "units": "celsius"},
          "bed_temperature": {"value": 85, "units": "celsius"},
          "print_speed": {"value": 40, "units": "mm/s"},
          "layer_height": {"value": 0.2, "units": "mm"}
        },
        "post_processing": {
          "annealing": {"required": true, "temperature": 65, "duration": 4, "units": "celsius_hours"},
          "support_removal": {"method": "manual_break_away"},
          "surface_finishing": {"optional": "vapor_smoothing"}
        },
        "quality_control": {
          "dimensional_tolerance": "±0.15mm_achievable",
          "thermal_testing": "temperature_cycling_-20_to_80C_required"
        }
      },
      "sustainability_assessment": {
        "carbon_footprint": {"value": 2.1, "units": "kg_CO2_per_kg"},
        "recyclability": {"rating": "good", "method": "mechanical_recycling"},
        "end_of_life": {"biodegradable": false, "recycling_code": "1_PETG"}
      }
    }
  ],
  "material_inventory": {
    "primary_materials": [
      {"material": "PETG_glass_filled", "quantity": 5, "units": "kg", "lead_time": "3_weeks"},
      {"material": "aluminum_6061_bar_stock", "quantity": 20, "units": "kg", "lead_time": "1_week"},
      {"material": "thermal_interface_paste", "quantity": 500, "units": "g", "lead_time": "2_weeks"}
    ],
    "total_material_cost": {"value": 1250, "units": "USD", "confidence": 0.85}
  }
}
```

## Communication Status and Error Handling

### Status Reporting Protocol

**File**: `curie_agent_status.json`
```json
{
  "timestamp": "2025-09-03T14:35:00Z",
  "agent_status": {
    "operational_state": "active_analysis",
    "current_task": "thermal_interface_optimization",
    "completion_percentage": 75,
    "estimated_completion": "2025-09-03T14:45:00Z"
  },
  "analysis_progress": {
    "material_selection": "completed",
    "thermal_analysis": "in_progress", 
    "validation": "pending",
    "documentation": "pending"
  },
  "warnings": [
    {
      "severity": "medium",
      "message": "Material property uncertainty >15% for polymer thermal expansion",
      "recommendation": "Physical testing recommended for validation"
    }
  ],
  "errors": [],
  "agent_health": {
    "memory_usage": "45%",
    "computation_load": "moderate",
    "database_connection": "healthy"
  }
}
```

### Error Handling and Recovery

**Material Data Conflicts**:
```json
{
  "error_type": "material_property_conflict",
  "severity": "high",
  "description": "Conflicting thermal conductivity values from multiple sources",
  "affected_materials": ["aluminum_6061_T6"],
  "conflict_details": {
    "source_1": {"value": 167, "source": "ASM_Handbook", "confidence": 0.95},
    "source_2": {"value": 180, "source": "Supplier_Datasheet", "confidence": 0.70}
  },
  "resolution_strategy": "use_higher_confidence_source",
  "impact_assessment": "thermal_analysis_uncertainty_increased_to_20%"
}
```

This comprehensive communication framework ensures seamless integration between Curie agent and all other engineering agents while maintaining full traceability and validation of thermal and materials analysis decisions.