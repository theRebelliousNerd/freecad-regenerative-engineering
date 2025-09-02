# CFD Simulation Guide for Thermal Systems

*"We don't need full CFD to get 90% accurate results."* - Watt's CFD Efficiency Principle

## Executive Summary

Computational Fluid Dynamics (CFD) is a powerful tool for thermal analysis, but it must be applied judiciously. Most thermal design problems can be solved with simplified analytical methods and empirical correlations. CFD should be reserved for complex geometries, optimization studies, or when detailed flow visualization is required. This guide provides a systematic approach to CFD analysis that balances accuracy with computational efficiency.

## When to Use CFD vs Analytical Methods

### Use Analytical Methods When:
- Geometry is relatively simple (rectangular ducts, standard heat sinks)
- Flow is primarily one-dimensional
- Preliminary design sizing needed
- Quick parametric studies required
- Design confidence needed rapidly

### Use CFD When:
- Complex three-dimensional geometries
- Flow separation or recirculation expected
- Detailed temperature distribution mapping needed
- Optimization of specific geometric features
- Validation of analytical predictions required
- Multiple design alternatives need comparison

### CFD-Light Approach Benefits:
- 90% accuracy in 10% of the computational time
- Results available in hours, not days
- Parameter studies feasible
- Physical insight more accessible than full CFD

## CFD Software Platform Guidance

### Professional CFD Software (2024-2025)

**ANSYS Fluent:**
- Industry standard for thermal analysis
- Excellent turbulence models and heat transfer correlations
- Strong meshing capabilities (ANSYS Mesh)
- Extensive validation database
- Cost: High ($50K+ annually)

**Siemens STAR-CCM+:**
- Excellent for electronics cooling (integrated with Simcenter Flotherm)
- Automated meshing with high quality
- Integrated design optimization
- Good parallel processing scaling
- Cost: High ($40K+ annually)

**ANSYS Icepak:**
- Specialized for electronics thermal management
- Integrated with ANSYS Electronics Desktop
- Component libraries for standard parts
- Simplified setup for PCB and enclosure analysis
- Cost: High ($30K+ annually)

### Open Source and Academic CFD

**OpenFOAM:**
- Free and highly customizable
- Excellent solver algorithms
- Steep learning curve
- Extensive validation studies available
- Good for research and development

**SU2:**
- Open source, originally for aerospace
- Good computational efficiency
- Limited thermal-specific features
- Cost: Free

### Cloud-Based CFD (2024 Trend)

**SimScale:**
- Browser-based CFD platform
- Good for basic thermal analysis
- Reasonable cost structure
- Limited advanced features
- Cost: $2K-10K annually

**OnShape + SimScale Integration:**
- CAD-integrated CFD workflow
- Good for product design teams
- Simplified setup process

## CFD Modeling Best Practices

### Geometry Preparation

**Geometry Simplification Strategy:**
1. **Remove unnecessary details**: Small fillets, screws, minor features
2. **Simplify complex shapes**: Use equivalent rectangular channels for complex ducts
3. **Create fluid domains**: Extract the air/fluid volumes for CFD analysis
4. **Seal all openings**: CFD requires watertight domains

**Critical Dimension Guidelines:**
- Minimum feature size: >1/100 of domain size
- Fillet radius: >1/200 of adjacent surface dimension
- Gap size: >1/500 of channel dimension

**Defeaturing Checklist:**
- [ ] Remove features <1mm if domain >100mm
- [ ] Combine small adjacent surfaces
- [ ] Simplify bolt patterns to equivalent blockages
- [ ] Replace complex curved surfaces with faceted approximations
- [ ] Remove internal components that don't affect flow significantly

### Mesh Generation Strategy

**Mesh Quality Requirements:**
- **Aspect ratio**: <20 for general cells, <100 near walls
- **Orthogonality**: >0.1 (angle between face normal and adjacent cell centers)
- **Skewness**: <0.8 for tetrahedral, <0.9 for hexahedral
- **Growth ratio**: <1.3 between adjacent cells

**Y+ Requirements for Wall Treatment:**
```
y+ = ρ·u_τ·y₁/μ
where u_τ = √(τ_wall/ρ) = friction velocity
```

**Wall Treatment Guidelines:**
- **y+ < 1**: Enhanced wall treatment (accurate but expensive)
- **30 < y+ < 300**: Standard wall functions (good compromise)
- **y+ > 300**: Poor accuracy, avoid

**Mesh Density Guidelines:**
- **Heat source surfaces**: 5-10 elements across smallest dimension
- **Heat sink fins**: 3-5 elements across fin thickness
- **Flow channels**: 8-15 elements across hydraulic diameter
- **Boundary layer**: 5-10 prism layers for accurate heat transfer

### Boundary Condition Setup

**Thermal Boundary Conditions:**

*Constant Heat Flux (q"):*
```
q" = P_component / A_surface  [W/m²]
```
- Use for: Electronic components with known power dissipation
- Advantage: Direct representation of component behavior

*Constant Temperature:*
```
T_wall = T_junction - P × R_jc
```
- Use for: Components with good thermal regulation
- Advantage: Simplifies convergence

*Convection Boundary:*
```
q" = h_external × (T_wall - T_ambient)
```
- Use for: External surfaces with known heat transfer coefficient
- Advantage: Accounts for external thermal resistance

**Flow Boundary Conditions:**

*Velocity Inlet:*
- Use when: Fan curve and system resistance known
- Specify: Velocity magnitude, turbulence intensity (5-20%), temperature

*Pressure Inlet/Outlet:*
- Use when: Pressure differences known, natural convection
- Specify: Gauge pressure, turbulence intensity, temperature

*Mass Flow Inlet:*
- Use when: Exact mass flow rate required
- Specify: Mass flow rate, turbulence intensity, temperature

**Turbulence Model Selection:**

*k-ε Standard:*
- Good for: High Reynolds number flows, far from walls
- Limitation: Poor near-wall accuracy without wall functions

*k-ω SST:*
- Good for: Flows with adverse pressure gradients, separation
- Advantage: Accurate near-wall treatment
- Recommended for most thermal applications

*Laminar Model:*
- Use when: Re < 2300 in internal flows, Re < 5×10⁵ for external flows
- Advantage: No turbulence modeling errors
- Limitation: Limited to low Reynolds number applications

### Solution Strategy

**Solution Initialization:**
1. Start with laminar flow solution for initial velocity field
2. Switch to turbulent model with low relaxation factors
3. Gradually increase relaxation factors as solution stabilizes

**Relaxation Factor Guidelines:**
- **Pressure**: 0.3 (most critical for stability)
- **Momentum**: 0.5-0.7
- **Energy**: 0.8-1.0
- **Turbulence**: 0.5-0.8

**Convergence Criteria:**
- **Residuals**: <10⁻⁴ for continuity, momentum; <10⁻⁶ for energy
- **Heat Balance**: Heat in = Heat out within 1%
- **Monitor Points**: Temperature stable to within 0.1K over 100 iterations

## Conjugate Heat Transfer (CHT) Modeling

### CHT Setup Strategy

**Coupled vs Segregated Solvers:**
- **Coupled**: Better for high temperature gradients, faster convergence
- **Segregated**: More memory efficient, better for complex geometries

**Material Property Assignment:**
- **Solids**: Define thermal conductivity, density, specific heat
- **Fluids**: Temperature-dependent properties critical for accuracy
- **Interfaces**: Ensure thermal continuity between domains

**Interface Treatment:**
```
k_solid × (∂T/∂n)|solid = k_fluid × (∂T/∂n)|fluid
```

### Advanced CHT Considerations

**Contact Resistance:**
- Model thin TIM layers as thermal resistance boundaries
- Use wall thermal resistance boundary condition
- Account for interface pressure effects on TIM performance

**Radiation Modeling:**
- Include for surface temperatures >100°C
- Use Surface-to-Surface (S2S) model for enclosed geometries
- Use Discrete Ordinates (DO) model for participating media

**Transient CHT:**
- Critical for power cycling analysis
- Requires proper time step selection: Δt < 0.1 × τ_smallest
- Consider thermal capacity of all solid domains

## Validation and Verification

### CFD Model Validation Process

**Step 1: Code Verification**
- Use analytical solutions for simple geometries
- Verify mesh convergence with successive refinement
- Check conservation of mass, momentum, and energy

**Step 2: Model Validation**
- Compare with experimental data when available
- Use empirical correlations for heat transfer coefficients
- Validate pressure drop predictions against handbook values

**Step 3: Solution Verification**
- Check residual convergence
- Verify heat balance closure
- Confirm independence from initial conditions

### Experimental Validation Methods (2024 Standards)

**Temperature Measurement:**
- **Thermocouples**: ±1-2°C accuracy, good for validation points
- **IR Thermography**: Surface temperature mapping for comparison
- **RTDs**: ±0.3°C accuracy for reference measurements

**Heat Flux Measurement:**
- **Hukseflux FHF05**: Direct heat flux measurement for boundary conditions
- **Thermoelectric Coolers**: Controlled heat input for validation
- **Calorimetry**: Total heat transfer measurement for system validation

**Flow Measurement:**
- **Hot-wire anemometers**: Point velocity measurements
- **PIV (Particle Image Velocimetry)**: Flow field visualization
- **Pressure taps**: Static pressure distribution measurement

### Validation Acceptance Criteria

**Temperature Predictions:**
- **Excellent**: ±2°C or ±5% of temperature rise
- **Good**: ±5°C or ±10% of temperature rise
- **Acceptable**: ±8°C or ±15% of temperature rise

**Pressure Drop Predictions:**
- **Excellent**: ±10%
- **Good**: ±20%
- **Acceptable**: ±30%

**Heat Transfer Coefficients:**
- **Excellent**: ±15%
- **Good**: ±25%
- **Acceptable**: ±40%

## Parametric Studies and Optimization

### Design of Experiments (DOE) Approach

**Parameter Selection:**
- Choose 3-7 most influential design variables
- Include geometric, material, and operating parameters
- Consider manufacturing constraints in parameter ranges

**DOE Methods:**
- **Full Factorial**: 2ⁿ design for n parameters
- **Box-Behnken**: Efficient for response surface creation
- **Latin Hypercube**: Good for high-dimensional spaces

**Response Variables:**
- Maximum temperature
- Heat transfer coefficient  
- Pressure drop
- Fan power requirement
- Temperature uniformity

### Optimization Integration

**Single-Objective Optimization:**
- Minimize maximum temperature
- Minimize pressure drop
- Minimize thermal resistance

**Multi-Objective Optimization:**
- Pareto frontier between competing objectives
- Weighted objective functions
- Constraint-based optimization

**Optimization Algorithms:**
- **Genetic Algorithm**: Global optimization, handles discrete variables
- **Gradient-based**: Local optimization, fast convergence
- **Response Surface**: Efficient for smooth design spaces

## Post-Processing and Results Analysis

### Temperature Field Analysis

**Hot Spot Identification:**
- Maximum temperature locations
- Temperature gradient magnitude
- Thermal stress concentration regions

**Temperature Distribution Metrics:**
- **Maximum temperature**: Critical for component reliability
- **Temperature uniformity**: σ/μ for temperature distribution
- **Temperature rise**: Above inlet or ambient conditions

### Flow Field Analysis

**Velocity Field Visualization:**
- Streamlines for flow path understanding
- Vector plots for flow direction and magnitude
- Recirculation zone identification

**Pressure Field Analysis:**
- Static pressure distribution
- Pressure drop breakdown by component
- Flow separation regions

### Heat Transfer Analysis

**Heat Flux Visualization:**
- Surface heat flux magnitude and direction
- Heat flux lines for thermal path identification
- Local heat transfer coefficient distribution

**Performance Metrics:**
- **Overall thermal resistance**: R = ΔT_max/P_total
- **Heat transfer effectiveness**: ε = Q_actual/Q_max
- **Thermal performance factor**: TPF = (Nu/Nu₀)/(f/f₀)^(1/3)

## Common CFD Pitfalls and Solutions

### Meshing Problems

**Problem**: High aspect ratio cells in boundary layer
**Solution**: Use prism layer meshing with proper growth rate

**Problem**: Poor mesh quality in complex geometry regions
**Solution**: Simplify geometry or use hybrid meshing approaches

**Problem**: Mesh too coarse for accurate heat transfer
**Solution**: Mesh independence study with systematic refinement

### Boundary Condition Errors

**Problem**: Incorrect heat flux specification
**Solution**: Verify power dissipation data with component specifications

**Problem**: Wrong turbulence intensity values
**Solution**: Use 5% for low turbulence, 20% for high turbulence inlet conditions

**Problem**: Inappropriate wall treatment for y+ values
**Solution**: Check y+ distribution and select appropriate wall model

### Convergence Issues

**Problem**: Residuals oscillating or not decreasing
**Solution**: Reduce relaxation factors, check mesh quality

**Problem**: Heat balance not closing
**Solution**: Verify boundary conditions, check for leakage in domain

**Problem**: Solution dependent on initial conditions
**Solution**: Try different initialization methods, check for multiple solutions

## CFD Software Specific Guidelines

### ANSYS Fluent Best Practices

**Mesh Setup:**
- Use ANSYS Mesh with physics-based sizing
- Enable proximity and curvature refinement
- Use inflation layers for near-wall resolution

**Solver Settings:**
- Use Coupled solver for better convergence
- Enable Expert Mode for advanced controls
- Use adaptive time stepping for transient analysis

**Post-Processing:**
- Use CFD-Post for advanced visualization
- Export data for external analysis tools
- Create custom field functions for derived quantities

### OpenFOAM Workflow

**Case Setup:**
- Use standard tutorials as templates
- Validate mesh with checkMesh utility
- Set up proper initial and boundary conditions

**Solver Selection:**
- buoyantSimpleFoam: Natural convection problems
- buoyantPimpleFoam: Transient thermal problems
- conjugateHeatFoam: Conjugate heat transfer

**Post-Processing:**
- Use paraView for visualization
- Python scripts for data extraction
- Validation plots with experimental data

## Integration with CAD Workflow

### FreeCAD to CFD Workflow

**Geometry Preparation:**
1. Export assembly from FreeCAD as STEP file
2. Import into CFD preprocessor
3. Extract fluid domains
4. Simplify geometry for CFD requirements

**Parameter Passing:**
- Geometric dimensions from FreeCAD parameters
- Material properties from FreeCAD material database
- Heat loads from electrical analysis tools

**Results Integration:**
- Import temperature fields for thermal stress analysis
- Update heat transfer coefficients for simplified models
- Validate design performance against requirements

## Quality Assurance Checklist

Before accepting CFD results:

### Mesh Quality
- [ ] Mesh independence study completed
- [ ] y+ values appropriate for wall treatment
- [ ] Aspect ratios within acceptable limits
- [ ] No highly skewed or negative volume cells

### Physics Setup  
- [ ] Appropriate turbulence model selected
- [ ] Boundary conditions physically realistic
- [ ] Material properties temperature-dependent where significant
- [ ] Gravity direction correctly specified for natural convection

### Solution Quality
- [ ] Residuals converged to acceptable levels
- [ ] Heat balance closed within 1%
- [ ] Solution independent of initialization
- [ ] Monitor points stabilized

### Validation
- [ ] Results compared with analytical predictions
- [ ] Key non-dimensional numbers calculated and verified
- [ ] Physical reasonableness checked (no negative temperatures, etc.)
- [ ] Uncertainty quantification performed

Remember: "CFD is a powerful tool, but it is not a replacement for understanding the underlying physics." Every CFD study should begin with analytical estimates and end with physical validation. The goal is not just to get numbers, but to gain insight that leads to better thermal design decisions.

Use CFD to answer specific questions that analytical methods cannot address. Avoid the temptation to model everything in detail - simplicity often provides better engineering insight than complexity.