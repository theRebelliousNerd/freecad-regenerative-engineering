# FreeCAD MCP Thermal Workflows and Material Integration
## Comprehensive Guide for Curie Agent FreeCAD Operations

*"Geometry exists only when thermally and materially proven sound."* - Curie FreeCAD Principle

## MCP Tool Integration Strategy

### Core MCP Function Categories for Curie Agent

#### 1. View Control and Documentation
```python
# Screenshot thermal analysis results
mcp__freecad__view_control({
    "operation": "screenshot",
    "width": 1200,
    "height": 800,
    "filename": "thermal_analysis_results.png"
})

# Set optimal view for thermal analysis
mcp__freecad__view_control({
    "operation": "set_view", 
    "view_type": "isometric"
})
```

#### 2. Part Operations for Thermal Components
```python
# Create heat sink fin geometry
mcp__freecad__part_operations({
    "operation": "box",
    "length": 50,    # mm
    "width": 2,      # fin thickness
    "height": 30,    # fin height
    "name": "heat_sink_fin"
})

# Create thermal interface volumes
mcp__freecad__part_operations({
    "operation": "cylinder",
    "radius": 12.5,  # CPU contact area
    "height": 0.1,   # TIM thickness
    "name": "thermal_interface"
})
```

#### 3. Advanced Material Property Application
```python
# Apply thermal materials with full property sets
mcp__freecad__execute_python({
    "code": """
    import FreeCAD
    import Materials
    from FreeCAD import Units
    
    def apply_curie_thermal_material(part_name, material_data):
        '''Apply comprehensive thermal material properties'''
        part = FreeCAD.ActiveDocument.getObject(part_name)
        
        # Create new material with thermal properties
        material = Materials.createMaterial()
        
        # Basic identification
        material.Name = material_data['name']
        material.Description = material_data['description']
        
        # Mechanical properties
        material.YoungsModulus = Units.Quantity(material_data['youngs_modulus'], 'Pa')
        material.PoissonRatio = material_data['poisson_ratio']
        material.Density = Units.Quantity(material_data['density'], 'kg/m^3')
        
        # Thermal properties (critical for Curie analysis)
        material.ThermalConductivity = Units.Quantity(material_data['thermal_conductivity'], 'W/m/K')
        material.ThermalExpansionCoefficient = Units.Quantity(material_data['thermal_expansion'], '1/K')
        material.SpecificHeat = Units.Quantity(material_data['specific_heat'], 'J/kg/K')
        
        # Electrical properties (for electromagnetic coupling)
        if 'electrical_conductivity' in material_data:
            material.ElectricalConductivity = Units.Quantity(material_data['electrical_conductivity'], 'S/m')
        
        # Custom thermal properties for advanced analysis
        material.addProperty('App::PropertyFloat', 'ThermalDiffusivity')
        material.ThermalDiffusivity = material_data['thermal_conductivity'] / (
            material_data['density'] * material_data['specific_heat']
        )
        
        # Temperature limits for validation
        material.addProperty('App::PropertyFloat', 'MaxOperatingTemp')
        material.MaxOperatingTemp = material_data.get('max_temp', 100.0)
        
        # Sustainability metrics
        material.addProperty('App::PropertyFloat', 'CarbonFootprint')
        material.CarbonFootprint = material_data.get('carbon_footprint', 0.0)
        
        # Manufacturing process compatibility
        material.addProperty('App::PropertyString', 'ManufacturingProcess')
        material.ManufacturingProcess = material_data.get('process', 'Unknown')
        
        # Apply to part
        part.Material = material
        
        return material
    
    # Example: Apply copper heat sink material
    copper_hs_data = {
        'name': 'Copper_101_HeatSink',
        'description': 'High thermal conductivity copper for heat sink applications',
        'youngs_modulus': 110e9,      # Pa
        'poisson_ratio': 0.34,
        'density': 8960,              # kg/m³
        'thermal_conductivity': 401,   # W/m·K
        'thermal_expansion': 16.5e-6,  # 1/K
        'specific_heat': 385,          # J/kg·K
        'electrical_conductivity': 5.96e7,  # S/m
        'max_temp': 200,               # °C
        'carbon_footprint': 3.2,       # kg CO₂/kg
        'process': '3D_Printing_Metal'
    }
    
    apply_curie_thermal_material('heat_sink_base', copper_hs_data)
    """
})
```

## Thermal Analysis Workflow Patterns

### 1. Heat Sink Design and Optimization

```python
def design_heat_sink_workflow(power_dissipation, max_temp_rise):
    """Complete heat sink design workflow"""
    
    # Step 1: Calculate thermal resistance requirement
    thermal_resistance_required = max_temp_rise / power_dissipation
    
    # Step 2: Create base heat sink geometry
    mcp__freecad__part_operations({
        "operation": "box",
        "length": 60,
        "width": 60, 
        "height": 10,
        "name": "heat_sink_base"
    })
    
    # Step 3: Create fin array
    fin_count = 12
    fin_spacing = 5.0  # mm
    
    for i in range(fin_count):
        mcp__freecad__part_operations({
            "operation": "box",
            "length": 60,
            "width": 2,
            "height": 30,
            "x": 0,
            "y": i * fin_spacing - (fin_count * fin_spacing / 2),
            "z": 10,
            "name": f"fin_{i}"
        })
    
    # Step 4: Boolean union all fins to base
    fin_names = [f"fin_{i}" for i in range(fin_count)]
    mcp__freecad__part_operations({
        "operation": "fuse",
        "objects": ["heat_sink_base"] + fin_names,
        "name": "complete_heat_sink"
    })
    
    # Step 5: Apply thermal material properties
    mcp__freecad__execute_python({
        "code": f"""
        # Calculate actual thermal resistance and validate
        import math
        
        # Natural convection heat transfer coefficient (W/m²·K)
        h_natural = 10  # Conservative estimate for vertical fins
        
        # Fin efficiency calculation
        fin_height = 0.030  # 30mm in meters
        fin_thickness = 0.002  # 2mm in meters
        k_fin = 401  # W/m·K for copper
        
        m = math.sqrt(2 * h_natural / (k_fin * fin_thickness))
        fin_efficiency = math.tanh(m * fin_height) / (m * fin_height)
        
        # Total surface area (base + fins)
        base_area = 0.06 * 0.06  # m²
        fin_area_each = 2 * 0.06 * 0.030  # Both sides
        total_fin_area = {fin_count} * fin_area_each * fin_efficiency
        
        total_area = base_area + total_fin_area
        
        # Thermal resistance
        R_thermal_calc = 1 / (h_natural * total_area)
        
        print(f"Calculated thermal resistance: {{R_thermal_calc:.3f}} K/W")
        print(f"Required thermal resistance: {{thermal_resistance_required:.3f}} K/W")
        print(f"Design margin: {{(R_thermal_calc / {thermal_resistance_required} - 1) * 100:.1f}}%")
        
        # Validation
        if R_thermal_calc <= {thermal_resistance_required}:
            print("Heat sink design PASSES thermal requirements")
        else:
            print("Heat sink design FAILS - increase surface area or use forced convection")
        """
    })
    
    return "complete_heat_sink"
```

### 2. Thermal Interface Material (TIM) Analysis

```python
def analyze_thermal_interface_workflow(component_power, junction_area):
    """Analyze TIM requirements and create geometry"""
    
    # Calculate heat flux density
    heat_flux = component_power / (junction_area * 1e-6)  # W/m²
    
    # Step 1: Create component geometry (CPU/chip)
    mcp__freecad__part_operations({
        "operation": "box",
        "length": math.sqrt(junction_area),
        "width": math.sqrt(junction_area),
        "height": 1.5,  # Typical chip thickness
        "name": "heat_source_component"
    })
    
    # Step 2: Create TIM layer geometry
    tim_thickness = select_optimal_tim_thickness(heat_flux)
    
    mcp__freecad__part_operations({
        "operation": "box", 
        "length": math.sqrt(junction_area) + 1,  # Slight overhang
        "width": math.sqrt(junction_area) + 1,
        "height": tim_thickness,
        "z": 1.5,  # On top of component
        "name": "thermal_interface_material"
    })
    
    # Step 3: Apply TIM material properties
    tim_material = select_tim_material(heat_flux)
    
    mcp__freecad__execute_python({
        "code": f"""
        # Apply TIM material properties
        tim_data = {tim_material}
        apply_curie_thermal_material('thermal_interface_material', tim_data)
        
        # Calculate thermal resistance
        tim_area = {junction_area} * 1e-6  # Convert mm² to m²
        tim_thickness = {tim_thickness} * 1e-3  # Convert mm to m
        k_tim = tim_data['thermal_conductivity']
        
        R_tim = tim_thickness / (k_tim * tim_area)
        
        print(f"TIM thermal resistance: {{R_tim*1000:.2f}} K/W")
        print(f"Heat flux density: {{{heat_flux/10000:.1f}}} W/cm²")
        print(f"Selected TIM: {{tim_data['name']}}")
        """
    })

def select_tim_material(heat_flux_w_per_m2):
    """Select appropriate TIM based on heat flux"""
    heat_flux_w_per_cm2 = heat_flux_w_per_m2 / 10000
    
    if heat_flux_w_per_cm2 < 1:
        return {
            'name': 'Standard_Thermal_Paste',
            'thermal_conductivity': 3.0,
            'max_temp': 150,
            'cost_factor': 1.0
        }
    elif heat_flux_w_per_cm2 < 5:
        return {
            'name': 'High_Performance_Paste', 
            'thermal_conductivity': 8.0,
            'max_temp': 180,
            'cost_factor': 2.0
        }
    elif heat_flux_w_per_cm2 < 20:
        return {
            'name': 'Phase_Change_Material',
            'thermal_conductivity': 4.0,
            'max_temp': 125,
            'cost_factor': 3.0
        }
    else:
        return {
            'name': 'Liquid_Metal_TIM',
            'thermal_conductivity': 50.0,
            'max_temp': 200,
            'cost_factor': 10.0
        }
```

### 3. Multi-Material Thermal Expansion Analysis

```python
def thermal_expansion_analysis_workflow(materials_list, temp_range):
    """Analyze thermal expansion compatibility between materials"""
    
    # Create multi-material assembly
    for i, material in enumerate(materials_list):
        mcp__freecad__part_operations({
            "operation": "cylinder",
            "radius": 10 - i,  # Nested cylinders
            "height": 20,
            "name": f"material_layer_{i}"
        })
        
        # Apply material properties
        mcp__freecad__execute_python({
            "code": f"""
            material_data = {material}
            apply_curie_thermal_material('material_layer_{i}', material_data)
            """
        })
    
    # Analyze thermal stress
    mcp__freecad__execute_python({
        "code": f"""
        import math
        
        temp_delta = {temp_range[1]} - {temp_range[0]}
        materials = {materials_list}
        
        print("Thermal Expansion Analysis:")
        print("=" * 50)
        
        for i, material in enumerate(materials):
            alpha = material['thermal_expansion']
            initial_radius = 10 - i
            
            expansion = alpha * initial_radius * temp_delta * 1000  # Convert to microns
            
            print(f"Layer {{i}} ({{material['name']}}): {{expansion:.1f}} μm expansion")
            
            if i > 0:
                prev_alpha = materials[i-1]['thermal_expansion'] 
                differential_expansion = abs(alpha - prev_alpha) * initial_radius * temp_delta * 1000
                
                if differential_expansion > 10:  # Critical threshold
                    print(f"  WARNING: {{differential_expansion:.1f}} μm differential expansion")
                    print(f"  Consider stress relief features or material change")
        
        # Calculate thermal stress (simplified)
        max_stress = 0
        for i in range(len(materials)-1):
            E1 = materials[i]['youngs_modulus'] 
            E2 = materials[i+1]['youngs_modulus']
            alpha1 = materials[i]['thermal_expansion']
            alpha2 = materials[i+1]['thermal_expansion']
            
            # Simplified bi-material thermal stress
            stress = abs(alpha1 - alpha2) * temp_delta * E1 * E2 / (E1 + E2)
            max_stress = max(max_stress, stress)
        
        print(f"Maximum thermal stress: {{max_stress/1e6:.1f}} MPa")
        """
    })
```

### 4. Electronics Cooling Integration Workflow

```python
def electronics_cooling_integration(pcb_components, ambient_temp, max_junction_temp):
    """Integrate electronics cooling with thermal analysis"""
    
    # Step 1: Create PCB base geometry
    mcp__freecad__part_operations({
        "operation": "box",
        "length": 100,  # PCB length
        "width": 80,    # PCB width  
        "height": 1.6,  # Standard PCB thickness
        "name": "pcb_substrate"
    })
    
    # Step 2: Create component geometries and analyze each
    total_power = 0
    for comp in pcb_components:
        # Create component geometry
        mcp__freecad__part_operations({
            "operation": "box",
            "length": comp['length'],
            "width": comp['width'], 
            "height": comp['height'],
            "x": comp['x_pos'],
            "y": comp['y_pos'],
            "z": 1.6,  # On top of PCB
            "name": comp['name']
        })
        
        total_power += comp['power']
        
        # Analyze component thermal requirements
        junction_to_case_resistance = comp.get('rth_jc', 10)  # K/W
        case_to_ambient_required = (max_junction_temp - ambient_temp) / comp['power'] - junction_to_case_resistance
        
        # Determine cooling solution
        if case_to_ambient_required > 20:  # Natural convection sufficient
            cooling_solution = "natural_convection"
        elif case_to_ambient_required > 5:  # Small heat sink needed
            cooling_solution = "small_heat_sink"
        else:  # Active cooling required
            cooling_solution = "forced_convection"
        
        print(f"Component {comp['name']}: {cooling_solution} required")
        
        # Create cooling geometry if needed
        if cooling_solution == "small_heat_sink":
            create_component_heat_sink(comp['name'], comp['power'], case_to_ambient_required)
    
    # Step 3: Overall PCB thermal analysis
    mcp__freecad__execute_python({
        "code": f"""
        # PCB thermal analysis
        pcb_area = 0.1 * 0.08  # m²
        total_power = {total_power}
        power_density = total_power / pcb_area
        
        print(f"PCB Power Density: {{power_density:.1f}} W/m²")
        
        if power_density > 5000:  # W/m²
            print("High power density PCB - consider:")
            print("- Thermal vias under high-power components")  
            print("- Metal core PCB substrates")
            print("- Component placement optimization")
            print("- Active cooling (fan)")
        
        # Estimate PCB temperature rise
        h_natural_pcb = 8  # W/m²·K for horizontal PCB
        delta_T_pcb = power_density / h_natural_pcb
        
        print(f"Estimated PCB temperature rise: {{delta_T_pcb:.1f}} K")
        print(f"Estimated PCB temperature: {{ambient_temp + delta_T_pcb:.1f}} °C")
        """
    })

def create_component_heat_sink(component_name, power, required_resistance):
    """Create appropriately sized heat sink for component"""
    
    # Simple heat sink sizing
    fin_area_needed = 1 / (10 * required_resistance)  # Assuming h=10 W/m²·K
    fin_count = max(3, int(fin_area_needed * 1000))  # Minimum 3 fins
    
    mcp__freecad__part_operations({
        "operation": "box",
        "length": 20,
        "width": 20, 
        "height": 3,
        "name": f"{component_name}_hs_base"
    })
    
    for i in range(fin_count):
        mcp__freecad__part_operations({
            "operation": "box", 
            "length": 20,
            "width": 1,
            "height": 15,
            "y": i * 2 - fin_count,
            "z": 3,
            "name": f"{component_name}_fin_{i}"
        })
```

## Material Validation and Testing Protocols

### 1. Material Property Validation

```python
def validate_material_properties(material_name):
    """Validate applied material properties against database"""
    
    mcp__freecad__execute_python({
        "code": f"""
        import FreeCAD
        
        # Get material from part
        part = FreeCAD.ActiveDocument.getObject('{material_name}')
        material = part.Material
        
        # Validation checks
        validation_results = {{}}
        
        # Check thermal conductivity range
        k = material.ThermalConductivity.Value
        if k <= 0:
            validation_results['thermal_conductivity'] = 'FAIL: Non-positive value'
        elif k > 500:  # W/m·K - check for unrealistic values
            validation_results['thermal_conductivity'] = 'WARNING: Unusually high value'
        else:
            validation_results['thermal_conductivity'] = 'PASS'
        
        # Check thermal expansion coefficient
        alpha = material.ThermalExpansionCoefficient.Value
        if alpha < 0:
            validation_results['thermal_expansion'] = 'FAIL: Negative expansion'
        elif alpha > 100e-6:  # 1/K - extremely high expansion
            validation_results['thermal_expansion'] = 'WARNING: Very high expansion'
        else:
            validation_results['thermal_expansion'] = 'PASS'
        
        # Check density reasonableness
        density = material.Density.Value
        if density <= 0 or density > 25000:  # kg/m³
            validation_results['density'] = 'FAIL: Unrealistic density'
        else:
            validation_results['density'] = 'PASS'
        
        # Temperature limits check
        if hasattr(material, 'MaxOperatingTemp'):
            max_temp = material.MaxOperatingTemp
            if max_temp < -273:  # Below absolute zero
                validation_results['temperature_limit'] = 'FAIL: Below absolute zero'
            elif max_temp > 3000:  # Unrealistically high for most materials
                validation_results['temperature_limit'] = 'WARNING: Extremely high temperature'
            else:
                validation_results['temperature_limit'] = 'PASS'
        
        # Report validation results
        print(f"Material Validation Results for {{material.Name}}:")
        print("=" * 50)
        for property_name, result in validation_results.items():
            print(f"{{property_name:20}}: {{result}}")
        
        # Overall assessment
        failures = [k for k, v in validation_results.items() if 'FAIL' in v]
        warnings = [k for k, v in validation_results.items() if 'WARNING' in v]
        
        if failures:
            print(f"\\nOVERALL: FAIL - {{len(failures)}} critical issues")
            return False
        elif warnings:
            print(f"\\nOVERALL: PASS with {{len(warnings)}} warnings")
            return True
        else:
            print("\\nOVERALL: PASS - All properties validated")
            return True
        """
    })
```

This comprehensive FreeCAD integration framework ensures that Curie agent can effectively implement thermal analysis and material selection directly within the FreeCAD environment, maintaining full traceability and validation of all thermal design decisions.