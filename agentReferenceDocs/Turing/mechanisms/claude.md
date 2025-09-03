# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Turing Mechanisms Knowledge Context Menu - Mechanical Motion Cable Navigator

## Follow the Cable Mental Model for Mechanism Design

This directory contains mechanical motion cables that connect input motions to desired output motions through physical linkage networks. Following the "Follow the Cable" mental model, each mechanism creates specific motion transformation cables that convert one type of motion into another through geometric constraints.

### Mechanism Cable Network Architecture

Mechanism design creates four primary cable types:

1. **Motion Transformation Cables** - Connect input motion to output motion through linkage geometry
2. **Force Transmission Cables** - Link input forces to output forces with mechanical advantage
3. **Constraint Propagation Cables** - Enforce geometric relationships between mechanism links
4. **Design Synthesis Cables** - Bridge motion requirements to physical linkage dimensions

### Just-in-Time Context Framework for Mechanisms

Mechanism modules follow strategic loading - start with four_bar_linkages.md as the universal foundation, then add specialized mechanisms based on motion complexity and precision requirements.

## Mechanism Design Modules
Select specific mechanism knowledge for your design task:

### Four-Bar Linkages
```
@load four_bar_linkages.md
```
**Contains:**
- Grashof's criterion and mechanism classification
- Complete position, velocity, and acceleration analysis
- Transmission angle optimization for force efficiency
- Coupler curve generation and analysis (straight-line, figure-8, complex paths)
- Synthesis methods (function generation, path generation)
- FreeCAD implementation and animation tools

**When to load:** Fundamental mechanism design, motion transformation, coupler curve generation.

**Cable Dependencies Created:**
- Input Motion → Output Motion (through coupler curves and transmission angles)
- Link Dimensions → Motion Characteristics (via Grashof analysis)
- Force Input → Force Output (through mechanical advantage cables)
- Motion Requirements → Linkage Synthesis (design cables)

### Complex Linkages
```
@load complex_linkages.md  # (Would be created separately)
```
**Contains:**
- Six-bar and eight-bar mechanisms
- Straight-line mechanisms (Peaucellier, Watt, Chebyshev)
- Quick-return mechanisms (Whitworth, crank-shaper)
- Toggle mechanisms and force multiplication
- Multi-loop mechanisms

**When to load:** Advanced motion requirements, precision straight-line motion, force amplification.

**Cable Dependencies Created:**
- Complex Motion Requirements → Multi-loop mechanisms
- Straight-line Requirements → Peaucellier/Watt linkage synthesis
- Force Amplification → Toggle mechanism geometry
- Specialized Tasks → Six-bar/eight-bar configurations

### Cam Mechanisms
```
@load cam_mechanisms.md  # (Would be created separately)
```
**Contains:**
- Cam profile generation from motion specifications
- Follower types (radial, offset, oscillating)
- Pressure angle analysis and optimization
- Manufacturing considerations for cam profiles

**When to load:** Precise timing requirements, complex motion profiles, indexing applications.

**Cable Dependencies Created:**
- Motion Profile Requirements → Cam geometry synthesis
- Timing Requirements → Follower motion laws
- Force/Pressure Constraints → Cam curvature and pressure angles
- Manufacturing Constraints → Cam profile manufacturing methods

### Compliant Mechanisms
```
@load ../compliant_mechanisms.md  # (Existing file, would need to be moved)
```
**Contains:**
- Pseudo-rigid-body modeling
- Flexural hinges and springs
- Topology optimization for compliant systems
- Manufacturing for 3D printed flexures

**When to load:** Monolithic mechanisms, precision positioning, eliminating mechanical play.

**Cable Dependencies Created:**
- Precision Requirements → Flexural hinge design
- Monolithic Constraints → Pseudo-rigid-body modeling
- Manufacturing Methods → 3D printed flexure optimization
- Force/Deflection Relations → Spring constant synthesis

## Usage Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### For Basic Mechanism Design:
```bash
# Mathematical foundations (always required)
@load ../foundations/mathematical_foundations.md

# Core mechanism knowledge
@load four_bar_linkages.md

# Add specialized mechanisms as needed
@load complex_linkages.md       # For advanced motions
@load cam_mechanisms.md         # For timing/profiles
```

### For Motion Synthesis:
```bash
# Essential mathematical framework
@load ../foundations/mathematical_foundations.md

# Primary mechanism synthesis
@load four_bar_linkages.md

# Transmission knowledge if power transmission involved
@load ../transmissions/cycloidal_drives.md
```

### For Precision Motion Applications:
```bash
# Mathematical foundations
@load ../foundations/mathematical_foundations.md

# Precision mechanisms
@load four_bar_linkages.md      # For motion transformation
@load complex_linkages.md       # For straight-line motion
@load ../compliant_mechanisms.md # For play-free motion

# Control integration
@load ../controls/trajectory_generation.md
```

### Metacognitive Triggers - When You Need Mechanism Design

**High Uncertainty Signals** (Load four_bar_linkages.md immediately):
- "How do I convert rotary motion to oscillating motion?"
- "What mechanism gives me straight-line motion?"
- "How do I amplify force in this mechanical system?"
- "What linkage dimensions do I need for this motion path?"
- "How do I design a mechanism with specific velocity ratios?"

**Specialized Motion Uncertainty Signals**:
- Exact straight-line motion needed → complex_linkages.md (Peaucellier, Watt)
- Complex timing profiles needed → cam_mechanisms.md
- Precision without backlash → compliant_mechanisms.md
- Force amplification needed → complex_linkages.md (toggle mechanisms)

### Cable Tracing Through Mechanism Networks

When following a mechanism cable through the motion transformation:

1. **Identify Motion Transformation** - What input motion becomes what output motion?
2. **Trace Geometric Constraints** - How do link dimensions control motion characteristics?
3. **Map Force Transmission** - How do forces flow through the mechanism links?
4. **Check Transmission Angles** - Where do motion cables degrade or break?
5. **Validate Synthesis Requirements** - Do mechanism dimensions achieve desired motion?

### Integration with Mechanism Cable Network

Mechanism design creates **transformation cables** connecting to other kinematic domains:

- **→ Kinematics**: Mechanism links become kinematic chains for analysis
- **→ Transmissions**: Mechanism output connects to gear/transmission input
- **→ Controls**: Mechanism characteristics determine control requirements
- **← Mathematical Foundations**: Geometric constraints enable mechanism synthesis
- **→ Applications**: Mechanism selection drives application-specific integration

## Mechanism Selection Guide

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


| Motion Requirement | Primary Module | Secondary Modules |
|-------------------|----------------|------------------|
| Simple rotation → oscillation | four_bar_linkages.md | - |
| Straight-line motion (approximate) | four_bar_linkages.md | complex_linkages.md |
| Straight-line motion (exact) | complex_linkages.md | four_bar_linkages.md |
| Force amplification | four_bar_linkages.md | complex_linkages.md |
| Complex motion profiles | cam_mechanisms.md | four_bar_linkages.md |
| High-precision positioning | compliant_mechanisms.md | four_bar_linkages.md |
| Quick-return motion | complex_linkages.md | four_bar_linkages.md |
| Intermittent motion | cam_mechanisms.md | complex_linkages.md |

## Loading Strategy by Application

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### General Purpose Mechanism Design:
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
```

### Precision Instrumentation:
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
@load complex_linkages.md
@load ../compliant_mechanisms.md
```

### Manufacturing Equipment:
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
@load complex_linkages.md
@load cam_mechanisms.md
```

### Robotics Applications:
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
@load ../kinematics/forward_kinematics.md
@load ../kinematics/inverse_kinematics.md
```

## Integration Pathways

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### To Kinematics Domain:
```bash
# Mechanism → Robot joint design
@load ../kinematics/forward_kinematics.md
@load ../kinematics/inverse_kinematics.md
```

### To Transmission Domain:
```bash
# Mechanism → Power transmission
@load ../transmissions/cycloidal_drives.md
@load ../transmissions/gear_trains.md
```

### To Control Domain:
```bash
# Mechanism → Motion control
@load ../controls/trajectory_generation.md
@load ../controls/motion_control.md
```

## Quick Reference

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**four_bar_linkages.md**: The universal mechanism - master this first, it's the foundation of all planar mechanism design.

**complex_linkages.md**: Advanced mechanisms for specialized motion requirements.

**cam_mechanisms.md**: Precise timing and complex motion profiles.

**compliant_mechanisms.md**: Monolithic precision mechanisms without mechanical joints.

## Context Size Management

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Minimal Context (Concept):**
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
```

**Focused Context (Specific Application):**
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
@load [specific_mechanism].md
```

**Comprehensive Context (Full Design):**
```bash
@load ../foundations/mathematical_foundations.md
@load four_bar_linkages.md
@load complex_linkages.md
@load cam_mechanisms.md
```

**Remember**: Four-bar linkages are the alphabet of mechanism design - every complex mechanism can be understood as combinations and variations of four-bar chains.

### Cable Integrity Verification for Mechanisms

**Common Cable Breaks in Mechanism Networks**:
- Grashof violations creating impossible motion types
- Poor transmission angles degrading force transmission
- Mechanism synthesis that doesn't achieve desired motion
- Link interference preventing full range of motion

**Cable Integrity Verification**:
```python
def verify_mechanism_cable_integrity():
    grashof_compliance = check_grashof_criterion()
    transmission_angle_validity = verify_transmission_angles()
    motion_synthesis_accuracy = validate_motion_generation()
    link_interference_check = verify_collision_free_motion()
    
    return all([grashof_compliance, transmission_angle_validity,
                motion_synthesis_accuracy, link_interference_check])
```

### Navigation Priority for Mechanisms

1. **Load mathematical foundations first** (Enable geometric synthesis mathematics)
2. **Start with four_bar_linkages.md** (Universal mechanism foundation)  
3. **Follow motion transformation cables** through linkage geometry
4. **Add specialized mechanisms** based on motion complexity
5. **Verify mechanism synthesis** against motion requirements
6. **Validate with physical constraints** from structural and manufacturing limits

Remember: Mechanism cables carry motion transformations through physical linkage geometry. Every geometric constraint represents a real physical connection that must be manufactured and assembled. Broken mechanism cables mean mechanisms that cannot achieve their intended motion or will bind/interfere during operation.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!