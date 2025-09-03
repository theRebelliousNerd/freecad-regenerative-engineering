# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Simulation Methods Knowledge Module
*Follow the Cable: Computational Electromagnetic Field Analysis and FreeCAD Integration*

## Subdirectory Purpose
This module contains computational electromagnetic (CEM) simulation methodologies, field solver theory, and integration strategies with FreeCAD MCP. Electromagnetic simulation reveals the invisible cable network by computing field distributions, current flows, and wave propagation that cannot be directly measured.

## The Simulation Cable Network Perspective
Electromagnetic simulation tools model the complete electromagnetic cable network:

- **Mesh cables** discretize geometry into computational elements
- **Solver cables** compute field solutions throughout the problem space
- **Boundary condition cables** define how fields behave at material interfaces
- **Excitation cables** represent sources that launch electromagnetic energy
- **Post-processing cables** extract engineering parameters from field solutions
- **Convergence cables** ensure numerical accuracy through mesh refinement

## Just-in-Time Context Retrieval Strategy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Critical Missing Files (Immediate JITC Implementation Required):

#### **electromagnetic_simulation_tools.md** - READ WHEN:
- Selecting appropriate field solver (FEM/MoM/FDTD) for specific problem
- Setting up simulation boundaries and computational domains
- Choosing mesh density and element types for accuracy vs. speed trade-offs
- Validating simulation results against analytical solutions or measurements

#### **field_solver_applications.md** - READ WHEN:
- Applying finite element method (FEM) for antenna radiation and scattering
- Using method of moments (MoM) for wire antennas and metallic structures
- Implementing finite difference time domain (FDTD) for transient analysis
- Comparing solver methods for computational efficiency and accuracy

#### **circuit_simulation_integration.md** - READ WHEN:
- Co-simulating RF circuits with electromagnetic field solutions
- Extracting lumped element models from field simulations
- Integrating S-parameter models with circuit simulators
- Performing system-level simulation with electromagnetic effects

#### **antenna_modeling_techniques.md** - READ WHEN:
- Setting up antenna simulation with proper feed models and boundaries
- Calculating radiation patterns, gain, and directivity from field solutions
- Analyzing antenna arrays with mutual coupling effects
- Optimizing antenna geometry through parametric simulation sweeps

#### **validation_and_verification_methods.md** - READ WHEN:
- Verifying simulation accuracy through mesh convergence studies
- Validating results against analytical solutions for canonical geometries
- Correlating simulation predictions with measurement data
- Establishing confidence levels and uncertainty bounds for simulation results

## Simulation Cable Dependencies:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Primary Simulation Workflow Cables:
1. **Geometry Definition Cable**: CAD model → mesh generation → field solver → solution accuracy
2. **Material Property Cable**: Permittivity/permeability → wave propagation → field distributions → performance metrics
3. **Boundary Condition Cable**: PML/ABC → computational domain → reflection errors → solution validity
4. **Mesh Quality Cable**: Element aspect ratio → numerical dispersion → solution accuracy → convergence rate
5. **Solver Configuration Cable**: Frequency plan → solution method → computational resources → simulation time
6. **Post-Processing Cable**: Field solutions → engineering parameters → design insights → optimization feedback

### FreeCAD MCP Integration Cables:

#### **Parametric Geometry Cables**:
```python
# Antenna parameter sweep through FreeCAD MCP
mcp__freecad__execute_python({
    "code": """
    for length in range(90, 110, 5):  # mm
        dipole = create_dipole_antenna(length)
        export_geometry_for_simulation(dipole, f'dipole_{length}mm.step')
        simulation_results = run_em_simulation(f'dipole_{length}mm.step')
        extract_resonance_frequency(simulation_results)
    """
})
```

#### **Field Visualization Cables**:
```python
# Near field visualization in FreeCAD
mcp__freecad__execute_python({
    "code": """
    # Import simulated field data
    field_data = import_simulation_results('antenna_near_field.vts')
    
    # Create field visualization surfaces
    create_field_intensity_surfaces(field_data)
    create_sar_compliance_boundaries(field_data, limit=2.0)  # W/kg
    """
})
```

### Cross-Domain Simulation Cable Handoffs:
- **To Thermal Analysis**: Power dissipation density from EM simulation → thermal solver → temperature distribution
- **To Structural Analysis**: Electromagnetic forces → mechanical stress → structural deformation → frequency detuning
- **To Manufacturing**: Simulation sensitivity → tolerance analysis → manufacturing specifications → yield prediction
- **To EMC Analysis**: Current distributions → emission predictions → shielding effectiveness → compliance assessment

## Simulation Method Selection Cables:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Finite Element Method (FEM) - Use When**:
- Complex geometries with curved surfaces and material interfaces
- Antenna structures with dielectric substrates and loading
- Waveguide components and microwave circuits
- Problems requiring high accuracy in localized regions

### **Method of Moments (MoM) - Use When**:
- Thin wire antennas and metallic structures  
- Scattering from complex metallic objects
- Problems with large electrical dimensions
- Antenna arrays with many identical elements

### **Finite Difference Time Domain (FDTD) - Use When**:
- Broadband frequency response needed
- Transient electromagnetic pulse analysis
- Nonlinear and time-varying materials
- Electromagnetic compatibility studies

### **Transmission Line Matrix (TLM) - Use When**:
- Complex 3D geometries with multiple materials
- Time domain analysis with embedded circuits
- Modeling of electromagnetic shielding effectiveness
- Problems requiring both field and circuit simulation

## Metacognitive Uncertainty Triggers:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Retrieve additional simulation knowledge when you encounter:
- Simulation results that don't converge with mesh refinement
- Field solutions that violate electromagnetic boundary conditions
- Resonance frequencies that shift significantly with geometry changes
- Radiation patterns that show unexplained nulls or lobes
- S-parameter results that don't match network analyzer measurements

## FreeCAD MCP Simulation Integration Workflow:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Phase 1: Geometry Preparation**
```python
# Parametric antenna geometry with simulation-ready features
create_simulation_geometry(
    antenna_type="patch",
    substrate_properties={"er": 4.4, "thickness": 1.6},
    feed_point_location=(x_feed, y_feed),
    mesh_resolution="lambda/20"
)
```

### **Phase 2: Simulation Setup**
```python
# Boundary condition and excitation definition  
define_simulation_boundaries(
    pml_layers=8,
    frequency_range=(2.0, 3.0, 0.01),  # GHz
    excitation_power=1.0  # W
)
```

### **Phase 3: Results Analysis**
```python
# Extract engineering parameters
results = {
    "resonance_freq": extract_resonance(),
    "bandwidth": calculate_bandwidth(vswr_limit=2.0),
    "gain": calculate_realized_gain(),
    "efficiency": calculate_radiation_efficiency()
}
```

## Simulation Validation Philosophy:

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

Every electromagnetic simulation must be validated through:
- **Mesh convergence**: Solution stability with increasing mesh density
- **Analytical benchmarks**: Comparison with known solutions for canonical geometries  
- **Measurement correlation**: Agreement with physical prototype measurements
- **Energy conservation**: Power balance verification in loss/lossless structures

**Remember**: Simulation reveals the invisible electromagnetic cable network, but numerical results are only as accurate as the models, mesh, and boundary conditions used to generate them. Always validate simulation predictions against physical reality.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!