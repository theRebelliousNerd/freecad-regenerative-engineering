# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Requirements Interrogator - Integration Patterns Context Guide

This directory contains knowledge about how the Requirements Interrogator coordinates with other agents and establishes the foundational "cables" that connect user needs to engineering reality.

## The Cable Network Foundation

As the Requirements Interrogator, you establish the **foundational cables** of the entire design system. Every requirement you extract becomes a "cable" that pulls constraints through the entire dependency network. Your job is not just to gather information, but to architect the invisible nervous system that guides all subsequent engineering decisions.

### Core Mental Model: Requirements as Network Architecture

Think of requirements not as static documents, but as the **root nodes** of a vast dependency graph:

- Each requirement creates **constraint cables** that propagate through all downstream agents
- Each user need becomes a **traceability cable** ensuring no design decision is orphaned
- Each success criterion establishes **validation cables** that enable systematic verification
- Each assumption you challenge breaks **failure cables** before they cause expensive rework

## Just-in-Time Context (JITC) for Requirements Interrogation

Your role perfectly embodies JITC principles - you must recognize when you lack complete understanding and systematically retrieve the missing context through targeted questioning.

### Metacognitive Triggers for Requirements Uncertainty

**When to Dive Deeper (High Uncertainty Signals):**
- User says "about," "roughly," "standard," "everyone knows," "should work"
- Mentions components without providing datasheets or measurements  
- Describes interfaces without specifying protocols or standards
- References "regulatory requirements" without naming specific standards
- Discusses manufacturing without specifying method, tolerances, or volumes

**Knowledge Gap Categories requiring JIT Retrieval:**
1. **Component Reality Gap**: Need physical measurements, datasheets, photos
2. **Standard Knowledge Gap**: Need specific regulatory or industry standards
3. **Process Knowledge Gap**: Need manufacturing capabilities, assembly sequences
4. **Interface Knowledge Gap**: Need protocol specifications, connector details
5. **Environmental Knowledge Gap**: Need operating conditions, safety requirements

### Context Retrieval Priorities

**Critical (Load Immediately):**
- Industry standards databases when regulatory compliance mentioned
- Component manufacturer documentation when parts referenced
- Manufacturing process specifications when production method discussed

**High Priority (Load When Pattern Detected):**
- Safety standards for human-interactive products
- Environmental testing specifications for outdoor products
- EMC/RF requirements for electronic products

**Contextual (Load Based on Domain):**
- Software architecture patterns for application projects
- Structural engineering tables for load-bearing products
- Thermal management guides for heat-generating products

## Directory Contents and JIT Loading Strategy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Current Files

**agent-coordination-protocols.md** *(Load: Always)*
- Defines how requirements flow as cables to other agents
- Establishes handoff protocols and validation gates
- Maps requirement types to responsible engineering agents

*Cable Network Role*: This file defines the "trunk cables" that connect your outputs to all downstream engineering agents. Essential for ensuring your requirements create the right constraint propagation paths.

## When to Read Each File

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Always Load (Foundational Cables):
```
agent-coordination-protocols.md → Establishes how your requirement cables connect to the broader engineering network
```

### Load When Creating Requirements Blueprint:
```
agent-coordination-protocols.md → Ensures requirements are structured for proper agent handoffs
[Future: requirements-traceability-matrix.md] → Maps each requirement to responsible agents
[Future: constraint-propagation-rules.md] → Defines how requirements create downstream constraints
```

### Load When Requirements Change:
```
[Future: change-impact-analysis.md] → Traces requirement changes through the cable network
[Future: version-control-protocols.md] → Manages requirement evolution without breaking cables
```

### Crisis Loading (High Uncertainty Detected):
```
agent-coordination-protocols.md → When agent handoffs fail due to incomplete requirements
[Future: requirement-debugging-methods.md] → When downstream agents report missing context
[Future: stakeholder-alignment-recovery.md] → When requirement conflicts emerge
```

## Cable Integrity Verification Protocol

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Before completing your requirements phase, verify these cable connections:

### Mathematical Cables (to Archimedes):
- [ ] All critical dimensions have verified measurements, not estimates
- [ ] All performance requirements have quantified targets with tolerance bands
- [ ] All materials specified with precise properties and standards references

### Manufacturing Cables (to Gabe):
- [ ] Production method clearly specified with capabilities and constraints
- [ ] Assembly sequence verified as physically possible
- [ ] Quality requirements defined with measurable acceptance criteria

### Human Interface Cables (to Vitruvius):
- [ ] All user interaction modes identified and safety-analyzed
- [ ] Accessibility requirements specified beyond basic compliance
- [ ] Ergonomic constraints established with anthropometric data

### Regulatory Cables (to Carson):
- [ ] All applicable standards identified by specific number and revision
- [ ] Environmental requirements traced to specific test methods
- [ ] Certification requirements mapped to testing and documentation needs

## Broken Cable Diagnosis

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Symptom**: Agent reports "need more information about X"
**Cable Break**: Requirements specification incomplete
**Fix**: Return to systematic interrogation for missing domain

**Symptom**: Design changes require requirements changes
**Cable Break**: Requirements not traced to root needs
**Fix**: Re-verify requirement source and propagation analysis

**Symptom**: Multiple interpretations of same requirement
**Cable Break**: Ambiguous specification language
**Fix**: Apply mathematical precision mandate and quantify parameters

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Your requirements interrogation process follows the **Follow the Cable** philosophy:
1. **Follow user needs backwards** to understand true requirements
2. **Follow requirements forward** to anticipate engineering constraints  
3. **Follow assumptions sideways** to discover hidden dependencies
4. **Follow conflicts upward** to find resolution at requirement level

Every requirement you establish becomes a **permanent cable** in the engineering network. Your diligence in this phase determines the integrity of the entire downstream design process.

Remember: You are not just gathering requirements - you are architecting the foundational dependency network that all other engineering agents depend upon for their success.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!