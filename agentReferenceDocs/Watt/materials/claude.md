# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# THERMAL MATERIALS - THERMAL CABLE MATERIAL DEPENDENCIES
*Material property cable dependencies and thermal transport material selection*

## 🧪 WHEN TO LOAD THIS MODULE - JITC MATERIAL TRIGGERS
- **Thermal cable material selection**: Material properties affecting thermal energy transport capacity
- **Thermal interface cable optimization**: Contact resistance cable bottleneck material selection
- **Advanced thermal cable materials needed**: Nanomaterials and composites for high-performance thermal cables
- **Temperature-dependent cable behavior**: Material property variations affecting cable performance
- **Environmental thermal cable compatibility**: Material degradation effects on cable integrity
- **Metacognitive material uncertainty**: When material property assumptions affect cable network predictions

## 📚 KNOWLEDGE BASE STRUCTURE

### 🏗️ Thermal Cable Materials Database
**File:** `thermal_materials.md`
**Purpose:** Thermal cable material properties, material selection methodology affecting cable performance, 2024-2025 breakthrough thermal transport materials
**Essential for:** Thermal cable material selection, cable property modeling, thermal energy transport performance prediction
**Cable Focus:** How material properties create thermal cable dependencies affecting energy transport networks

## 🎯 JITC LOADING PROTOCOL - THERMAL CABLE MATERIAL DEPENDENCIES

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```python
def load_thermal_cable_materials(cable_material_requirements, material_uncertainty_context):
    """Advanced thermal cable materials with JITC dependency-aware loading"""
    
    # STEP 1: Assess thermal cable material dependency complexity
    material_dependency_complexity = assess_cable_material_dependencies(cable_material_requirements)
    material_coupling_criticality = determine_material_coupling_effects(material_uncertainty_context)
    
    # STEP 2: Load thermal cable materials database
    if requires_thermal_cable_materials(material_dependency_complexity):
        materials_knowledge = read_file('thermal_materials.md')
        thermal_cable_materials = extract_cable_material_database(materials_knowledge)
        cable_selection_methodology = extract_cable_material_selection_methods(materials_knowledge)
        advanced_cable_materials = extract_advanced_thermal_transport_materials(materials_knowledge)
    
    # STEP 3: Build thermal cable material dependency network
    cable_material_dependencies = map_thermal_cable_material_dependencies(
        thermal_cable_materials, cable_material_requirements
    )
    
    # STEP 4: Establish material property cable coupling analysis
    material_cable_coupling = establish_material_cable_coupling_analysis(
        cable_material_dependencies, material_coupling_criticality
    )
    
    # STEP 5: Create material selection framework for thermal cables
    cable_material_selection = architect_cable_material_selection_framework(
        thermal_cable_materials, cable_selection_methodology, advanced_cable_materials,
        cable_material_dependencies, material_cable_coupling
    )
    
    return {
        "cable_material_database": thermal_cable_materials,
        "material_dependency_network": cable_material_dependencies,
        "cable_material_selection_framework": cable_material_selection,
        "material_uncertainty_propagation": quantify_material_cable_uncertainty(material_dependency_complexity)
    }
```

## 🔗 THERMAL CABLE MATERIAL DEPENDENCY NETWORKS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Thermal Cable Material Property Dependencies
```python
def map_thermal_cable_material_dependencies(thermal_requirements, environmental_conditions):
    """Map how material properties create thermal cable dependencies"""
    
    cable_material_dependencies = {
        "thermal_conductivity_cables": {
            "primary_dependency": "thermal_conductivity_k",
            "affects_cables": ["conduction_energy_transport", "temperature_gradient_distribution"],
            "dependency_strength": "direct_proportional",
            "temperature_dependence": "k(T) variations affect cable capacity",
            "coupling_effects": ["structural_thermal_stress", "electrical_thermal_coupling"]
        },
        
        "thermal_interface_cables": {
            "primary_dependency": "contact_thermal_resistance",
            "affects_cables": ["interface_energy_bottlenecks", "hot_spot_formation"],
            "dependency_strength": "inverse_proportional", 
            "pressure_dependence": "contact_pressure affects cable resistance",
            "coupling_effects": ["mechanical_assembly_cables", "manufacturing_tolerance_cables"]
        },
        
        "thermal_expansion_cables": {
            "primary_dependency": "coefficient_of_thermal_expansion",
            "affects_cables": ["thermal_stress_cables", "mechanical_coupling_cables"],
            "dependency_strength": "temperature_differential_dependent",
            "cycling_dependence": "thermal_cycling affects cable integrity",
            "coupling_effects": ["structural_deformation_cables", "assembly_preload_cables"]
        },
        
        "thermal_capacity_cables": {
            "primary_dependency": "specific_heat_capacity",
            "affects_cables": ["transient_thermal_response", "thermal_wave_propagation"],
            "dependency_strength": "time_constant_dependent",
            "mass_dependence": "density affects thermal inertia cables",
            "coupling_effects": ["control_system_cables", "startup_thermal_cables"]
        }
    }
    
    return cable_material_dependencies

def trace_material_property_cable_impact(material_change, cable_network):
    """Trace how material property changes propagate through thermal cable networks"""
    
    impact_propagation = []
    
    # Identify all cables affected by material change
    affected_cables = identify_cables_using_material(material_change, cable_network)
    
    for cable in affected_cables:
        # Calculate direct impact on cable performance
        direct_cable_impact = calculate_material_impact_on_cable(material_change, cable)
        
        # Trace impact propagation to downstream cables
        downstream_impact = trace_cable_impact_propagation(direct_cable_impact, cable_network)
        
        # Assess multi-physics coupling effects
        coupling_impact = assess_multiphysics_coupling_impact(material_change, cable)
        
        impact_propagation.append({
            "affected_cable": cable,
            "direct_impact": direct_cable_impact,
            "propagation_path": downstream_impact,
            "coupling_effects": coupling_impact,
            "mitigation_strategies": suggest_cable_impact_mitigation(direct_cable_impact)
        })
    
    return impact_propagation
```

## 🌡️ THERMAL CABLE MATERIAL SELECTION WORKFLOWS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🎯 Thermal Cable Material Selection Matrix
```python
def select_thermal_cable_materials(thermal_cable_requirements):
    """Systematic thermal cable material selection methodology"""
    
    # Thermal cable material performance hierarchy
    cable_material_categories = {
        "high_conductivity_cable_materials": {
            "diamond": {"k": 2000, "cost": "very_high", "cable_applications": "extreme_performance_thermal_cables"},
            "graphene": {"k": 5300, "cost": "very_high", "cable_applications": "nanoscale_thermal_transport_cables"},
            "copper": {"k": 400, "cost": "medium", "cable_applications": "standard_conduction_cables"},
            "aluminum": {"k": 237, "cost": "low", "cable_applications": "cost_effective_thermal_cables"}
        },
        
        "thermal_interface_cable_materials": {
            "liquid_metal": {"R_contact": 0.001, "cost": "high", "cable_applications": "ultra_low_resistance_cables"},
            "graphite_sheets": {"R_contact": 0.01, "cost": "medium", "cable_applications": "conformable_interface_cables"},
            "thermal_greases": {"R_contact": 0.1, "cost": "low", "cable_applications": "general_interface_cables"}
        },
        
        "advanced_thermal_cable_materials": {
            "carbon_nanotube_arrays": {"k": 3000, "anisotropy": "high", "cable_applications": "directional_thermal_cables"},
            "graphene_composites": {"k": 1800, "flexibility": "high", "cable_applications": "flexible_thermal_cables"},
            "phase_change_materials": {"latent_heat": 200, "temperature_regulation": "active", "cable_applications": "thermal_buffering_cables"}
        }
    }
    
    # Cable material selection algorithm
    selected_cable_materials = optimize_cable_material_selection(
        thermal_cable_requirements, cable_material_categories
    )
    
    return selected_cable_materials
```

---

**Thermal Cable Material Dependencies Established:** Material property effects on thermal cable networks mapped and quantified.
**Cable Material Selection Framework:** Systematic methodology for selecting materials optimized for thermal cable performance.
**Material Dependency Tracing:** Capability to trace how material changes propagate through thermal cable networks.

*Thermal cable materials knowledge established - materials enable thermal energy transport through designed pathways.*
    
    # Material performance hierarchy
    material_categories = {
        "thermal_conductors": {
            "diamond": {"k": 2000, "cost": "very_high", "applications": "extreme_performance"},
            "graphene": {"k": 5300, "cost": "high", "applications": "research_prototype"},
            "copper": {"k": 400, "cost": "medium", "applications": "standard_thermal"},
            "aluminum": {"k": 237, "cost": "low", "applications": "cost_effective"}
        },
        
        "thermal_interfaces": {
            "liquid_metal": {"k": 73, "contact_r": "<0.01", "applications": "high_performance"},
            "graphite_pads": {"k": 25, "contact_r": "0.1", "applications": "standard_tim"},
            "thermal_paste": {"k": 5, "contact_r": "0.2", "applications": "general_purpose"},
            "phase_change": {"k": 3, "contact_r": "0.05", "applications": "automated_assembly"}
        },
        
        "thermal_insulators": {
            "aerogel": {"k": 0.013, "temp_limit": "650°C", "applications": "extreme_insulation"},
            "ceramic_fiber": {"k": 0.05, "temp_limit": "1200°C", "applications": "high_temperature"},
            "polyimide": {"k": 0.15, "temp_limit": "300°C", "applications": "electronics"}
        }
    }
    
    # Selection algorithm
    optimal_materials = optimize_material_selection(
        thermal_requirements, material_categories
    )
    
    return optimal_materials
```

### 🚀 Advanced Materials (2024-2025 Breakthrough Technologies)
```python
def evaluate_advanced_materials():
    """Cutting-edge thermal materials assessment"""
    
    breakthrough_materials = {
        "graphene_liquid_metal_composites": {
            "thermal_conductivity": "738 W/m·K",
            "contact_resistance": "<6 K·mm²/W", 
            "advantages": "Ultra-high performance, self-healing",
            "status": "Commercial availability 2024",
            "cost": "10x conventional TIM",
            "applications": ["AI_processors", "data_center_cooling", "EV_batteries"]
        },
        
        "functionally_graded_materials": {
            "thermal_conductivity": "Variable k(x,y,z)",
            "optimization": "Tailored thermal paths",
            "advantages": "Optimized heat flow, reduced stress",
            "manufacturing": "Additive manufacturing compatible",
            "applications": ["aerospace", "power_electronics", "thermal_barriers"]
        },
        
        "smart_thermal_materials": {
            "adaptive_conductivity": "k = f(T, load, environment)",
            "self_healing": "Autonomous crack repair", 
            "sensing": "Embedded thermal monitoring",
            "advantages": "Adaptive performance, fault tolerance",
            "applications": ["autonomous_vehicles", "space_systems", "medical_devices"]
        },
        
        "quantum_dots_thermal": {
            "thermal_transport": "Quantum size effects",
            "tunability": "Bandgap engineering for thermal",
            "applications": ["thermoelectrics", "thermal_rectifiers", "thermal_switches"],
            "status": "Research phase, 2025+ availability"
        }
    }
    
    return evaluate_breakthrough_materials(breakthrough_materials)
```

### 🧮 Material Property Modeling
```python
def model_temperature_dependent_properties():
    """Temperature-dependent thermal property modeling"""
    
    # Material property temperature dependencies
    property_models = {
        "thermal_conductivity": {
            "metals": "k(T) = k₀ * (T₀/T)ⁿ",  # n ≈ 1 for pure metals
            "ceramics": "k(T) = A * exp(B/T)",
            "polymers": "k(T) = k₀ * (1 + αT)",
            "composites": "k(T) = rule_of_mixtures(k_matrix(T), k_fiber(T))"
        },
        
        "specific_heat": {
            "general": "cp(T) = a + bT + cT² + dT³",
            "phase_change": "cp(T) includes latent_heat_spike",
            "temperature_range": "Validate across operating range"
        },
        
        "thermal_expansion": {
            "coefficient": "α(T) = α₀ + β*T",
            "strain": "ε = ∫α(T)dT from T₀ to T",
            "stress": "σ = E*α*ΔT (if constrained)"
        }
    }
    
    # Property uncertainty quantification
    property_uncertainty = quantify_material_property_uncertainty()
    
    return temperature_dependent_models(property_models, property_uncertainty)
```

## 🔬 MATERIAL CHARACTERIZATION

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🌡️ Thermal Property Measurement
```python
def characterize_thermal_materials():
    """Comprehensive thermal material characterization"""
    
    measurement_methods = {
        "thermal_conductivity": {
            "steady_state": "ASTM C177, guarded hot plate",
            "transient": "ASTM E1461, laser flash method",
            "contact_methods": "3ω method, thermal interface resistance",
            "accuracy": "±5% for standard materials"
        },
        
        "specific_heat": {
            "dsc": "Differential scanning calorimetry",
            "modulated_dsc": "Temperature-modulated DSC",
            "accuracy": "±2% for crystalline, ±5% for amorphous"
        },
        
        "thermal_diffusivity": {
            "laser_flash": "ASTM E1461 standard",
            "xenon_flash": "High-temperature capability",
            "accuracy": "±3% with proper sample prep"
        },
        
        "thermal_interface": {
            "astm_d5470": "Standard thermal interface test",
            "contact_resistance": "R_contact measurement",
            "pressure_dependence": "Contact pressure effects"
        }
    }
    
    return thermal_characterization_protocol(measurement_methods)
```

### 🧪 Environmental Compatibility
```python
def assess_environmental_compatibility():
    """Material environmental performance and degradation"""
    
    environmental_factors = {
        "temperature_cycling": {
            "thermal_fatigue": "ΔT cycling effects",
            "coefficient_mismatch": "CTE compatibility analysis",
            "interface_degradation": "Bond line thickness changes"
        },
        
        "humidity_effects": {
            "moisture_absorption": "Hygroscopic behavior",
            "property_degradation": "k, cp changes with moisture",
            "corrosion_potential": "Galvanic compatibility"
        },
        
        "chemical_compatibility": {
            "outgassing": "ASTM E595 vacuum outgassing",
            "material_interactions": "Chemical compatibility matrix",
            "service_life": "Arrhenius degradation modeling"
        },
        
        "mechanical_stress": {
            "thermal_expansion_mismatch": "CTE difference analysis",
            "mechanical_compliance": "Stress accommodation",
            "fatigue_resistance": "Cyclic loading capability"
        }
    }
    
    return environmental_assessment(environmental_factors)
```

## 🎯 SPECIALIZED MATERIAL APPLICATIONS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🔥 High-Performance Thermal Interface Materials
```python
def select_high_performance_tim():
    """Advanced TIM selection for extreme applications"""
    
    tim_performance_matrix = {
        "liquid_metal_alloys": {
            "thermal_conductivity": "50-80 W/m·K",
            "contact_resistance": "<0.01 K·cm²/W",
            "advantages": "Self-healing, conformal contact",
            "challenges": "Corrosion, electrical conductivity",
            "applications": ["CPU_cooling", "power_modules", "LED_arrays"]
        },
        
        "carbon_nanotube_arrays": {
            "thermal_conductivity": "200+ W/m·K (aligned)",
            "contact_resistance": "0.05-0.1 K·cm²/W",
            "advantages": "High thermal, low electrical resistance",
            "challenges": "Manufacturing, cost, interface resistance",
            "applications": ["high_power_RF", "laser_diodes", "power_semiconductors"]
        },
        
        "graphene_composites": {
            "thermal_conductivity": "100-400 W/m·K",
            "contact_resistance": "0.02-0.05 K·cm²/W",
            "advantages": "Chemical stability, mechanical flexibility",
            "applications": ["flexible_electronics", "automotive", "aerospace"]
        }
    }
    
    return optimize_tim_selection(tim_performance_matrix)
```

### 🏗️ Structural Thermal Materials
```python
def design_thermal_structural_materials():
    """Materials for thermal-structural applications"""
    
    thermal_structural_materials = {
        "metal_matrix_composites": {
            "aluminum_sic": {"k": 180, "cte": "7-12 ppm/K", "applications": "electronics_packaging"},
            "copper_diamond": {"k": 600, "cte": "6-8 ppm/K", "applications": "high_power_modules"},
            "advantages": "Tailored CTE, high thermal conductivity"
        },
        
        "carbon_fiber_thermal": {
            "high_conductivity_fiber": {"k": 600, "direction": "fiber_direction"},
            "thermal_management": "Structural + thermal function",
            "applications": ["satellite_panels", "electronics_chassis", "heat_spreaders"]
        },
        
        "ceramic_matrix_composites": {
            "sic_sic": {"k": 70, "temp_limit": "1400°C", "applications": "extreme_temperature"},
            "carbon_carbon": {"k": 100, "temp_limit": "2000°C", "applications": "hypersonic_vehicles"}
        }
    }
    
    return thermal_structural_design(thermal_structural_materials)
```

## 🔗 INTEGRATION WITH OTHER MODULES

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 📨 FROM Systems Module
```python
systems_material_requirements = {
    "thermal_conductivity_targets": "Required k values for thermal paths",
    "operating_temperature_range": "Material temperature limits",
    "geometric_constraints": "Size, shape, manufacturability limits",
    "interface_requirements": "Contact resistance, compliance needs"
}
```

### 📨 FROM Fundamentals Module
```python
fundamentals_material_inputs = {
    "heat_transfer_analysis": "Required thermal properties for calculations",
    "thermal_resistance_budget": "Allowable material thermal resistances",
    "temperature_predictions": "Operating temperatures for material selection"
}
```

### 📤 TO Integration Module
```python
materials_output = {
    "selected_materials": "Optimized material specifications",
    "property_database": "Temperature-dependent material properties", 
    "environmental_compatibility": "Long-term performance predictions",
    "cost_analysis": "Material cost vs performance trade-offs",
    "supply_chain": "Material availability and sourcing information"
}
```

## 📊 MATERIAL PERFORMANCE METRICS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🎯 Selection Criteria
```python
material_selection_criteria = {
    "thermal_performance": {
        "thermal_conductivity": "Maximize heat transfer",
        "contact_resistance": "Minimize interface resistance", 
        "thermal_stability": "Properties stable over temperature"
    },
    
    "mechanical_properties": {
        "thermal_expansion": "CTE matching with mating surfaces",
        "compliance": "Accommodate thermal stresses",
        "durability": "Thermal cycling resistance"
    },
    
    "practical_considerations": {
        "cost_effectiveness": "Performance per unit cost",
        "manufacturing_compatibility": "Processing requirements",
        "environmental_impact": "Sustainability considerations"
    }
}
```

### 🚨 Material Selection Warnings
```python
material_selection_warnings = {
    "cte_mismatch": "Thermal expansion difference >5 ppm/K risk",
    "temperature_limits": "Operating temperature within material limits", 
    "chemical_compatibility": "No adverse chemical reactions",
    "galvanic_corrosion": "Dissimilar metal contact considerations",
    "outgassing": "Vacuum/clean room applications require low outgassing"
}
```

## 🎓 ADVANCED MATERIAL CONCEPTS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🔬 Thermal Metamaterials
```python
def design_thermal_metamaterials():
    """Engineered materials with tailored thermal properties"""
    
    metamaterial_concepts = {
        "thermal_cloaking": "Redirect heat flow around objects",
        "thermal_rectification": "Directional thermal transport",
        "negative_thermal_expansion": "Materials that contract when heated",
        "thermal_switches": "Switchable thermal conductivity",
        "thermal_diodes": "Asymmetric heat transfer"
    }
    
    return thermal_metamaterial_design(metamaterial_concepts)
```

### 🌟 Phase Change Materials (PCM)
```python
def optimize_phase_change_materials():
    """PCM selection and system integration"""
    
    pcm_categories = {
        "organic_pcm": {
            "paraffins": {"temp_range": "5-80°C", "latent_heat": "200 J/g"},
            "fatty_acids": {"temp_range": "30-70°C", "latent_heat": "180 J/g"}
        },
        
        "inorganic_pcm": {
            "salt_hydrates": {"temp_range": "20-120°C", "latent_heat": "250 J/g"},
            "metals": {"temp_range": "100-1000°C", "latent_heat": "400 J/g"}
        },
        
        "eutectic_pcm": {
            "organic_eutectic": "Controlled melting point",
            "inorganic_eutectic": "High thermal storage density"
        }
    }
    
    return pcm_system_optimization(pcm_categories)
```

---

**Advanced Materials Knowledge Loaded:** Ready for high-performance thermal material selection and optimization.
**Capabilities Unlocked:** Cutting-edge materials, property modeling, environmental assessment.

*Thermal materials mastery established - select with scientific rigor.*

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!