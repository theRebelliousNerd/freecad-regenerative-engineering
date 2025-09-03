# Iterative Refinement Protocols

## The Evolution of Requirements Understanding

Requirements are not discovered in a single moment of clarity. They emerge through systematic iteration, each cycle revealing deeper layers of understanding, exposing hidden assumptions, and uncovering previously invisible constraints. The Requirements Interrogator orchestrates this evolutionary process with scientific rigor.

**Core Principle**: "Requirements are living documents that evolve toward truth through systematic iteration, not static specifications that must be perfect on first attempt."

## The Requirements Maturation Model

### Stage 0: Raw Expression (Genesis)
**Characteristics**: 
- User's initial problem statement
- Solution-focused rather than need-focused
- Heavy use of approximation language
- Embedded assumptions invisible

**Example**: "I need a plastic box about 100mm × 80mm to hold some electronics"

**Quality Metrics**:
- Specificity: 20% (vague dimensions, unspecified electronics)
- Completeness: 15% (no environmental, service, or performance requirements)
- Verifiability: 10% (no measurement method specified)

### Stage 1: Structured Inquiry (Archaeology)
**Process**: Systematic questioning to excavate buried requirements
**Focus**: What, where, when, who, how questions
**Output**: Expanded problem understanding with identified unknowns

**Example After Iteration 1**:
```yaml
functional_need: "Protect circuit board from dust and moisture during outdoor installation"
component_details: "Single PCB, dimensions TBD, mounted relay and terminal blocks"
environment: "Outdoor industrial setting, temperature range TBD"
constraints: "Must fit in existing cabinet space (approx 150×120×75mm)"
unknowns:
  - Exact PCB dimensions
  - IP rating requirement
  - Mounting method
  - Service access needs
```

**Quality Metrics**:
- Specificity: 45% (clearer purpose, some constraints identified)
- Completeness: 35% (environment acknowledged, but gaps remain)
- Verifiability: 25% (some measurement targets, but many TBDs)

### Stage 2: Evidence Gathering (Validation)
**Process**: Physical verification, stakeholder consultation, standard research
**Focus**: Converting TBDs into verified facts
**Output**: Evidence-backed specifications with uncertainty bounds

**Example After Iteration 2**:
```yaml
functional_requirement: "Protect PCB from IP54 environmental conditions per installation spec IS-001"
component_verified:
  pcb_dimensions: "114.2 × 86.5 × 1.6mm (measured, 3 samples, ±0.1mm)"
  relay_height: "43mm above PCB (datasheet Part No. RLY-4CH-24V)"
  terminal_clearance: "25mm minimum above highest terminal for wire insertion"
environment_specified:
  temperature: "-20°C to +60°C per site survey data"
  humidity: "95% RH non-condensing per local weather station"
  ip_rating: "IP54 minimum per installation standard"
constraints_verified:
  cabinet_space: "150×120×75mm internal (measured existing cabinet)"
  mounting: "Must use existing 4× M4 threaded inserts"
```

**Quality Metrics**:
- Specificity: 75% (measured values with uncertainties)
- Completeness: 60% (major categories covered, some details pending)
- Verifiability: 70% (measurement methods and sources documented)

### Stage 3: Integration Analysis (Synthesis)
**Process**: System-level thinking, stakeholder alignment, conflict resolution
**Focus**: How requirements interact, compete, and constrain each other
**Output**: Optimized, consistent, implementable specification set

**Example After Iteration 3**:
```yaml
integrated_specification:
  envelope_requirement:
    external_max: "148×118×73mm (allows 1mm cabinet clearance all sides)"
    internal_min: "135×105×65mm (accommodates PCB + clearances + mounting)"
  thermal_management:
    heat_generation: "12W total (PCB 8W + relay coil 4W)"
    cooling_strategy: "Natural convection + conduction to cabinet"
    temperature_rise: "<20°C above ambient (verified by calculation)"
  service_access:
    maintenance_frequency: "Annual inspection, 5-year relay replacement"
    tool_requirements: "Standard Phillips #2 screwdriver only"
    access_sequence: "Remove 4 screws → lift lid → access all components"
  manufacturing_constraints:
    material: "ABS plastic, UV stabilized for outdoor service"
    manufacturing: "3D printing for prototype, injection molding for production"
    cost_target: "<$25 per unit at 1000 quantity"
```

**Quality Metrics**:
- Specificity: 90% (precise values with rationale)
- Completeness: 85% (all major aspects covered)
- Verifiability: 90% (clear acceptance criteria defined)

### Stage 4: Validation Ready (Maturation)
**Process**: Final verification, stakeholder sign-off, handoff preparation
**Focus**: Ensuring nothing missed, all parties aligned
**Output**: Implementation-ready requirements blueprint

**Quality Metrics**:
- Specificity: 95% (manufacturing-ready precision)
- Completeness: 95% (all aspects covered or explicitly deferred)
- Verifiability: 95% (comprehensive test criteria established)

## The Iterative Refinement Engine

### The OODA Loop for Requirements (Observe-Orient-Decide-Act)

#### Observe Phase
**Collect**: New information, stakeholder feedback, test results, changed conditions
**Document**: What was learned, what changed, what surprised us
**Metrics**: Information quality, source reliability, relevance assessment

**Example Observation Log**:
```yaml
iteration_3_observations:
  - "PCB vendor revised dimensions: 114.2→115.8mm (0.7% increase)"
  - "Thermal testing shows 15°C rise, not 12°C as calculated"
  - "Service technician feedback: 'Need tool storage in lid'"
  - "Regulatory review: IP54 insufficient for coastal installations"
```

#### Orient Phase  
**Analyze**: How new information changes understanding
**Synthesize**: Integration with existing knowledge
**Pattern Recognition**: Identify trends and recurring themes

**Example Analysis**:
```yaml
orientation_analysis:
  dimension_impact:
    - "PCB change requires internal length increase to 136mm"
    - "External envelope now 149×118×73mm (cabinet fit marginal)"
  thermal_revision:
    - "Higher temperature rise indicates need for better heat transfer"
    - "May require thermal pad or heat sink consideration"  
  scope_expansion:
    - "Tool storage adds complexity but significant user value"
    - "Coastal rating upgrade affects material selection"
```

#### Decide Phase
**Prioritize**: Which changes are critical vs nice-to-have
**Resource**: What effort is required for each change
**Timeline**: How changes affect project schedule
**Risk**: What happens if changes are not made

**Example Decisions**:
```yaml
iteration_4_decisions:
  critical_changes:
    - "Increase internal length to 136mm (accommodation required)"
    - "Add thermal pad specification for heat transfer improvement"
  deferred_changes:  
    - "Tool storage moved to Phase 2 (complexity vs benefit)"
  rejected_changes:
    - "Coastal IP rating upgrade (scope creep, <5% of installations)"
```

#### Act Phase
**Implement**: Update specifications based on decisions
**Communicate**: Inform all stakeholders of changes
**Verify**: Confirm changes solve the identified issues
**Plan**: Next iteration cycle

### The Progressive Fidelity Protocol

#### Iteration Scope Definition
Each iteration has a specific focus area to prevent overwhelming complexity:

**Iteration 1**: Core functional requirements
**Iteration 2**: Physical constraints and components  
**Iteration 3**: Environmental and operational requirements
**Iteration 4**: Manufacturing and service requirements
**Iteration 5**: Integration and optimization
**Iteration 6**: Validation and handoff preparation

#### The Requirements Quality Gates
Before advancing to the next iteration, verify:

```python
def quality_gate_check(requirements, iteration_level):
    checks = {
        'specificity': calculate_specificity_score(requirements),
        'completeness': calculate_completeness_score(requirements, iteration_level),
        'verifiability': calculate_verifiability_score(requirements),
        'consistency': check_internal_consistency(requirements),
        'stakeholder_alignment': verify_stakeholder_consensus(requirements)
    }
    
    thresholds = {
        1: {'specificity': 30, 'completeness': 20, 'verifiability': 20},
        2: {'specificity': 50, 'completeness': 40, 'verifiability': 40},
        3: {'specificity': 70, 'completeness': 60, 'verifiability': 60},
        4: {'specificity': 85, 'completeness': 80, 'verifiability': 80},
        5: {'specificity': 95, 'completeness': 90, 'verifiability': 90}
    }
    
    return all(checks[metric] >= thresholds[iteration_level][metric] 
              for metric in thresholds[iteration_level])
```

## Advanced Refinement Techniques

### The Requirements Stress Testing
**Purpose**: Deliberately challenge requirements to reveal weaknesses
**Method**: Apply extreme scenarios, edge cases, and failure conditions

**Example Stress Tests**:
```yaml
stress_scenarios:
  dimensional_extremes:
    - "What if PCB tolerance is worst-case +1mm in all dimensions?"
    - "What if cabinet space is 2mm smaller due to building settlement?"
  environmental_extremes:  
    - "What if temperature reaches 70°C during heat wave?"
    - "What if humidity spikes to 100% during storm?"
  operational_extremes:
    - "What if service is needed in winter with thick gloves?"
    - "What if multiple components fail simultaneously?"
```

### The Requirements Archaeology Deep-Dive
**Purpose**: Uncover requirements buried beneath solution assumptions
**Method**: Recursive "why" questioning for each requirement

**Example Deep-Dive**:
```
Requirement: "Enclosure must be ABS plastic"
Why ABS? "It's cheaper than metal"
Why does cost matter? "Budget is limited"  
What is the budget? "Under $25 per unit"
Why that budget? "Market pricing analysis"
What if we could reduce other costs? "Then material options expand"
Deeper requirement: "Total unit cost <$25 to maintain market competitiveness"
```

### The Convergence Acceleration Techniques

#### The Requirements Triage Method
**Green Requirements**: Stable, verified, ready for implementation
**Yellow Requirements**: Need minor clarification or verification
**Red Requirements**: Major issues, conflicts, or missing information

Focus iteration cycles on moving red→yellow→green:

```yaml
requirements_triage:
  green_count: 15  # 65% of total requirements
  yellow_count: 6  # 25% of total requirements  
  red_count: 2     # 10% of total requirements
  
target_next_iteration:
  green_target: 18  # Move 3 from yellow to green
  yellow_target: 4  # Move 1 red to yellow, resolve 2 yellows
  red_target: 1     # Resolve 1 critical red requirement
```

#### The Stakeholder Feedback Velocity
**Rapid Cycles**: Short iterations with quick stakeholder validation
**Focused Reviews**: Each iteration targets specific stakeholder concerns
**Parallel Processing**: Multiple stakeholders review different requirement areas simultaneously

```yaml
iteration_schedule:
  cycle_length: "3 days maximum"
  review_parallel_tracks:
    - "Technical feasibility (Engineering)"
    - "Cost implications (Finance)"  
    - "User impact (Operations)"
    - "Compliance review (Legal/Safety)"
  integration_session: "Day 4 - resolve conflicts and align"
```

## The Requirements Evolution Tracking

### Version Control for Requirements
Each iteration creates a versioned snapshot:

```yaml
requirements_v2_3:
  version: "2.3"
  date: "2024-09-15"  
  iteration: 4
  changes_from_v2_2:
    - "Updated PCB dimensions to 115.8×86.5mm"
    - "Added thermal pad requirement"
    - "Removed tool storage from scope"
  quality_metrics:
    specificity: 85%
    completeness: 75%
    verifiability: 80%
  stakeholder_approvals:
    - "Engineering: Approved with thermal concerns noted"
    - "Manufacturing: Approved pending material selection"
    - "Operations: Conditional approval - wants tool storage in Phase 2"
```

### The Requirements Provenance Trail
Track the evolution of each requirement:

```yaml
requirement_history:
  req_id: "ENV-001"
  current: "Operating temperature: -20°C to +60°C"
  evolution:
    v1_0: "Room temperature operation"
    v1_5: "Indoor use, 10°C to 40°C"  
    v2_0: "Outdoor rated, -10°C to 50°C"
    v2_3: "-20°C to +60°C per site survey data"
  rationale: "Site survey revealed winter lows to -18°C, summer cabinet temps to 58°C"
  evidence: "Weather station data 2019-2023, thermal modeling results"
```

## Refinement Completion Criteria

### Convergence Indicators
The requirements have converged when:

1. **Stability**: <5% changes between iterations
2. **Quality**: All metrics >90% for target iteration level  
3. **Consensus**: All stakeholders formally approve specifications
4. **Completeness**: No major requirement categories remain "TBD"
5. **Verifiability**: Every requirement has defined acceptance criteria
6. **Implementability**: Engineering confirms feasibility and approach

### The Handoff Readiness Assessment
```yaml
handoff_checklist:
  requirements_quality:
    - specificity_score: ">90%"
    - completeness_score: ">90%" 
    - verifiability_score: ">90%"
    - consistency_check: "PASS"
  stakeholder_alignment:
    - formal_approvals: "All critical stakeholders signed off"
    - conflict_resolution: "All conflicts resolved or deferred with agreement"
    - change_process: "Change management protocol established"
  implementation_readiness:
    - feasibility_confirmed: "Engineering verification complete"
    - resource_allocation: "Budget and schedule approved"
    - risk_mitigation: "Critical risks identified with mitigation plans"
```

## The Iterative Refinement Manifesto

*"I embrace the evolutionary nature of requirements understanding. I do not demand perfection in the first iteration, but I demand systematic progress toward truth in every iteration. I measure not just what we know, but how well we know it. I track not just requirements, but the evidence that supports them. I orchestrate the convergence of understanding across stakeholders, domains, and time. Through disciplined iteration, I transform uncertainty into clarity, assumptions into facts, and wishes into implementable specifications."*

## Success Patterns for Iterative Refinement

**The Spiral of Increasing Precision**: Each iteration adds specific detail while maintaining system coherence
**The Stakeholder Convergence**: Different perspectives align through structured dialogue and shared evidence
**The Evidence Accumulation**: Facts replace assumptions through systematic verification
**The Complexity Management**: System understanding grows without overwhelming any individual iteration

## Anti-Patterns to Avoid

1. **The Analysis Paralysis**: Infinite refinement without implementation progress
2. **The Scope Creep Spiral**: Each iteration adds new requirements without prioritization
3. **The Perfectionism Trap**: Demanding unrealistic precision on non-critical elements
4. **The Consensus Fatigue**: Wearing down stakeholders with excessive iterations
5. **The Context Loss**: Losing sight of the original problem during refinement

Remember: The goal of iterative refinement is not perfect requirements, but requirements that are good enough to enable successful implementation. Each iteration should move measurably closer to that goal.