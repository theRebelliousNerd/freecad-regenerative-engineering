# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Foundational Principles - Manufacturing Physics as Natural Law

## Overview
This directory contains the core manufacturing physics that govern 3D printing. These are not guidelines but natural laws - as immutable as gravity. Every "cable" in the Follow the Cable model traces back to these fundamental constraints.

## Follow the Cable Mental Model Integration

### Manufacturing Constraints as Cables
In the Follow the Cable framework, manufacturing constraints are not limitations but **dependency cables** that connect design decisions to physical reality. Each manufacturing principle creates cables that propagate throughout the entire design network:

- **Wall thickness constraints** → cables to nozzle diameter → cables to material flow → cables to structural integrity
- **Layer adhesion properties** → cables to print orientation → cables to stress paths → cables to failure modes  
- **Thermal behavior** → cables to material selection → cables to part geometry → cables to cooling requirements
- **Support requirements** → cables to overhang angles → cables to surface finish → cables to post-processing time

### The Manufacturing Cable Network
Manufacturing is the **prime mover** in the cable network - it reaches backward to constrain all upstream design decisions. A 0.4mm nozzle diameter isn't a preference; it's a physical quantum that cables backward through:
- Minimum wall thickness (1.2mm = 3 perimeters)
- Feature resolution limits
- Internal channel dimensions
- Assembly clearances
- Overall part proportions

## Just-in-Time Context (JITC) Application

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Metacognitive Triggers for Manufacturing Uncertainty
The JITC framework helps recognize when manufacturing knowledge gaps emerge:

**High-Certainty Scenarios** (low retrieval threshold):
- Standard wall thicknesses with proven materials
- Simple geometries within established design rules
- Well-characterized print orientations

**High-Uncertainty Scenarios** (immediate knowledge retrieval):
- Novel material combinations
- Complex multi-physics interactions (thermal + structural)
- Untested geometric features
- Production scaling challenges

### Context Retrieval Priorities
When manufacturing uncertainty is detected, prioritize loading:
1. **Core principles** (this directory) - always loaded first
2. **Material-specific constraints** - based on material selection
3. **Geometry-specific rules** - based on feature complexity
4. **Latest research** - for novel applications or failure modes

## Directory Structure and When to Load Each File

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🔥 Always Load First (Core Physics)
```
slant_3d_core_principles.md - The 8 immutable rules of mass production
anisotropic_behavior.md - Layer-by-layer strength characteristics 
support_elimination_strategies.md - 45° rule and self-supporting geometry
```

### 📐 Load by Geometric Complexity
```
01_wall_thickness_and_structural_integrity.md
WHEN: Any part with walls, ribs, or structural elements
CABLES: nozzle_diameter → wall_thickness → structural_integrity → load_capacity

02_anisotropic_nature_of_fdm.md  
WHEN: Parts experiencing multi-directional loads
CABLES: print_orientation → layer_adhesion → stress_concentration → failure_mode

05_tolerances_in_fdm.md
WHEN: Precision assemblies or tight-fitting parts
CABLES: material_shrinkage → print_precision → assembly_clearances → fit_quality
```

### 🌡️ Load by Thermal Requirements
```
04_thermal_dynamics_management.md
WHEN: Parts with heat-generating components or thermal cycling
CABLES: operating_temperature → material_selection → geometry_constraints → cooling_strategy
```

### 🏗️ Load by Production Phase
```
03_first_layer_optimization.md
WHEN: Optimizing for automated production or adhesion issues
CABLES: first_layer → bed_adhesion → part_ejection → automation_feasibility

overhang_management.md
WHEN: Complex geometries with overhangs or bridges
CABLES: overhang_angle → support_requirements → surface_finish → post_processing
```

## Manufacturing Cable Tracing Examples

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Trace: Wall Thickness Decision
```
Design Decision: "Make enclosure wall 0.6mm thick"
↓
Manufacturing Cable Analysis:
- 0.6mm < 1.2mm minimum → VIOLATION
- 0.4mm nozzle × 3 perimeters = 1.2mm minimum
- 0.6mm = 1.5 perimeters → impossible to print reliably
↓
Cable Propagation:
- Structural integrity compromised → increased failure risk
- Print quality degraded → higher defect rate  
- Production yield reduced → increased cost
- Customer satisfaction impacted → market risk
↓
Resolution: Increase wall thickness to 1.2mm minimum
```

### Cable Trace: Print Orientation Selection
```
Design Decision: "Print part flat on build plate"
↓
Manufacturing Cable Analysis:
- Flat orientation → large bed contact area
- Large contact area → difficult automated ejection
- Difficult ejection → manual intervention required
- Manual intervention → breaks automation cable
↓
Alternative Orientation Analysis:
- 45° angle → minimal bed contact
- Minimal contact → easy ejection
- Easy ejection → maintains automation
- BUT: may introduce overhangs requiring supports
↓
Resolution: Redesign geometry to eliminate overhangs at 45° orientation
```

## Key Manufacturing Cables by Category

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Nozzle Diameter Cable (0.4mm Standard)**
- **Destinations**: Wall thickness, feature resolution, print speed, material flow
- **Critical Path**: All geometric constraints trace back to this fundamental quantum
- **When to Question**: Never - this is a manufacturing axiom

### **Layer Adhesion Cable**
- **Destinations**: Part strength, print orientation, failure modes
- **Critical Path**: Mechanical design → stress analysis → layer orientation
- **When to Question**: When parts fail along layer lines

### **Thermal Management Cable**  
- **Destinations**: Material selection, cooling requirements, part geometry
- **Critical Path**: Heat sources → thermal paths → material limits
- **When to Question**: When dealing with heat-generating components

### **Support Elimination Cable**
- **Destinations**: Surface finish, print time, post-processing labor
- **Critical Path**: Geometry design → overhang angles → support requirements
- **When to Question**: When supports become unavoidable

## Metacognitive Manufacturing Awareness

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### When You KNOW You Know
- Standard PLA/PETG with proven geometries
- Wall thicknesses ≥1.2mm 
- Print angles ≤45° overhangs
- Assembly clearances ≥0.2mm

### When You KNOW You Don't Know (Research Trigger)
- Novel materials or material combinations
- Complex thermal interactions
- Micro-scale features (<1mm)
- High-precision assemblies (<0.1mm tolerance)
- Production volumes >10,000 units

### When You Don't Know You Don't Know (Danger Zone)
- Assumptions about material behavior
- Untested geometric features  
- Scaling effects in mass production
- Long-term reliability under stress

## Manufacturing Reality Enforcement Protocol

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


As Gabe, you are the guardian of manufacturing reality. When you detect violations of these foundational principles:

1. **STOP** - Do not proceed with violated design
2. **TRACE** - Follow the cable back to the root decision
3. **EDUCATE** - Explain the physical reality behind the constraint
4. **REDESIGN** - Propose manufacturing-compatible alternatives
5. **VALIDATE** - Confirm the solution satisfies all manufacturing cables

Remember: Every manufacturing constraint is a **cable** in the system's nervous system. Cutting a cable breaks the entire network. Your role is to ensure the integrity of the manufacturing cable network while enabling maximum design creativity within physical reality.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!