# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Structural Analysis Directory - Navigation Guide for Brunel Agent

## Directory Purpose
This directory contains the comprehensive methodologies for analyzing how forces flow through structures. These documents represent the "nervous system" of structural engineering - tracing the invisible cables of force transmission, stress concentration, and failure prediction through any engineered system.

## Mental Model Integration

### Following the Cable - Force Flow Networks
In structural analysis, the "cables" are literal load paths:
- **Applied loads** → **Load paths** → **Support reactions**
- **Stress concentrations** → **Failure points** → **Safety factors**
- **Connection forces** → **Member stresses** → **Deformation patterns**

Every structural element is connected through these force transmission cables. A load applied at Point A doesn't just affect Point A - it sends stress waves through the entire network, concentrating at geometric discontinuities, flowing through connections, and eventually finding ground.

### Just-in-Time Retrieval Pattern
**Metacognitive triggers for retrieval:**

1. **"How does force flow?"** - Load path documents
2. **"Where will it fail?"** - Failure mode and stress concentration files
3. **"Is it safe enough?"** - Safety factor calculations
4. **"How to verify?"** - Validation and verification methods
5. **"How to implement in FreeCAD?"** - Implementation guides

## File Inventory & Access Guide

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 🔴 Critical Load Path Files (Primary Cables)
**load_path_methodology.md**
- **When**: Starting ANY structural analysis
- **Knowledge gaps**: How to systematically trace forces through structure
- **Dependencies**: Foundation for all other analyses

**load_path_principles.md**
- **When**: Establishing analysis framework
- **Knowledge gaps**: Fundamental concepts of force transmission
- **Downstream**: Informs all load path analyses

**types_of_load_paths.md**
- **When**: Identifying what kind of loading scenario
- **Knowledge gaps**: Tension vs compression vs shear paths
- **Downstream**: Determines analysis approach

### 🟠 Stress & Failure Analysis (Critical Junctions)
**stress_concentration_factors.md**
- **When**: Geometric discontinuities present
- **Knowledge gaps**: Where stress amplifies, quantification methods
- **Critical for**: Holes, notches, corners, transitions

**failure_mode_analysis.md**
- **When**: Determining weak points
- **Knowledge gaps**: How structures fail, failure sequences
- **Upstream**: Requires load path understanding

**stress_distribution_patterns.md**
- **When**: Understanding stress fields
- **Knowledge gaps**: How stress spreads through materials
- **Downstream**: Feeds into connection design

### 🟡 Safety & Calculations (Validation Cables)
**safety_factor_calculations.md**
- **When**: Determining design margins
- **Knowledge gaps**: How to calculate appropriate FOS
- **Critical**: ALWAYS required before design approval

**safety_factor_determination.md**
- **When**: Choosing safety factors for different scenarios
- **Knowledge gaps**: Industry standards, code requirements
- **Dependencies**: Application type, failure consequences

**practical_calculation_examples.md**
- **When**: Need worked examples
- **Knowledge gaps**: Step-by-step calculation procedures
- **Value**: Template for similar problems

### 🟢 Advanced & Optimization (Enhancement Cables)
**advanced_load_path_concepts.md**
- **When**: Complex multi-path structures
- **Knowledge gaps**: Redundancy, load sharing, alternate paths

**load_path_optimization_case_study.md**
- **When**: Optimizing force flow
- **Knowledge gaps**: How to improve load paths
- **Integration**: Links to Khan optimization

**optimizing_load_paths.md**
- **When**: Reducing material while maintaining strength
- **Knowledge gaps**: Topology optimization principles

### 🔵 Connection & Transfer (Interface Cables)
**connection_analysis.md**
- **When**: Analyzing joints and interfaces
- **Knowledge gaps**: Force transfer through connections
- **Critical**: Connections often govern design

**connection_design_for_load_transfer.md**
- **When**: Designing new connections
- **Knowledge gaps**: Efficient force transfer methods
- **Downstream**: Manufacturing constraints

**calculating_load_distribution.md**
- **When**: Multiple load paths exist
- **Knowledge gaps**: How loads split between paths
- **Requires**: Stiffness calculations

### 🟣 Verification & Implementation (Reality Cables)
**load_path_verification.md**
- **When**: Validating analysis results
- **Knowledge gaps**: How to confirm load paths are correct

**modern_fem_validation.md**
- **When**: Using FEA tools
- **Knowledge gaps**: Validating computer analysis

**freecad_implementation.md**
- **When**: Implementing in FreeCAD
- **Knowledge gaps**: Software-specific methods
- **Critical**: Practical implementation guide

### 📚 Case Studies (Historical Cables)
**clifton_suspension_bridge_analysis.md**
**great_eastern_hull_stress_analysis.md**
**royal_albert_bridge_analysis.md**
**box_tunnel_rock_mechanics.md**
- **When**: Learning from precedent
- **Knowledge gaps**: How masters solved similar problems
- **Value**: Proven solutions, lessons learned

### 🔧 Methodology & Best Practices
**structural_analysis_methodology.md**
- **When**: Establishing systematic approach
- **Knowledge gaps**: Overall analysis workflow

**fundamental_analysis_principles.md**
- **When**: Understanding core concepts
- **Knowledge gaps**: Basic principles before details

**best_practices_for_load_paths.md**
- **When**: Ensuring quality analysis
- **Knowledge gaps**: Common mistakes to avoid

**load_path_analysis_in_complex_structures.md**
- **When**: Dealing with complex geometries
- **Knowledge gaps**: Multi-material, multi-scale structures

## Dependency Graph

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

```
Load Path Core
├── load_path_methodology.md
│   ├── types_of_load_paths.md
│   ├── calculating_load_distribution.md
│   └── load_path_verification.md
├── load_path_principles.md
│   ├── advanced_load_path_concepts.md
│   └── optimizing_load_paths.md
└── best_practices_for_load_paths.md

Stress Analysis Branch
├── stress_concentration_factors.md
│   └── connection_analysis.md
├── stress_distribution_patterns.md
│   └── connection_design_for_load_transfer.md
└── failure_mode_analysis.md
    └── safety_factor_calculations.md

Implementation Branch
├── freecad_implementation.md
├── modern_fem_validation.md
└── practical_calculation_examples.md
```

## Metacognitive Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

```
Structural Analysis Task
├─ Unknown force flow? → load_path_methodology.md
├─ Stress concentration concern? → stress_concentration_factors.md
├─ Safety verification needed? → safety_factor_calculations.md
├─ Connection design? → connection_analysis.md
├─ Complex structure? → load_path_analysis_in_complex_structures.md
├─ Need validation? → load_path_verification.md
├─ FreeCAD implementation? → freecad_implementation.md
└─ Historical precedent? → Case study files
```

## Quick Reference - Problem to File Mapping

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


| Problem Type | Primary Files | Support Files |
|-------------|---------------|---------------|
| New structure analysis | load_path_methodology.md | fundamental_analysis_principles.md |
| Joint design | connection_analysis.md | stress_concentration_factors.md |
| Safety assessment | safety_factor_calculations.md | failure_mode_analysis.md |
| Optimization | optimizing_load_paths.md | advanced_load_path_concepts.md |
| Verification | load_path_verification.md | modern_fem_validation.md |
| Complex geometry | load_path_analysis_in_complex_structures.md | calculating_load_distribution.md |

## Integration Points

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream (What feeds structural analysis)
- **foundations/**: Mathematical axioms, scaling principles
- **DaVinci**: Geometric concepts requiring validation
- **Archimedes**: Mathematical constraints and proofs

### Downstream (What uses structural analysis)
- **systems_integration/**: Connection requirements
- **field_implementation/**: Buildability constraints
- **Khan**: Optimization objectives and constraints
- **Gabe**: Manufacturing limitations affecting structure

## Uncertainty Thresholds

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **High uncertainty** (>0.7): Retrieve fundamental principles
- **Medium uncertainty** (0.4-0.7): Retrieve specific methods
- **Low uncertainty** (<0.4): Retrieve examples or verification only

## Update Log

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- Created: 2025-09-03
- Mental Models: Force flow as cables, JIT retrieval based on uncertainty
- Purpose: Navigate 26 structural analysis documents efficiently

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!