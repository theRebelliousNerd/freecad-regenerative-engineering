# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# 04_Selection_Frameworks - Navigation Guide for Marie Curie Agent

## Directory Purpose
This directory contains structured decision-making frameworks for material selection when multiple constraints and objectives compete. It transforms material selection from intuition to systematic optimization, revealing the hidden trade-off cables between properties.

## The Trade-off Cable Network
Every material decision pulls multiple cables simultaneously:
- **Performance vs. Cost Cable**: Better materials cost more
- **Strength vs. Weight Cable**: Stronger often means denser
- **Stiffness vs. Toughness Cable**: Rigid materials tend to be brittle
- **Thermal vs. Electrical Cable**: Good conductors for both (metals) or neither (ceramics)
- **Processing vs. Properties Cable**: Easier to manufacture often means compromised performance

## Files in This Directory

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### `decision_matrices.md`
**When to Read**: When facing multi-criteria selection with no clear winner
**Purpose**: Structured approaches to weight and score options
**Key Methods**:
- Pugh matrices for concept comparison
- Weighted scoring for quantitative ranking
- Ashby charts for property mapping
- Pareto frontier identification

## Just-in-Time Retrieval Patterns

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Scenario: "Select material for drone frame"
1. IDENTIFY competing requirements:
   - Minimize weight (ρ)
   - Maximize stiffness (E)
   - Minimize cost ($/kg)
   - Ensure manufacturability
2. CONSTRUCT performance index: E^(1/3)/ρ for stiffness-limited design
3. RETRIEVE Ashby chart for E vs. ρ
4. FILTER by cost constraint
5. CHECK manufacturability with Gabe

### Scenario: "Heat sink material for LED"
1. DEFINE objective: Maximize heat dissipation per dollar
2. CREATE performance index: k/(ρ·cost)
3. RETRIEVE thermal conductivity data
4. WEIGHT by availability and machinability
5. VERIFY corrosion resistance for environment

### Scenario: "Multi-material optimization"
1. MAP functional requirements to zones
2. IDENTIFY interface constraints
3. RETRIEVE compatibility matrices
4. OPTIMIZE each zone independently
5. VERIFY interface integrity

## Metacognitive Triggers for Selection

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Complexity Indicators (Need Framework)
- **>3 competing objectives**: Simple ranking fails
- **Non-linear trade-offs**: Requires optimization
- **Coupled constraints**: Properties affect each other
- **Uncertain requirements**: Need robust selection
- **Multiple stakeholders**: Different priority weights

### Framework Selection Guide
```
How many criteria?
├─ 2-3: Use Ashby chart
├─ 4-6: Apply weighted scoring
├─ >6: Employ Pugh matrix
└─ Uncertain: Perform sensitivity analysis
```

## Material Selection Indices

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Common Performance Indices
- **Minimum weight, stiffness-limited**: E/ρ
- **Minimum weight, strength-limited**: σy/ρ
- **Minimum cost, stiffness-limited**: E/(ρ·Cm)
- **Maximum heat dissipation**: k
- **Thermal shock resistance**: σf·k/(E·α)
- **Damage tolerance**: K1c²/E

### Creating Custom Indices
1. Express objective as function of properties
2. Identify constraints (fixed geometry or load)
3. Derive index through substitution
4. Plot materials on log-log chart
5. Find Pareto frontier

## Decision Framework Hierarchy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Level 1: Screening
- Eliminate materials failing hard constraints
- Temperature limits
- Chemical compatibility
- Availability
- Regulatory compliance

### Level 2: Ranking  
- Apply performance indices
- Score against objectives
- Weight by importance
- Generate shortlist

### Level 3: Detailed Evaluation
- Precise property verification
- Manufacturing trials
- Cost analysis
- Risk assessment

### Level 4: Final Selection
- Prototype testing
- Supplier qualification
- Documentation
- Contingency planning

## Network Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Upstream (Feeds Into Selection)
- Functional requirements from interrogator
- Load cases from Brunel
- Thermal requirements from Watt
- Manufacturing constraints from Gabe
- Cost targets from requirements

### Downstream (Selection Affects)
- Design geometry must suit material
- Manufacturing process determined
- Assembly methods constrained
- Maintenance requirements set
- End-of-life disposal defined

## Quick Decision Tree

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```
Material Selection Challenge?
├─ Single dominant requirement?
│   ├─ YES → Rank by that property
│   └─ NO → Need multi-criteria framework
├─ Quantifiable objectives?
│   ├─ YES → Use performance indices
│   └─ NO → Apply qualitative scoring
├─ High uncertainty?
│   ├─ YES → Robust design approach
│   └─ NO → Deterministic optimization
└─ Novel application?
    ├─ YES → Prototype multiple options
    └─ NO → Use proven solutions
```

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Follow The Cable
Each selection criterion is a cable:
- Cost cable → Budget constraints → Design simplification
- Weight cable → Transportation limits → Size reduction
- Thermal cable → Operating temperature → Material screening
- Regulatory cable → Compliance needs → Certification costs

### Just-in-Time Context
Progressive refinement approach:
1. Start with broad material classes
2. Retrieve properties for promising subset
3. Detailed data only for shortlist
4. Manufacturing info only for finalists
5. Supplier data only for selected

## Common Selection Pitfalls

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


1. **Over-constraining**: Making all criteria "must have"
2. **Under-weighting cost**: Selecting optimal without considering economics
3. **Ignoring availability**: Perfect material with 6-month lead time
4. **Missing interactions**: Properties change with processing
5. **Static selection**: Not considering aging/degradation
6. **Single-source risk**: No alternative if supplier fails

## Sensitivity Analysis Requirements

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Always test selection robustness:
- Vary weights ±20% - does selection change?
- Consider property uncertainty - still optimal?
- Check temperature range - properties stable?
- Evaluate batch variation - acceptable spread?
- Assess long-term availability - sustainable choice?

## Documentation Requirements

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


For each selection, document:
1. All considered alternatives
2. Evaluation criteria and weights
3. Data sources and uncertainties
4. Trade-offs accepted
5. Risks identified
6. Contingency plans

## Cross-References

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

- **01_Foundations**: Selection methodology basis
- **02_MaterialProperties**: Property data source
- **05_Manufacturing**: Process compatibility check
- **06_Sustainability**: Environmental criteria
- **Khan agent**: For optimization algorithms

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!