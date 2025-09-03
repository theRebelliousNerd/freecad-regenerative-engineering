# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# THERMAL FUNDAMENTALS - THERMAL ENERGY CABLE NETWORKS
*Foundation knowledge for thermal energy flow architecture and dependency tracing*

## 🔥 WHEN TO LOAD THIS MODULE - JITC TRIGGERS
- **Heat flux uncertainty >0.5**: Fundamental thermal physics needs validation
- **Thermal resistance unknown**: Cable network modeling required
- **Temperature prediction uncertainty**: Heat transfer foundations needed
- **Material thermal property gaps**: Conductivity/capacity data required  
- **First thermal assessment**: Core cable architecture establishment
- **Metacognitive thermal uncertainty**: When thermal intuition fails verification

## 🌡️ THERMAL CABLES: THE FUNDAMENTAL NETWORK VIEW

### Understanding Thermal Reality as Energy Cable Networks
Thermal systems are literal "cable networks" where heat energy flows through physical pathways:
- **Conduction cables**: Solid material paths carrying thermal energy
- **Convection cables**: Fluid motion paths transporting thermal energy  
- **Radiation cables**: Electromagnetic pathways transmitting thermal energy
- **Interface cables**: Contact resistances creating thermal bottlenecks

Every thermal design creates an energy cable network where heat sources connect to heat sinks through multiple parallel and series paths. Understanding thermal behavior means tracing these energy cables from generation to dissipation.

## 📚 KNOWLEDGE BASE STRUCTURE

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🌡️ Heat Transfer Cable Architecture
**File:** `heat_transfer_fundamentals.md`
**Purpose:** Core thermal energy cable theory, resistance network topology, thermal property dependencies
**Essential for:** Tracing heat flow paths, thermal resistance cable mapping, energy source characterization
**Cable Focus:** Understanding how thermal energy propagates through material cable networks

### 💨 Fluid Dynamic Cable Networks  
**File:** `fluid_dynamics_principles.md`
**Purpose:** Fluid flow cable analysis, pressure drop dependencies, convective heat transfer cables
**Essential for:** Cooling flow network design, thermal-fluid coupling, mass-energy transport cables
**Cable Focus:** How moving fluids create dynamic thermal transport cables

## 🎯 JITC LOADING PROTOCOL - THERMAL CABLE NETWORK ARCHITECTURE

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```python
def load_thermal_cable_fundamentals(uncertainty_context, thermal_dependencies):
    """Just-in-Time Context loading of thermal energy cable networks"""
    
    # STEP 1: Assess thermal cable complexity
    thermal_complexity = assess_thermal_cable_network(uncertainty_context)
    cable_criticality = determine_thermal_cable_criticality(thermal_dependencies)
    
    # STEP 2: Load thermal cable physics (core energy paths)
    if requires_conduction_cables(thermal_complexity):
        knowledge_base = read_file('heat_transfer_fundamentals.md')
        thermal_cable_principles = extract_thermal_cable_theory(knowledge_base)
    
    # STEP 3: Load fluid thermal cables (dynamic transport networks)
    if requires_convection_cables(thermal_complexity):
        fluid_knowledge = read_file('fluid_dynamics_principles.md') 
        flow_cable_principles = extract_fluid_thermal_cables(fluid_knowledge)
    
    # STEP 4: Build complete thermal cable network model
    thermal_cable_foundation = architect_thermal_cable_network(
        thermal_cable_principles, flow_cable_principles, cable_criticality
    )
    
    # STEP 5: Establish cable tracing capability
    cable_tracing_framework = establish_thermal_cable_tracing(thermal_cable_foundation)
    
    return {
        "cable_network": thermal_cable_foundation,
        "tracing_capability": cable_tracing_framework,
        "uncertainty_bounds": quantify_thermal_cable_uncertainty(thermal_complexity)
    }
```

## 🧮 CORE CAPABILITIES UNLOCKED

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Thermal Cable Network Analysis
- **Conduction cable mapping**: Tracing solid material energy paths with thermal resistances
- **Convection cable modeling**: Dynamic fluid thermal transport network architecture  
- **Radiation cable assessment**: Electromagnetic energy transfer pathway identification
- **Thermal resistance network topology**: Complete cable system from source to sink
- **Junction-to-ambient cable tracing**: Full thermal energy path mapping
- **Heat source cable origination**: Understanding energy injection points into networks

### Fluid Thermal Cable Analysis  
- **Reynolds number cable characterization**: Flow regime impact on thermal transport
- **Nusselt number cable coefficients**: Heat transfer enhancement in fluid cables
- **Pressure drop cable resistance**: Flow restriction impact on thermal transport
- **Natural/forced convection cable selection**: Passive vs active thermal transport cables
- **Mass-thermal coupling cables**: Combined mass and energy transport networks

### Material Thermal Cable Properties
- **Thermal conductivity cable capacity**: Material-specific energy transport capability
- **Temperature-dependent cable variations**: How thermal properties change with cable loading
- **Thermal interface cable bottlenecks**: Contact resistance impact on energy flow networks
- **Composite material cable architectures**: Multi-material thermal transport networks
- **Cable degradation mechanisms**: How thermal cycling affects cable performance

## 🔗 THERMAL CABLE NETWORK FUNDAMENTALS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Network Resistance Architecture
```python
# Conduction Cable Resistance
R_conduction_cable = L_cable / (k_material * A_cross_section)  # [K/W]

# Convection Cable Resistance  
R_convection_cable = 1 / (h_coefficient * A_surface)  # [K/W]

# Interface Cable Bottleneck Resistance
R_interface_cable = R_contact + R_spreading  # [K/W]

# Thermal Cable Network Total Resistance
R_thermal_network = f(R_series_cables, R_parallel_cables)

# Energy Flow Through Cable Network
Q_cable = ΔT_network / R_thermal_network    # [W]
```

### Fluid Thermal Cable Characterization
```python
# Reynolds Number (Flow Cable Characterization)
Re_cable = ρ_fluid * V_cable * D_hydraulic / μ_fluid

# Nusselt Number (Thermal Cable Enhancement)
Nu_cable = f(Re_cable, Pr_fluid, geometry_factor)

# Thermal Cable Heat Transfer Coefficient
h_cable = Nu_cable * k_fluid / D_characteristic
```

## 🧠 METACOGNITIVE THERMAL UNCERTAINTY DETECTION

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### When to Load Additional Thermal Cable Knowledge
```python
def assess_thermal_uncertainty(current_analysis):
    """Detect when thermal intuition needs JITC knowledge support"""
    
    uncertainty_flags = {
        "temperature_prediction_variance": calculate_temp_variance(current_analysis),
        "thermal_resistance_confidence": assess_resistance_uncertainty(current_analysis),
        "heat_transfer_coefficient_stability": check_htc_stability(current_analysis),
        "material_property_certainty": validate_material_properties(current_analysis)
    }
    
    # Trigger JITC loading if uncertainty exceeds thresholds
    for flag, value in uncertainty_flags.items():
        if value > thermal_uncertainty_threshold[flag]:
            return {
                "trigger": flag,
                "load_module": determine_required_module(flag),
                "uncertainty_level": value
            }
    
    return "thermal_fundamentals_sufficient"
```

### Typical Thermal Cable Resistances
```python
thermal_cable_resistances = {
    "silicon_die_to_case_cable": "0.5-2.0 K/W",
    "thermal_interface_cable_bottleneck": "0.1-1.0 K·cm²/W", 
    "heat_sink_natural_convection_cable": "10-50 K/W",
    "heat_sink_forced_convection_cable": "1-10 K/W",
    "convection_to_ambient_cable": "5-100 K/W",
    "pcb_trace_conduction_cable": "0.01-0.1 K/W",
    "via_thermal_cable": "0.001-0.01 K/W",
    "enclosure_wall_cable": "1-20 K/W"
}
```

### Thermal Cable Network Dependencies
```python
cable_dependencies = {
    "conduction_cables": {
        "depends_on": ["material_conductivity", "geometry", "temperature_gradient"],
        "affects": ["temperature_distribution", "heat_flux_density", "thermal_stress"]
    },
    "convection_cables": {
        "depends_on": ["fluid_properties", "flow_regime", "surface_geometry"],
        "affects": ["heat_transfer_rate", "pressure_drop", "flow_stability"]
    },
    "interface_cables": {
        "depends_on": ["surface_finish", "contact_pressure", "thermal_interface_material"],
        "affects": ["system_thermal_resistance", "hot_spot_temperature", "reliability"]
    }
}
```

## 🎯 THERMAL CABLE OUTPUTS TO OTHER MODULES

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### To Systems Module - Thermal Cable Architecture
```python
thermal_cable_foundation_output = {
    "thermal_cable_network_topology": "Complete energy flow network architecture",
    "cable_resistance_budget": "R_thermal allocations across cable network",
    "thermal_cable_coefficients": "h values for convective cable segments",
    "cable_temperature_limits": "Component thermal constraints along energy paths",
    "material_cable_properties": "k, ρ, cp for cable network modeling",
    "cable_coupling_interfaces": "Thermal-fluid-structural cable dependencies"
}
```

### To Analysis Module - Thermal Cable Validation Framework
```python
thermal_cable_analysis_foundation = {
    "cable_network_equations": "Energy flow equations for cable networks",
    "thermal_cable_boundary_conditions": "Energy injection/extraction points", 
    "cable_material_models": "Temperature-dependent cable properties",
    "cable_validation_criteria": "Thermal cable network accuracy targets",
    "uncertainty_propagation": "How thermal uncertainty flows through cables"
}
```

### To Materials Module - Thermal Property Cable Dependencies
```python
thermal_material_cable_connections = {
    "conductivity_cable_impact": "How k affects energy transport capacity",
    "interface_cable_bottlenecks": "Contact resistance cable limitations",
    "thermal_expansion_cable_stress": "Thermal cycling effects on cable integrity",
    "material_selection_cable_optimization": "Cable performance vs material choice"
}
```

### To Integration Module - Multi-Physics Cable Coupling
```python
thermal_integration_cables = {
    "thermal_structural_cables": "Thermal stress coupling through mechanical systems",
    "thermal_electromagnetic_cables": "Heat generation from EM systems",
    "thermal_fluid_cables": "Mass-energy transport coupling networks",
    "thermal_manufacturing_cables": "Process thermal effects on cable performance"
}
```

## 🚨 CRITICAL THERMAL LIMITS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Component Temperature Limits
```python
component_temp_limits = {
    "silicon_junction": "125-150°C typical",
    "aluminum_electrolytic": "85-105°C",
    "plastic_enclosures": "60-80°C",
    "solder_joints": "100-125°C",
    "human_touch": "45°C (15 min exposure)"
}
```

### Heat Flux Thresholds
```python
heat_flux_categories = {
    "natural_convection": "< 1 W/cm²",
    "enhanced_natural": "1-5 W/cm²", 
    "forced_air": "5-50 W/cm²",
    "liquid_cooling": "50-1000 W/cm²",
    "phase_change": "> 1000 W/cm²"
}
```

---

## 🔍 THERMAL CABLE TRACING PROTOCOLS

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Network Navigation
```python
def trace_thermal_cable(heat_source, thermal_sink, system_geometry):
    """Follow thermal energy cables from source to sink"""
    
    cable_path = []
    current_node = heat_source
    
    while current_node != thermal_sink:
        # Identify next cable segment
        next_segment = find_dominant_thermal_cable(current_node, system_geometry)
        
        # Calculate cable resistance and energy flow
        cable_resistance = calculate_cable_resistance(next_segment)
        energy_flow = calculate_energy_flow(next_segment)
        
        # Document cable characteristics
        cable_path.append({
            "segment": next_segment,
            "resistance": cable_resistance,
            "energy_flow": energy_flow,
            "bottleneck_risk": assess_bottleneck_risk(cable_resistance),
            "thermal_stress": calculate_thermal_stress(next_segment)
        })
        
        current_node = next_segment.end_node
    
    return cable_path
```

### Thermal Cable Network Validation
```python
def validate_thermal_cable_network(cable_network):
    """Ensure thermal cable network integrity"""
    
    validation_results = {
        "energy_conservation": verify_energy_conservation(cable_network),
        "temperature_continuity": check_temperature_continuity(cable_network),
        "no_thermal_loops": detect_thermal_loops(cable_network),
        "cable_capacity_adequate": verify_cable_capacity(cable_network),
        "bottleneck_identification": identify_thermal_bottlenecks(cable_network)
    }
    
    return validation_results
```

---

**Thermal Cable Network Foundation Established:** Ready for thermal energy architecture and cable tracing.
**Cable Dependencies Mapped:** Multi-physics thermal coupling cables identified.
**Next Steps:** Load systems module for thermal cable system architecture, analysis module for cable validation.

*Thermal cable networks established - heat flows where energy cables direct it.*

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!