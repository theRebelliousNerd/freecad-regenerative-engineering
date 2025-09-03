# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Applications Directory - Human Factors Cable Network Navigator

## Just-in-Time Context Framework for Human Factors Applications

This directory contains application-specific human factors knowledge modules. Following the "Follow the Cable" mental model, each application domain creates specific safety, usability, and accessibility "cables" that connect throughout the entire system.

### Cable Network Architecture

Human factors applications create three primary cable types:

1. **Safety Cables** - Connect human vulnerability points to system design constraints
2. **Usability Cables** - Link human cognitive/physical capabilities to interface requirements  
3. **Accessibility Cables** - Bridge diverse human abilities to universal design solutions

### Directory Structure & Just-in-Time Loading

#### Interface/ - Digital Interaction Cables
**When to Load**: Digital interfaces, control panels, software UI, AR/VR systems
```python
if project.has_digital_interface() or project.involves_human_computer_interaction():
    load_context("Applications/Interface/claude.md")
```

**Cable Dependencies**: 
- Vision cables → Display specifications, contrast, font sizing
- Motor cables → Touch targets, click precision, gesture tolerance
- Cognitive cables → Information architecture, workflow complexity

#### Manufacturing/ - Industrial Human Factors Cables  
**When to Load**: Factory design, worker safety, production ergonomics
```python
if project.involves_manufacturing() or project.has_workers_in_production():
    load_context("Applications/Manufacturing/claude.md")  
```

**Cable Dependencies**:
- Strength cables → Lifting limits, force requirements, tool weight
- Postural cables → Work height, reach envelopes, repetitive motion
- Environmental cables → Noise, vibration, temperature, lighting

#### Systems/ - Complex System Integration Cables
**When to Load**: Multi-component systems, FreeCAD integration, system-level design
```python
if project.involves_system_integration() or project.uses_freecad():
    load_context("Applications/Systems/claude.md")
```

**Cable Dependencies**:
- Integration cables → How human factors propagate across subsystems
- Validation cables → Testing protocols for human-system interaction
- Scaling cables → How human constraints affect system architecture

### Metacognitive Triggers - When You Need This Directory

**High Uncertainty Signals** (Load immediately):
- "How do users interact with this system?"
- "What are the safety implications for operators?"
- "Will this design accommodate diverse user populations?"
- "How do we validate human factors in this application?"

**Domain-Specific Uncertainty** (Load specific subdirectory):
- Interface questions → Interface/
- Manufacturing questions → Manufacturing/  
- System integration questions → Systems/

### Cable Tracing Through Applications

When following a human factors cable through applications:

1. **Identify Human Touchpoint** - Where do humans interact with the system?
2. **Trace Safety Dependencies** - What could harm the human?
3. **Map Usability Requirements** - What capabilities must the human have?
4. **Check Accessibility Needs** - What accommodations are required?
5. **Validate System Response** - How does the system adapt to human variability?

### Integration with Agent Network

Human factors applications create **meta-cables** connecting to other agents:

- **→ Brunel**: Structural safety limits based on human force application
- **→ Edison**: Interface specifications for human-electronics interaction  
- **→ Tesla**: Motor control systems that respond safely to human commands
- **→ Watt**: Environmental controls for human comfort zones
- **→ Gabe**: Manufacturing constraints based on human assembly capabilities
- **→ Archimedes**: Mathematical verification of human factors constraints

### Critical Path Analysis

**Always Critical** (Cannot be bypassed):
- Safety standards and injury prevention
- Legal accessibility compliance
- Basic ergonomic accommodation

**Context Critical** (Load based on application):
- Specific industry standards
- Advanced usability optimization  
- Specialized population considerations

### Failure Mode Prevention

**Common Cable Breaks**:
- Designing interfaces without considering motor limitations
- Creating systems that exceed cognitive capacity
- Ignoring accessibility requirements until late in design
- Failing to validate human factors assumptions

**Cable Integrity Verification**:
```python
def verify_application_cables():
    safety_verified = check_injury_risk_mitigation()
    usability_verified = check_task_completion_capability()  
    accessibility_verified = check_universal_design_compliance()
    
    return all([safety_verified, usability_verified, accessibility_verified])
```

### Navigation Priority

1. **Load Core principles first** (from parent Vitruvius directory)
2. **Identify primary application domain** (Interface/Manufacturing/Systems)
3. **Follow uncertainty signals** to specific subdirectory
4. **Verify cable integrity** throughout application network
5. **Validate with real humans** whenever possible

Remember: Human factors applications are not just about making things "user-friendly" - they're about creating safety, usability, and accessibility cables that protect and empower every human who interacts with the system. Every design decision creates consequences that propagate through these cables to real human lives.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!