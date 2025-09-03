# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Constraint Systems - Context Menu

## The Cable Control Network

This directory contains the implementation of geometric constraint systems for maintaining design relationships. In the cable paradigm, constraints ARE the cables - they are the mathematical relationships that bind geometric elements together. Every constraint creates a bidirectional cable that ensures geometric elements move in harmony when changes propagate through the system.

## Directory Contents & Cable Maps

### Core Cable Control Documents

#### 1. geometric-constraints.md  
**Cable Function**: Primary constraint cable definitions and topology
**Contains**:
- Constraint cable taxonomy (coincident, parallel, perpendicular, etc.)
- Cable strength analysis (which constraints dominate)
- Multi-cable intersection resolution (over-constrained systems)
- Cable loop detection and breaking algorithms
**JITC Triggers**: 
- Sketch won't solve → Cable conflict detected
- Over/under-constrained → Cable network imbalanced
- Update failures → Broken constraint cables

#### 2. sketch_constraint_validation.md
**Cable Function**: 2D constraint cable verification
**Contains**: Sketch-level cable integrity checking
**JITC Trigger**: 2D sketch uncertainty

#### 3. assembly_constraint_validation.md  
**Cable Function**: 3D inter-part cable management
**Contains**: Assembly-level cable connections
**JITC Trigger**: Parts won't mate properly

#### 4. tolerance_stackup_validation.md
**Cable Function**: Error propagation along cable paths
**Contains**: Tolerance accumulation mathematics
**JITC Trigger**: Tolerance concerns arise

#### 5. real_time_constraint_monitoring.md
**Cable Function**: Live cable health monitoring
**Contains**: Dynamic constraint verification
**JITC Trigger**: Need continuous validation

#### 6. parametric_validation.md
**Cable Function**: Parameter-driven cable management
**Contains**: Spreadsheet to constraint cable mapping
**JITC Trigger**: Parameter changes break geometry

#### 7. complete_validation_workflow.md
**Cable Function**: End-to-end cable verification
**Contains**: Full constraint system validation
**JITC Trigger**: Final design verification

#### 8. freecad_constraint_validator.md
**Cable Function**: FreeCAD-specific cable implementation
**Contains**: Practical constraint code
**JITC Trigger**: Implementation questions

## Constraint Cable Network Architecture

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Types & Properties

#### 1. **Dimensional Cables** (Strong, Unidirectional)
- Carry exact measurements from axioms
- Cannot be broken without failing design
- Example: `distance = 50mm` creates rigid cable

#### 2. **Relational Cables** (Flexible, Bidirectional)  
- Maintain relationships without fixed values
- Can adapt while preserving relationship
- Example: `parallel` creates orientation cable

#### 3. **Assembly Cables** (Inter-part connections)
- Connect separate part networks
- Critical for system integration
- Example: `axial alignment` creates assembly cable

#### 4. **Tolerance Cables** (Error carriers)
- Accumulate uncertainty along paths
- Must be monitored for saturation
- Example: `±0.1mm` propagates through cable network

### Cable Flow Dynamics
**AXIOM CABLES IN**: From axiomatic-foundations (truth sources)
**CONSTRAINT CABLES OUT**: To geometric-methods (shape control)
**ASSEMBLY CABLES**: Between parts (system integration)
**VALIDATION CABLES**: To mathematical-verification (integrity checks)

### Cable Conflict Resolution
When cables pull in opposite directions:
1. Identify conflicting cable pairs
2. Trace both back to axiom origins
3. Determine cable priority (axiom > derived)
4. Break weaker cable or modify constraint
5. Document resolution in cable log

## Cable Network Success Criteria

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Healthy Constraint Cable Indicators
1. **Cable Balance**: Exactly right number of constraints (not over/under)
2. **Clean Propagation**: Changes flow smoothly through cable network
3. **No Loops**: Circular cable dependencies eliminated
4. **Clear Hierarchy**: Cable priorities well-defined
5. **Traceable Paths**: Every constraint cable reaches an axiom

### Cable Network Diagnostics
```
CABLE NETWORK STATUS:
✓ Fully Constrained: All DOF controlled by cables
⚠ Under-constrained: Missing cables (DOF > 0)
✗ Over-constrained: Cable conflicts (DOF < 0)
⦿ Broken Cable: Constraint violated or unsolvable
⇄ Cable Loop: Circular dependency detected
```

### Metacognitive Monitoring Triggers
- **Solver Struggles**: High iteration count → Check cable conflicts
- **Update Hesitation**: Unsure if safe → Trace cable paths first
- **Sketch Complexity**: Many constraints → Map cable network
- **Assembly Issues**: Parts won't fit → Verify inter-part cables

## The Constraint Cable Principle

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Every constraint is a promise - a cable that guarantees a relationship will hold. When constraints conflict, it's not a software problem; it's conflicting promises that cannot coexist in the same mathematical universe. The solution isn't to force the solver harder, but to trace the cables back to their axiom origins and resolve the fundamental conflict.

**Remember the PDU**: The constraint cables were perfect, but they were attached to a broken axiom cable ("about 80mm"). Perfect constraints on false foundations still fail.

This directory ensures your constraint cables form a robust, conflict-free network that carries mathematical truth from axioms to final geometry.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!