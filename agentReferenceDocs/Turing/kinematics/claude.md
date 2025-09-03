# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Turing Kinematics Knowledge Context Menu - Motion Cable Network Navigator

## Follow the Cable Mental Model for Robotic Kinematics

This directory contains kinematic cables that connect joint motion to end-effector positioning through mathematical transformation chains. Following the "Follow the Cable" mental model, each kinematic relationship creates specific motion propagation cables that link joint space to Cartesian space.

### Kinematic Cable Network Architecture

Kinematic analysis creates three primary cable types:

1. **Forward Motion Cables** - Connect joint angles to end-effector positions/orientations
2. **Inverse Motion Cables** - Link desired poses to required joint configurations  
3. **Workspace Boundary Cables** - Define reachable space limits and singularity boundaries

### Just-in-Time Context Framework for Kinematics

Kinematic modules follow the economic principle of context loading - load forward OR inverse kinematics initially based on problem direction, add the complementary module only when bidirectional analysis is required.

## Robotic Kinematics Modules
Select specific kinematic analysis tools:

### Forward Kinematics
```
@load forward_kinematics.md
```
**Contains:**
- DH parameter transformations and analytical solutions
- Standard robot configurations (6-DOF, SCARA, Delta, etc.)
- Velocity forward kinematics and Jacobian computation
- Parallel robot kinematics (Stewart platforms)
- FreeCAD integration for kinematic modeling
- Real-time implementation and optimization

**When to load:** Joint angles → end-effector pose problems, workspace analysis, robot modeling.

**Cable Dependencies Created:**
- Joint Space → Cartesian Space (Forward motion cable)
- DH Parameters → Transformation matrices
- Joint Velocities → End-effector velocities (Jacobian cable)  
- Joint Configurations → Workspace boundaries

### Inverse Kinematics
```
@load inverse_kinematics.md
```
**Contains:**
- Analytical solutions (2-DOF planar, 6-DOF with spherical wrist)
- Numerical methods (Newton-Raphson, damped least squares)
- Multiple solution handling and selection criteria
- Redundant manipulator IK with null space optimization
- Global optimization approaches (PSO, genetic algorithms)
- Real-time IK implementation

**When to load:** End-effector pose → joint angles problems, trajectory planning, robot control.

**Cable Dependencies Created:**
- Cartesian Space → Joint Space (Inverse motion cable)
- Desired Pose → Multiple joint solutions
- Trajectory Points → Joint angle sequences
- Task Constraints → Configuration selection criteria

### Workspace Analysis
```
@load workspace_analysis.md  # (Would be created separately)
```
**Contains:**
- Reachable vs dexterous workspace calculation
- Workspace volume optimization
- Singularity mapping and avoidance
- Joint limit impact on workspace

**When to load:** Robot design optimization, workspace requirements analysis.

**Cable Dependencies Created:**
- Joint Limits → Workspace boundaries
- Kinematic Configuration → Reachable volumes
- Singularities → Workspace holes and degraded regions
- Task Requirements → Robot design constraints

## Usage Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### For Robot Analysis Tasks:
```bash
# Essential mathematical foundation
@load ../foundations/mathematical_foundations.md

# Primary kinematics (choose based on problem direction)
@load forward_kinematics.md          # If you have joint angles, need pose
@load inverse_kinematics.md          # If you have target pose, need joint angles

# Add workspace analysis if optimizing design
@load workspace_analysis.md
```

### For Robot Control Implementation:
```bash
# Mathematical foundations required
@load ../foundations/mathematical_foundations.md

# Both directions needed for control loops
@load forward_kinematics.md
@load inverse_kinematics.md

# Add trajectory planning
@load ../controls/trajectory_generation.md
```

### For Robot Design and Synthesis:
```bash
# Start with mathematics
@load ../foundations/mathematical_foundations.md

# Load comprehensive kinematics
@load forward_kinematics.md
@load inverse_kinematics.md
@load workspace_analysis.md

# Add mechanism knowledge if needed
@load ../mechanisms/four_bar_linkages.md
```

### Metacognitive Triggers - When You Need Kinematic Analysis

**High Uncertainty Signals** (Load kinematic modules immediately):
- "How do I get from joint angles to end-effector position?"
- "What joint angles do I need for this target pose?"
- "Is this pose reachable by the robot?"
- "How many solutions exist for this inverse kinematics problem?"
- "What is the robot's workspace and where are the singularities?"

**Direction-Specific Uncertainty Signals**:
- Joint angles known, pose needed → forward_kinematics.md
- Target pose known, joint angles needed → inverse_kinematics.md  
- Workspace optimization needed → workspace_analysis.md

### Cable Tracing Through Kinematics

When following a kinematic cable through the motion chain:

1. **Identify Motion Direction** - Forward (joints→pose) or inverse (pose→joints)?
2. **Trace Transformation Chain** - How does motion propagate through kinematic links?
3. **Map Solution Dependencies** - What mathematical relationships connect input to output?
4. **Check Singularity Boundaries** - Where do kinematic cables break down?
5. **Validate Motion Feasibility** - Are all poses reachable and all solutions valid?

### Integration with Kinematic Cable Network

Kinematics creates **motion cables** connecting to other kinematic domains:

- **→ Mechanisms**: Kinematic chains become physical linkage systems
- **→ Transmissions**: Joint motion requirements drive gear ratio selection
- **→ Controls**: Kinematic models enable trajectory planning and control
- **→ Applications**: Workspace analysis guides robot design optimization
- **← Mathematical Foundations**: Transformation mathematics enable kinematic solutions

## Loading Decision Matrix

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


| Task Type | Forward | Inverse | Workspace | Foundations |
|-----------|---------|---------|-----------|-------------|
| Joint angles → Pose | ✓ | - | - | ✓ |
| Pose → Joint angles | - | ✓ | - | ✓ |
| Trajectory following | ✓ | ✓ | - | ✓ |
| Robot design | ✓ | ✓ | ✓ | ✓ |
| Workspace optimization | ✓ | ✓ | ✓ | ✓ |
| Singularity analysis | ✓ | ✓ | ✓ | ✓ |
| Control system design | ✓ | ✓ | - | ✓ |

## Quick Context Loading

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Minimum Viable Context (Analysis):
```bash
@load ../foundations/mathematical_foundations.md
@load forward_kinematics.md  # OR inverse_kinematics.md
```

### Full Kinematics Context (Design):
```bash
@load ../foundations/mathematical_foundations.md
@load forward_kinematics.md
@load inverse_kinematics.md
@load workspace_analysis.md
```

### Integration with Other Domains:
```bash
# For mechanism design
@load ../mechanisms/four_bar_linkages.md

# For control systems  
@load ../controls/trajectory_generation.md

# For gear/transmission design
@load ../transmissions/cycloidal_drives.md
```

## Module Descriptions

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**forward_kinematics.md**: The computational foundation - transforms joint space to Cartesian space with mathematical precision. Essential for robot modeling and simulation.

**inverse_kinematics.md**: The problem solver - finds joint configurations for desired poses. Critical for robot control and path planning.

**workspace_analysis.md**: The optimizer - analyzes and optimizes robot reach and dexterity. Key for robot design and task planning.

**Memory Efficiency**: Load forward_kinematics.md OR inverse_kinematics.md initially, add the other only when bidirectional analysis is needed.

### Cable Integrity Verification for Kinematics

**Common Cable Breaks in Kinematic Networks**:
- Forward/inverse kinematic solutions that don't match (mathematical inconsistency)
- Joint configurations that exceed workspace boundaries
- Singular configurations breaking motion transmission
- Invalid DH parameters creating impossible kinematic chains

**Cable Integrity Verification**:
```python
def verify_kinematic_cable_integrity():
    forward_inverse_consistency = check_fk_ik_consistency()
    workspace_validity = verify_workspace_boundaries()  
    singularity_analysis = map_singular_configurations()
    dh_parameter_validity = validate_dh_parameters()
    
    return all([forward_inverse_consistency, workspace_validity,
                singularity_analysis, dh_parameter_validity])
```

### Navigation Priority for Kinematics

1. **Load mathematical foundations first** (Enable transformation mathematics)
2. **Identify problem direction** (Forward OR inverse initially)
3. **Follow motion cables** through transformation chains
4. **Add complementary modules** when bidirectional analysis needed
5. **Verify kinematic consistency** throughout motion network
6. **Validate with physical constraints** from mechanism design

Remember: Kinematic cables carry motion from joints to end-effector through mathematical transformation chains. Every transformation represents a physical link that must exist in the real mechanism. Broken kinematic cables mean impossible robot configurations.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!