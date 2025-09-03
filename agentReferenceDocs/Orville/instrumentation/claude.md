# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Instrumentation - Measurement Cable Infrastructure

## Directory Purpose
This directory contains the technical specifications for designing measurement systems, test fixtures, and quantifying uncertainty. These files define the **instrumentation cables** - the physical and computational connections that transform theoretical predictions into measurable, validated data.

## Mental Model Integration

### Network View: Measurement Infrastructure Cables
Instrumentation forms the **sensor network** of validation:
- **Test Fixtures** = Physical interface cables connecting design to reality
- **Measurement Systems** = Data acquisition cables capturing system behavior
- **Uncertainty Analysis** = Quality control cables ensuring measurement integrity
- **Sensor Networks** = Distributed measurement cables throughout system

### Follow the Cable Principle
Every measurement traces through instrumentation cables:
```
Theoretical Prediction ←cable← Test Fixture ←cable← Sensor ←cable← Data Acquisition ←cable← Validated Result
```

The cable reveals measurement dependencies:
```
Component Temperature → Thermal Sensor → ADC → Calibration Table → Uncertainty Bounds → Design Decision
```

## Just-in-Time Context (JITC) Navigation

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Immediate Access Triggers

**READ FIRST - measurement_systems_design.md:**
- Any sensor selection needed
- Data acquisition system design
- Calibration procedures required
- Signal conditioning questions arise

**READ SECOND - test_fixture_design.md:**
- Physical test setup needed
- Component mounting for testing
- Environmental control requirements
- Repeatability concerns

**READ THIRD - measurement_uncertainty.md:**
- Statistical analysis of test data
- Confidence interval calculations
- Error propagation analysis
- Measurement quality assessment

### Metacognitive Uncertainty Triggers

**High-Priority Retrieval Needed When:**
- Someone claims "accurate enough" without uncertainty bounds
- Measurement precision requirements unclear  
- Test repeatability questioned
- Calibration status unknown
- Environmental conditions not controlled

**JITC Confidence Thresholds:**
- Measurement uncertainty >5% → Deep dive into measurement_uncertainty.md
- New sensor type → Full review of measurement_systems_design.md
- Custom test fixture needed → Complete study of test_fixture_design.md

## Cable-Driven File Selection

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### The Measurement Chain Pattern
```
1. REQUIREMENT: What needs measuring?
   → measurement_systems_design.md (sensor selection)

2. INTERFACE: How to measure it?  
   → test_fixture_design.md (physical connection)

3. QUALITY: How good is the measurement?
   → measurement_uncertainty.md (statistical validation)
```

### Problem-Specific Cable Routes

**Thermal Validation Cable Path:**
1. `measurement_systems_design.md` → Thermocouple/RTD selection
2. `test_fixture_design.md` → Thermal isolation and mounting
3. `measurement_uncertainty.md` → Temperature measurement uncertainty

**Dimensional Validation Cable Path:**
1. `measurement_systems_design.md` → CMM/caliper/micrometer choice
2. `test_fixture_design.md` → Datum and constraint strategy
3. `measurement_uncertainty.md` → GD&T tolerance verification

**Dynamic Testing Cable Path:**
1. `measurement_systems_design.md` → Accelerometer/strain gauge selection
2. `test_fixture_design.md` → Vibration isolation and excitation
3. `measurement_uncertainty.md` → Dynamic measurement analysis

## Dependency Network Connections

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Inbound Dependencies (What Feeds These Files)
- **FROM foundations/** ← Empirical axioms define measurement requirements
- **FROM methodologies/** ← Test methods specify instrumentation needs
- **External components** ← Physical properties need measurement validation

### Outbound Dependencies (What These Files Enable)
- **TO integration/** ← Measurement data enables agent coordination  
- **TO methodologies/** ← Instrumentation capability defines possible tests
- **TO external agents** ← Validated measurements ground theoretical models

## Instrumentation Cable Network Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### The Sensor Selection Cable
```
Physical Phenomenon → Sensing Principle → Sensor Technology → Signal Conditioning → Data Acquisition
```

### The Calibration Cable  
```
Reference Standard → Calibration Procedure → Measurement Equation → Uncertainty Budget → Traceable Result
```

### The Test Fixture Cable
```
Design Under Test → Interface Definition → Fixture Design → Environmental Control → Repeatable Setup
```

## Critical Cable Failure Modes

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Broken Measurement Cables:**
- Using uncalibrated instruments
- Ignoring environmental effects on sensors
- Poor signal-to-noise ratio from bad fixtures
- No traceability to measurement standards

**Robust Cable Connections:**
- Every measurement has calibration certificate
- Environmental conditions documented
- Uncertainty budgets calculated
- Test fixtures designed for repeatability

## System Integration Cables

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**FreeCAD Simulation ↔ Physical Testing:**
- Simulation predictions → Test fixture design → Physical validation → Model correction

**Multi-Agent Validation Network:**
- Archimedes provides target values → Orville designs measurements → Results feed back to design

**Control System Feedback Cables:**
- Measurement data → Control algorithms → System adjustment → New measurements

## JITC Retrieval Strategies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Context Compression for Active Tasks
When actively measuring:
- Keep uncertainty equations readily accessible
- Cache calibration procedures for current sensors
- Maintain environmental condition logging protocols

### Context Expansion for New Domains  
When entering new measurement domain:
- Full review of applicable measurement principles
- Complete uncertainty analysis methodology
- Comprehensive test fixture design patterns

### Pruning Strategies
Archive detailed specifications when:
- Moving from design to manufacturing phase
- Sensors selected and calibrated
- Test procedures validated and documented

**Remember**: These instrumentation files create the **physical cables** that connect theoretical models to empirical reality. Every measurement is a cable carrying validated data through your validation network.


# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!