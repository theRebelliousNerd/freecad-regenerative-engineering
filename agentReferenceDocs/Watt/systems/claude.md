# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# THERMAL SYSTEMS - THERMAL ENERGY DISTRIBUTION NETWORKS
*System-level thermal cable architectures and cooling energy network orchestration*

## ⚙️ WHEN TO LOAD THIS MODULE - JITC SYSTEM TRIGGERS
- **System thermal cable architecture required**: Multi-component energy distribution networks
- **Cooling technology cable selection needed**: Active/passive thermal transport system choice
- **Heat exchanger cable network design**: Thermal energy transfer system optimization
- **System-level cable integration uncertainty**: Multi-physics thermal coupling complexity
- **Thermal management strategy gap**: System architecture decision framework needed
- **Metacognitive system complexity**: When individual component thermal knowledge insufficient for system behavior

## 📚 KNOWLEDGE BASE STRUCTURE

### 🏗️ Thermal Management Cable Networks
**File:** `thermal_management_systems.md`
**Purpose:** System-level thermal cable architectures, energy distribution budgets, hierarchical cable design philosophy  
**Essential for:** Thermal cable network strategy, energy budget allocation across cable segments, transient thermal wave propagation
**Cable Focus:** How thermal energy flows through system-wide networks from generation to dissipation

### ❄️ Cooling Technology Cable Systems
**File:** `cooling_technologies.md` 
**Purpose:** Advanced cooling cable solutions, thermal transport technology selection, 2024-2025 cable innovations
**Essential for:** Active/passive thermal cable technology selection, cable performance comparison, cost-benefit cable analysis
**Cable Focus:** Different cooling technologies as thermal energy transport cable architectures

### 🔄 Heat Exchanger Cable Networks
**File:** `heat_exchanger_design.md`
**Purpose:** Heat exchanger cable sizing, effectiveness-NTU cable method, thermal energy network manufacturing considerations
**Essential for:** Efficient thermal energy transfer cable system design, thermal energy recovery networks
**Cable Focus:** Heat exchangers as thermal energy transfer cable hubs connecting different thermal domains

## 🎯 JITC LOADING PROTOCOL - THERMAL SYSTEM CABLE ORCHESTRATION

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```python
def load_thermal_system_cables(system_complexity, coupling_dependencies):
    """System-level thermal cable network architecture with JITC loading"""
    
    # STEP 1: Assess system thermal cable complexity
    cable_network_complexity = assess_system_cable_complexity(system_complexity)
    coupling_criticality = determine_multiphysics_coupling_needs(coupling_dependencies)
    
    # STEP 2: Load system thermal cable architecture principles
    if requires_system_cable_architecture(cable_network_complexity):
        system_knowledge = read_file('thermal_management_systems.md')
        thermal_cable_architecture = extract_system_cable_principles(system_knowledge)
    
    # STEP 3: Load cooling technology cable options
    if requires_active_thermal_cables(cable_network_complexity):
        cooling_knowledge = read_file('cooling_technologies.md')
        cooling_cable_options = extract_cooling_cable_technologies(cooling_knowledge)
    
    # STEP 4: Load heat exchanger cable networks (if multi-domain coupling needed)
    if requires_thermal_domain_coupling(coupling_criticality):
        hx_knowledge = read_file('heat_exchanger_design.md')
        heat_exchanger_cables = extract_hx_cable_principles(hx_knowledge)
    
    # STEP 5: Architect complete system thermal cable network
    system_thermal_cables = architect_system_cable_network(
        thermal_cable_architecture, cooling_cable_options, heat_exchanger_cables
    )
    
    # STEP 6: Establish system-level cable management protocols  
    cable_management = establish_system_cable_management(system_thermal_cables)
    
    return {
        "system_cable_network": system_thermal_cables,
        "cable_management_protocols": cable_management,
        "system_uncertainty_propagation": quantify_system_thermal_uncertainty(cable_network_complexity)
    }
```

## 🌡️ THERMAL SYSTEM CABLE NETWORK DESIGN WORKFLOWS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🎯 Thermal Cable Network Architecture Selection
```python
def select_thermal_cable_architecture():
    """Choose optimal thermal energy distribution network"""
    
    # Assess thermal energy cable requirements
    thermal_cable_budget = calculate_system_thermal_cable_budget()
    cable_coupling_needs = assess_multiphysics_cable_coupling()
    
    # Cable network architecture decision matrix
    if thermal_cable_budget['max_heat_flux'] < 1:  # W/cm²
        cable_architecture = "passive_natural_convection_cables"
        cable_complexity = "simple_parallel_thermal_paths"
    elif thermal_cable_budget['max_heat_flux'] < 5:
        cable_architecture = "enhanced_natural_convection_cables" 
        cable_complexity = "structured_thermal_cable_networks"
    elif thermal_cable_budget['max_heat_flux'] < 50:
        cable_architecture = "forced_air_cooling_cables"
        cable_complexity = "active_thermal_transport_networks"
    else:
        cable_architecture = "liquid_cooling_cable_system"
        cable_complexity = "high_capacity_thermal_energy_networks"
    
    # Account for multi-physics cable coupling
    if cable_coupling_needs['electromagnetic_thermal']:
        cable_architecture += "_with_em_coupling"
    if cable_coupling_needs['structural_thermal']:
        cable_architecture += "_with_mechanical_coupling"
    
    return {
        "architecture": cable_architecture,
        "complexity": cable_complexity,
        "coupling_cables": cable_coupling_needs
    }
```

### ❄️ Cooling Technology Cable Network Selection
```python
def select_cooling_cable_technology(thermal_cable_requirements):
    """Select optimal thermal transport cable network solution"""
    
    # Technology cable selection matrix from cooling_technologies.md
    cooling_cable_options = {
        "heat_sink_natural_cables": {
            "max_flux": 5, "cost": "low", "complexity": "low",
            "cable_type": "passive_convection_network",
            "cable_dependencies": ["ambient_temp", "surface_area", "fin_geometry"]
        },
        "heat_sink_forced_cables": {
            "max_flux": 50, "cost": "medium", "complexity": "medium",
            "cable_type": "forced_convection_network", 
            "cable_dependencies": ["fan_power", "airflow_patterns", "pressure_drop"]
        },
        "heat_pipe_cables": {
            "max_flux": 100, "cost": "medium", "complexity": "medium",
            "cable_type": "phase_change_transport_network",
            "cable_dependencies": ["working_fluid", "orientation", "thermal_coupling"]
        },
        "vapor_chamber_cables": {
            "max_flux": 200, "cost": "high", "complexity": "medium",
            "cable_type": "distributed_phase_change_network",
            "cable_dependencies": ["wick_structure", "vapor_space", "condenser_area"]
        },
        "liquid_cooling_cables": {
            "max_flux": 1000, "cost": "high", "complexity": "high",
            "cable_type": "active_liquid_transport_network",
            "cable_dependencies": ["pump_power", "flow_distribution", "heat_exchanger_coupling"]
        },
        "immersion_cooling_cables": {
            "max_flux": 5000, "cost": "very_high", "complexity": "high",
            "cable_type": "direct_immersion_energy_network",
            "cable_dependencies": ["dielectric_fluid", "circulation_patterns", "vapor_management"]
        }
    }
    
    # Select based on thermal cable requirements and coupling constraints
    optimal_cable_technology = optimize_cooling_cable_selection(
        thermal_cable_requirements, cooling_cable_options
    )
    
    return optimal_cable_technology
```

### 🔄 Heat Exchanger Thermal Cable Hub Design
```python
def design_heat_exchanger_cable_hub(thermal_load, fluid_properties, cable_coupling_requirements):
    """Design optimal thermal energy transfer cable hub using effectiveness-NTU method"""
    
    # From heat_exchanger_design.md - Heat exchangers as thermal cable network hubs
    hx_cable_types = {
        "shell_tube_cables": "separate_fluid_domain_thermal_cables",
        "plate_cables": "high_surface_density_thermal_cables", 
        "fin_tube_cables": "enhanced_convection_thermal_cables",
        "microchannel_cables": "high_flux_density_thermal_cables"
    }
    
    # Performance calculation for thermal cable hub
    hx_cable_performance = {}
    for hx_type, cable_architecture in hx_cable_types.items():
        # Calculate thermal cable network performance
        effectiveness = calculate_cable_effectiveness_ntu(hx_type, thermal_load)
        pressure_drop = calculate_cable_pressure_drop(hx_type, fluid_properties)
        cost = estimate_hx_cable_cost(hx_type, thermal_load)
        
        # Assess multi-physics cable coupling capacity
        coupling_capacity = assess_cable_coupling_capacity(hx_type, cable_coupling_requirements)
        
        hx_cable_performance[hx_type] = {
            "cable_effectiveness": effectiveness,
            "cable_pressure_loss": pressure_drop, 
            "cable_system_cost": cost,
            "cable_coupling_capacity": coupling_capacity,
            "cable_architecture": cable_architecture
        }
    
    # Select optimal thermal cable hub
    optimal_hx_cable_hub = select_optimal_heat_exchanger_cable_hub(hx_cable_performance)
    return optimal_hx_cable_hub
```

## 🔗 SYSTEM-LEVEL THERMAL CABLE DEPENDENCY NETWORKS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### System Thermal Cable Architecture
```python
def architect_system_thermal_cables(component_heat_sources, system_constraints):
    """Design complete system thermal energy cable network"""
    
    # Map all system thermal energy generation points
    thermal_sources = map_system_heat_sources(component_heat_sources)
    
    # Identify thermal energy sinks and coupling points
    thermal_sinks = identify_thermal_sinks(system_constraints)
    coupling_points = identify_multiphysics_coupling_nodes(system_constraints)
    
    # Design thermal cable network topology
    cable_network = {
        "primary_thermal_cables": design_primary_energy_paths(thermal_sources, thermal_sinks),
        "secondary_thermal_cables": design_backup_energy_paths(thermal_sources, thermal_sinks),
        "coupling_thermal_cables": design_multiphysics_coupling_cables(coupling_points),
        "cable_bottleneck_analysis": identify_thermal_cable_bottlenecks(cable_network),
        "cable_failure_modes": assess_cable_network_failure_modes(cable_network)
    }
    
    return cable_network

def trace_system_thermal_dependency(heat_source, affected_components):
    """Trace how thermal energy propagates through system cable dependencies"""
    
    dependency_chain = []
    current_thermal_node = heat_source
    
    while affected_components:
        # Find next thermal cable connection
        next_cable = find_thermal_cable_connection(current_thermal_node, affected_components)
        
        # Calculate thermal energy propagation
        energy_transfer = calculate_cable_energy_transfer(next_cable)
        temperature_impact = calculate_temperature_propagation(next_cable, energy_transfer)
        
        # Document dependency
        dependency_chain.append({
            "cable_segment": next_cable,
            "energy_transfer": energy_transfer,
            "temperature_impact": temperature_impact,
            "affected_component": next_cable.end_component,
            "coupling_effects": assess_multiphysics_coupling(next_cable.end_component)
        })
        
        current_thermal_node = next_cable.end_component
        affected_components.remove(current_thermal_node)
    
    return dependency_chain
```

## 🚀 ADVANCED THERMAL CABLE TECHNOLOGIES (2024-2025)

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 💎 Breakthrough Thermal Cable Networks
advanced_thermal_cable_networks = {
    "graphene_liquid_metal_cable_interfaces": {
        "thermal_conductivity": "738 W/m·K",
        "contact_resistance": "<6 K·mm²/W",
        "cable_type": "ultra_high_conductivity_interface_cables",
        "cable_dependencies": ["surface_preparation", "thermal_cycling", "electrical_isolation"],
        "applications": "High-power electronics thermal cable networks"
    },
    
    "two_phase_immersion_cable_networks": {
        "heat_flux_capacity": "> 1000 W/cm²",
        "market_growth": "22.5% CAGR",
        "cable_type": "direct_immersion_thermal_energy_networks",
        "cable_dependencies": ["fluid_circulation", "vapor_management", "condensation_cables"],
        "applications": "Data center thermal energy distribution networks"
    },
    
    "coral_vapor_chamber_cable_arrays": {
        "enhanced_surface_area": "300% vs conventional",
        "thermal_resistance": "50% reduction",
        "cable_type": "distributed_phase_change_cable_networks",
        "cable_dependencies": ["wick_connectivity", "vapor_space_coupling", "condensation_distribution"],
        "applications": "Mobile device thermal cable networks"
    },
    
    "smart_thermal_material_cables": {
        "adaptive_conductivity": "Variable k(T)",
        "self_healing": "Crack repair capability",
        "cable_type": "adaptive_thermal_transport_networks", 
        "cable_dependencies": ["temperature_sensing", "conductivity_control", "material_recovery"],
        "applications": "Aerospace adaptive thermal cable systems"
    }
}
```

### 🎯 Technology Selection Matrix
```python
def select_advanced_cooling():
    """2024-2025 cooling technology decision framework"""
    
    technology_matrix = {
        "performance_tier_1": ["natural_convection", "enhanced_fins"],
        "performance_tier_2": ["forced_air", "heat_pipes"], 
        "performance_tier_3": ["vapor_chambers", "single_phase_liquid"],
        "performance_tier_4": ["two_phase_liquid", "immersion_cooling"],
        "performance_tier_5": ["advanced_materials", "phase_change"]
    }
    
    # Select tier based on requirements
    required_tier = determine_performance_tier(thermal_requirements)
    cooling_solutions = technology_matrix[required_tier]
    
    return cooling_solutions
```

## 🔗 INTEGRATION WITH OTHER MODULES

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 📨 FROM Fundamentals Module
```python
fundamentals_input = {
    "heat_transfer_coefficients": "h values for convection calculations",
    "thermal_resistances": "Component thermal resistance data",
    "material_properties": "Thermal conductivity, specific heat",
    "temperature_limits": "Component operating constraints"
}
```

### 📨 FROM Analysis Module
```python
analysis_feedback = {
    "cfd_validation": "Flow and temperature field validation",
    "optimization_results": "Multi-objective optimization outcomes", 
    "test_correlation": "Experimental vs predicted performance",
    "uncertainty_bounds": "Confidence intervals for predictions"
}
```

### 📤 TO Integration Module
```python
systems_output = {
    "cooling_system_geometry": "3D models and spatial requirements",
    "thermal_interface_specs": "TIM selection and application",
    "flow_system_requirements": "Pump/fan specifications",
    "power_consumption": "Parasitic losses for cooling system"
}
```

## 🎯 SYSTEM PERFORMANCE METRICS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🏆 Design Targets
```python
system_performance_targets = {
    "thermal_efficiency": "> 80% (useful cooling / total power)",
    "temperature_uniformity": "< 10°C variation across components",
    "response_time": "< 30 seconds to steady-state",
    "reliability": "> 50,000 hours MTBF",
    "noise_level": "< 35 dBA at 1 meter"
}
```

### 📊 Optimization Objectives  
```python
multi_objective_optimization = {
    "minimize": ["cost", "weight", "volume", "power_consumption"],
    "maximize": ["cooling_capacity", "reliability", "efficiency"],
    "constraints": ["temperature_limits", "space_envelope", "manufacturing"]
}
```

## 🚨 SYSTEM DESIGN WARNINGS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🛑 Critical Design Errors to Avoid
```python
design_pitfalls = {
    "insufficient_thermal_margin": "< 20% derating leads to failure",
    "poor_airflow_design": "Dead zones cause hot spots", 
    "thermal_interface_neglect": "Major thermal resistance bottleneck",
    "transient_neglect": "Startup/shutdown thermal stresses",
    "manufacturing_tolerance": "Thermal contact variability"
}
```

### ⚖️ Design Trade-offs
```python
system_tradeoffs = {
    "performance_vs_cost": "Higher cooling capacity increases cost",
    "size_vs_efficiency": "Compact designs often less efficient",
    "noise_vs_cooling": "Quiet operation limits heat removal",
    "complexity_vs_reliability": "More components = more failure modes"
}
```

---

## 🔍 SYSTEM-LEVEL THERMAL CABLE DEPENDENCY TRACING

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### System Thermal Cable Network Validation
```python
def validate_system_thermal_cable_network(system_cable_network):
    """Validate complete system thermal energy distribution network"""
    
    validation_results = {
        "energy_balance": verify_system_energy_conservation(system_cable_network),
        "cable_capacity_margins": assess_thermal_cable_margins(system_cable_network),
        "coupling_cable_integrity": validate_multiphysics_coupling_cables(system_cable_network),
        "thermal_bottleneck_identification": identify_system_thermal_bottlenecks(system_cable_network),
        "cable_failure_resilience": assess_thermal_cable_redundancy(system_cable_network),
        "transient_cable_response": validate_thermal_wave_propagation(system_cable_network)
    }
    
    return validation_results

def trace_system_thermal_impact(design_change, system_cable_network):
    """Trace how design changes propagate through thermal cable dependencies"""
    
    impact_propagation = trace_thermal_cable_impact(design_change, system_cable_network)
    
    affected_subsystems = []
    for cable_path in impact_propagation:
        subsystem_impact = assess_subsystem_thermal_impact(cable_path)
        if subsystem_impact['significance'] > threshold:
            affected_subsystems.append({
                "subsystem": subsystem_impact['affected_system'],
                "thermal_impact": subsystem_impact['temperature_change'],
                "performance_impact": subsystem_impact['performance_degradation'],
                "coupling_effects": subsystem_impact['multiphysics_coupling_changes']
            })
    
    return affected_subsystems
```

---

**System Thermal Cable Networks Established:** Ready for thermal energy architecture orchestration and system-level cable management.
**Cable Dependencies Mapped:** Multi-physics system thermal coupling cables validated.
**Integration Points:** Links to fundamentals for cable physics, analysis for network validation, materials for cable properties.

*Thermal system cable networks architected - energy flows through designed pathways, dependencies traced and managed.*

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!