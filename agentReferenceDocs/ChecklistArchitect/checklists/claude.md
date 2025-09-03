# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Checklists Directory - Quality Assurance Cable Network Hub

## Overview: Checklists as Quality Cables
This directory contains the comprehensive checklist library that forms the backbone of our quality assurance cable network. Each checklist creates "cables" - systematic connections between requirements and verification - ensuring no critical dependency is overlooked in the engineering process.

## Just-in-Time Context Framework
Following the JITC principle of minimal viable context retrieval, access checklists based on:
- **Current project phase** (foundation → integration → production → safety → validation)
- **Complexity level** (simple → moderate → complex → safety-critical)
- **Active failure patterns** detected in your project
- **Agent coordination requirements** when multiple specialists are involved

## Cable Architecture of Validation

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Primary Quality Cables
Each subdirectory represents a major "cable bundle" in the quality network:

#### Foundation Cables (`foundation/`)
- **Purpose**: Core verification cables that connect requirements to basic implementation
- **When to Access**: Gate 0 (Pre-Project) and Gate 1 (Pre-CAD) transitions
- **Cable Function**: Ensures fundamental assumptions are verified before design work begins
- **Metacognitive Trigger**: "Do I have verified dimensions for every component?"

#### Integration Cables (`integration/`)  
- **Purpose**: Cross-domain verification cables connecting different engineering disciplines
- **When to Access**: When multiple agents (Tesla↔Watt, Turing↔Brunel, etc.) must coordinate
- **Cable Function**: Validates coupled multi-physics dependencies don't conflict
- **Metacognitive Trigger**: "Are electromagnetic and thermal requirements compatible?"

#### Production Cables (`production/`)
- **Purpose**: Manufacturing readiness cables connecting design to producibility
- **When to Access**: Gate 3 (Detailed Design Review) and Gate 4 (Pre-Production)
- **Cable Function**: Ensures design decisions trace through to manufacturable outcomes
- **Metacognitive Trigger**: "Can this actually be built with available resources?"

#### Safety Cables (`safety/`)
- **Purpose**: Critical safety verification cables that cannot be compromised
- **When to Access**: Safety-critical projects, regulatory compliance, human interaction
- **Cable Function**: Creates unbreakable connections between human safety and system design
- **Metacognitive Trigger**: "Could this design harm someone?"

#### Validation Cables (`validation/`)
- **Purpose**: Performance verification cables connecting specifications to measurable outcomes
- **When to Access**: Throughout design process for empirical validation
- **Cable Function**: Links theoretical predictions to measurable results
- **Metacognitive Trigger**: "How will we prove this works as intended?"

## Navigation Strategy by Project Complexity

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Simple Projects (1-5 components, single domain)
**Minimal Cable Set**:
```
foundation/component-verification.md
validation/basic-performance.md
```

### Moderate Projects (5-20 components, 2-3 domains)  
**Standard Cable Bundle**:
```
foundation/component-verification.md + requirements-completeness.md
integration/thermal-electromagnetic.md (if applicable)
production/manufacturing-readiness.md
validation/performance-verification.md
```

### Complex Projects (20+ components, 4+ domains)
**Complete Cable Network**:
```
foundation/* (all foundation cables)
integration/* (relevant coupling cables)
production/* (comprehensive manufacturing)
validation/* (thorough testing protocols)
safety/* (if human interaction or safety-critical)
```

## Cable Dependency Tracing

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Following the Quality Cable
When a checklist item fails, trace the cable back to its source:
1. **Identify the broken cable**: Which verification failed?
2. **Trace upstream**: What assumption or requirement fed this verification?
3. **Find the root**: Often leads back to foundation/ or integration/ issues
4. **Repair systematically**: Fix the source, then re-verify downstream cables

### Cable Strength Indicators
- **PASS**: Cable is intact, dependency verified
- **FAIL**: Cable is broken, must stop and repair
- **INCOMPLETE**: Cable not fully connected, needs more verification
- **NOT_APPLICABLE**: Cable not needed for this project type

## Just-in-Time Checklist Retrieval

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Metacognitive Triggers for Checklist Access
The ChecklistArchitect detects uncertainty and retrieves appropriate checklists:

**High Uncertainty Signals**:
- "I'm not sure if..." → Load foundation/requirements-completeness.md
- "Will this fit together?" → Load foundation/component-verification.md + integration/
- "Can this be manufactured?" → Load production/manufacturing-readiness.md
- "Is this safe?" → Load safety/ (entire directory)
- "How do we test this?" → Load validation/performance-verification.md

**Project Phase Triggers**:
- Gate 0 Review → foundation/
- Multi-agent coordination → integration/
- Manufacturing handoff → production/
- Safety assessment → safety/
- Performance validation → validation/

## Cable Network Integrity Verification

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Self-Diagnostic Questions
Before accessing any checklist subdirectory, verify cable continuity:

1. **Source Connection**: "Is this checklist connected to actual requirements?"
2. **Dependency Flow**: "Does this checklist's output feed necessary downstream validation?"
3. **Completeness**: "Are all relevant cables represented in my selected checklists?"
4. **Redundancy Check**: "Am I loading overlapping checklists unnecessarily?"

### Network Health Indicators
- **Strong Network**: All checklists trace back to requirements, forward to validation
- **Weak Links**: Checklists that don't connect to project requirements
- **Missing Cables**: Gaps where verification should exist but doesn't
- **Cable Loops**: Circular dependencies that prevent progress

## Integration with Agent Orchestration

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Cable Handoff Protocols
Checklists create information cables between agents:
- **Archimedes → ChecklistArchitect**: Mathematical axioms become verification criteria
- **ChecklistArchitect → Orville**: Verification requirements become test protocols  
- **Gabe → ChecklistArchitect**: Manufacturing constraints become design verification
- **Vitruvius → ChecklistArchitect**: Safety requirements become mandatory gates

### Cross-Domain Cable Management
When agents must coordinate, checklists manage the cable intersections:
- Tesla + Watt coordination: integration/thermal-electromagnetic.md
- Turing + Brunel coordination: integration/kinematic-structural.md
- Edison + Hertz coordination: integration/electrical-rf.md

## Usage Analytics and Cable Optimization

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Track which cable combinations are most effective:
- **High Success Combinations**: Checklist bundles that prevent failures
- **Failure Pattern Correlation**: Which missing cables lead to specific failures
- **Efficiency Metrics**: Optimal cable loading for different project types
- **Metacognitive Accuracy**: How well uncertainty triggers match actual needs

Remember: **Checklists are not just task lists - they are quality assurance cables that ensure systematic verification of all critical dependencies in your engineering process. Each checklist creates measurable connections between requirements and validation.**

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!