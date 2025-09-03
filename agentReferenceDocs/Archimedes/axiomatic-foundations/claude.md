# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Axiomatic Foundations - Context Menu

## The Origin of All Design Cables

This directory contains the practical implementation of axiomatic principles for establishing mathematical certainty in FreeCAD designs. In the cable paradigm, AXIOMS ARE THE PRIMARY CABLE ORIGINS. Every design element must trace its cable back to an axiom here. A design element without an axiom cable is orphaned geometry - it has no right to exist.

## Directory Contents

### 1. establishing-axioms.md
**When to read**: ALWAYS at project start, before any CAD operations
**Contains**:
- Socratic interrogation protocol for extracting precise requirements
- Axiom formalization in machine-readable formats (JSON/YAML)
- Constraint network building and repository structure  
- Guardian of consistency protocols for change management
**Triggers**: New project start, vague requirements received, need to establish design foundation

### 2. mathematical-constraints.md
**When to read**: When working with constraint systems or tolerance analysis
**Contains**:
- Linear and non-linear constraint mathematics
- Tolerance propagation (worst-case and RSS methods)
- Constraint satisfaction verification algorithms
- Geometric constraint classification and implementation
**Triggers**: Complex constraint systems, tolerance analysis needed, geometric relationships verification

### 3. component-verification.md  
**When to read**: CRITICAL for enclosure design or any physical component integration
**Contains**:
- Component dimension verification hierarchy and confidence levels
- Stack-up analysis requirements and protocols
- Pre-CAD verification gate checklist
- Failure mode prevention based on real project lessons
**Triggers**: Enclosure design, component integration, physical part verification, "about" or "approximately" dimensions encountered

## Reading Priority & Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**MANDATORY SEQUENCE** (for new projects):
1. component-verification.md → Physical reality first
2. establishing-axioms.md → Transform reality into axioms  
3. mathematical-constraints.md → Mathematical framework for axioms

**REFERENCE ORDER** (during design):
- Vague requirements → establishing-axioms.md
- Complex math → mathematical-constraints.md  
- Physical components → component-verification.md

## Axiom Cable Network

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Types Originating Here
1. **Dimension Cables**: Every geometric dimension must cable back to a verified measurement
2. **Constraint Cables**: Mathematical relationships that propagate through the entire design
3. **Tolerance Cables**: Error bounds that accumulate along dependency chains
4. **Component Cables**: Physical reality anchors that ground the abstract design
5. **Requirement Cables**: Every axiom must cable back to a validated requirement

### Cable Propagation Rules
- **Axiom Changes**: Ripple through ALL connected cables (use establishing-axioms.md guardian protocol)
- **Broken Cables**: An unverified dimension = broken cable = cascade failure
- **Tolerance Accumulation**: Follows √(Σ(tolerance²)) along cable paths
- **Confidence Degradation**: Confidence decreases along cable length from axiom

### Critical Cable Paths
**STRONG CABLES FROM**: archimedes-core-philosophy (philosophical constraints)
**AXIOM CABLES TO**: ALL design elements (nothing exists without axiom cable)
**VERIFICATION CABLES TO**: mathematical-verification (proving cable integrity)
**GEOMETRIC CABLES TO**: geometric-methods (manifesting axioms in space)

## Task-Specific Loading

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Project Start**: Read 1 → 2 → 3 in sequence
**Requirements Issues**: Focus on establishing-axioms.md
**Tolerance Problems**: Focus on mathematical-constraints.md
**Component Fit Issues**: Focus on component-verification.md
**Enclosure Design**: component-verification.md is CRITICAL

## Cable Break Detection Signals

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### CRITICAL CABLE BREAKS (Stop immediately):
- "About" or "roughly" = BROKEN AXIOM CABLE → Load component-verification.md
- Missing dimensions = NO CABLE → Cannot proceed without axiom
- Estimate instead of measurement = WEAK CABLE → Will fail under load
- Circular dependencies = CABLE LOOP → System is logically invalid

### Metacognitive Triggers for JITC Loading:
- **Uncertainty > 0.1**: Dimension unclear → Load component-verification.md
- **Constraint Conflict**: Cables pulling opposite directions → Load mathematical-constraints.md  
- **Axiom Ambiguity**: Cable origin unclear → Load establishing-axioms.md
- **Propagation Unknown**: Can't trace cable → Load entire directory

## Cable Verification Checklist

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


After processing this directory, verify:
1. ✓ Every design element has a traceable cable to an axiom
2. ✓ All axiom cables originate from verified measurements
3. ✓ No broken cables (estimates/approximations) in critical paths
4. ✓ Tolerance accumulation calculated along all cable paths
5. ✓ Circular cable dependencies eliminated
6. ✓ Confidence levels documented at each cable node

## The PDU Lesson - Why Cables Matter

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


The PDU Media Player disaster occurred because of a BROKEN AXIOM CABLE:
- Started with: "PCB about 80mm" (broken cable)
- Reality was: 114mm × 86.5mm (true cable)
- Result: Complete redesign required

**THE FUNDAMENTAL LAW**: A perfect design built on a broken axiom cable will fail perfectly.

This directory ensures that never happens again by establishing unbreakable axiom cables from the start.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!