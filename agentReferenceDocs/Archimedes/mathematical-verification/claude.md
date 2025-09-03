# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Mathematical Verification - Context Menu

## Cable Integrity Verification Hub

This directory contains the computational implementation of Archimedean verification methods for ensuring mathematical certainty in FreeCAD designs. In the cable paradigm, this is where we VERIFY that all cables are intact, properly connected, and carrying valid mathematical signals. Every cable from axioms to implementation must pass through verification here.

## Directory Contents

### 1. method-of-exhaustion.md
**When to read**: When verifying complex surfaces, volumes, or curved geometries
**Contains**:
- Implementation of Archimedes' Method of Exhaustion for modern CAD
- Surface area calculation with guaranteed bounds
- Clearance verification between complex surfaces  
- Volume calculation using nested polyhedra
- Curvature analysis with bounded uncertainty
**Triggers**: Complex surface verification, curved geometry analysis, clearance checking between non-trivial shapes

### 2. interval-arithmetic.md
**When to read**: When dealing with dimensional tolerances and uncertainty propagation  
**Contains**:
- Complete interval arithmetic implementation for CAD calculations
- Arithmetic operations preserving bounds through all calculations
- Distance and volume calculations with tolerance propagation
- Constraint verification using guaranteed bounds
- Integration with FreeCAD dimensional analysis
**Triggers**: Tolerance stack-up analysis, uncertainty quantification, dimensional chain calculations

### 3. certificates-of-soundness.md
**When to read**: ALWAYS before finalizing any component or proceeding to next design phase
**Contains**:
- Complete Certificate of Mathematical Soundness framework
- Standard certificate templates and digital signatures
- Integration with FreeCAD automatic certificate generation  
- Certificate database and retrieval systems
- Design gate integration requiring certificates
**Triggers**: Component completion, design phase transitions, verification documentation needed

## Reading Priority & Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**VERIFICATION WORKFLOW** (use in this sequence):
1. method-of-exhaustion.md → For complex geometry verification
2. interval-arithmetic.md → For tolerance and uncertainty analysis  
3. certificates-of-soundness.md → For formal certification and documentation

**METHOD-SPECIFIC READING**:
- Complex surfaces → method-of-exhaustion.md
- Tolerance analysis → interval-arithmetic.md
- Final verification → certificates-of-soundness.md

## Cable Verification Architecture

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Testing Protocols
1. **Continuity Testing**: Verify cable connects axiom to implementation without breaks
2. **Signal Integrity**: Ensure mathematical truth propagates without distortion
3. **Load Testing**: Verify cable can handle tolerance accumulation
4. **Cross-Cable Interference**: Check for conflicting constraints
5. **Cable Certification**: Issue certificates for verified cable paths

### Cable Flow Monitoring
**INPUT CABLES FROM**: axiomatic-foundations (axiom cables to verify)
**VERIFICATION CABLES TO**: geometric-methods (certified geometry cables)
**VALIDATION CABLES TO**: constraint-systems (verified constraint networks)
**CERTIFICATE CABLES TO**: All downstream agents (proof of cable integrity)

### JITC Context Triggers
- **Uncertainty Signal > 0.05**: Cable might be degrading → Load interval-arithmetic.md
- **Complex Geometry**: Multiple cable intersections → Load method-of-exhaustion.md
- **Phase Gate**: Cable certification required → Load certificates-of-soundness.md
- **Tolerance Cascade**: Cable carrying accumulated error → Load entire directory

## Critical Decision Matrix

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


| Verification Need | Primary Method | Supporting Method | Certificate Required |
|------------------|----------------|-------------------|---------------------|
| Surface clearance | Method of Exhaustion | Interval Arithmetic | Yes |
| Dimensional chains | Interval Arithmetic | - | Yes |
| Volume calculations | Method of Exhaustion | Interval Arithmetic | Yes |  
| Curved surfaces | Method of Exhaustion | - | Yes |
| Tolerance analysis | Interval Arithmetic | - | Yes |
| Final design approval | - | - | MANDATORY |

## Task-Specific Loading

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Complex Surface Verification**: Read 1 then 3
**Tolerance Stack Analysis**: Read 2 then 3  
**Component Finalization**: Read 3 (MANDATORY)
**Uncertainty Quantification**: Read 2 first, then 1 if needed
**Design Gates**: Read 3 for requirements

## Cable Failure Detection

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Critical Cable Failures (STOP WORK):
- **Unbounded Approximation**: Cable carrying undefined signal → Cannot verify
- **Tolerance Explosion**: Cable error exceeds design limits → Trace back to source
- **Certification Void**: Cable lacks verification certificate → Cannot proceed
- **Convergence Failure**: Method of Exhaustion cannot bound → Cable too complex

### Metacognitive Cable Monitoring:
- **Weak Signal**: Values near tolerance limits → Strengthen cable or add redundancy
- **Cable Oscillation**: Conflicting constraints → Identify and resolve loops
- **Orphaned Results**: Output with no input cable → Invalid computation
- **Certificate Expiry**: Design changed after certification → Re-verify cables

## Cable Integrity Success Criteria

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


After verification, every cable should have:
1. **Traceable Path**: Complete cable route from axiom to implementation
2. **Bounded Signal**: Mathematical bounds at every cable node
3. **Certification Status**: Formal certificate with cable ID and timestamp
4. **Tolerance Budget**: Accumulated error within acceptable limits
5. **Redundancy Check**: Critical cables have backup paths
6. **No Orphans**: Every result traces to an axiom cable

### Cable Health Dashboard
```
CABLE STATUS INDICATORS:
✓ Green Cable: Verified, certified, within tolerance
⚠ Yellow Cable: Near limits, monitor closely  
✗ Red Cable: Broken, exceeds tolerance, or uncertified
⦿ Orphan Node: No cable connection to axioms
```

## Computational Requirements

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


These methods require:
- SymPy for symbolic mathematics
- NumPy for numerical calculations
- SciPy for optimization and advanced mathematics
- Proper error handling for convergence failures
- Database system for certificate storage

## The Cable Verification Manifesto

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Every mathematical operation creates or modifies a cable. This directory ensures:
- No cable carries false signals (incorrect mathematics)
- No cable breaks under load (tolerance accumulation)
- No cable exists without purpose (orphaned calculations)
- Every cable is certified before use (verification gates)

**Remember the PDU**: One broken cable ("about 80mm") invalidated months of perfect downstream work.

This directory transforms computational checking into cable certification, ensuring that mathematical truth flows unbroken from axioms to reality.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!