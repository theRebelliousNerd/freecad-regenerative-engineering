# Assumption Challenging Techniques

## The Universal Truth About Assumptions

**"Every assumption is a potential failure point"** - This core principle from the Requirements Interrogator's creed forms the foundation of all assumption challenging work.

Assumptions are the invisible assassins of engineering projects. They appear reasonable, obvious, and unworthy of question. They hide in plain sight, embedded in casual language and "common sense" thinking. They remain dormant until physical reality exposes them as false, usually at the most expensive moment possible.

## The Anatomy of Dangerous Assumptions

### Linguistic Markers of Hidden Assumptions
Learn to recognize the language patterns that conceal assumptions:

#### The Certainty Markers
- **"Obviously"** → Nothing is obvious until verified
- **"Of course"** → Courses can change direction  
- **"Naturally"** → Nature requires specification
- **"Clearly"** → Clarity demands definition
- **"Everyone knows"** → Knowledge must be documented

#### The Approximation Markers  
- **"About"** → Mathematical precision required
- **"Roughly"** → Roughness has no tolerance
- **"More or less"** → Engineering allows no "or"
- **"Around"** → Circles have defined radii
- **"Approximately"** → Approximations compound to failures

#### The Deferral Markers
- **"We'll figure it out"** → Crisis scheduling
- **"That's a detail"** → Details determine success
- **"Later"** → Later becomes never
- **"Eventually"** → Events require timing
- **"When we get there"** → Location undefined

#### The Authority Markers
- **"Trust me"** → Trust requires verification
- **"I've done this before"** → Past ≠ Present conditions
- **"The vendor says"** → Vendors have motivations
- **"Standard practice"** → Standards require identification
- **"Industry norm"** → Norms have variations

## The Assumption Challenging Arsenal

### Technique 1: The Evidence Demand
**Principle**: Every assumption must produce evidence or acknowledge uncertainty

**Pattern**: "You've stated X. What evidence supports this assumption?"

**Examples**:
```
Assumption: "The PCB is about 100mm long"
Challenge: "What is the source of that dimension?"
Evidence: "I'm estimating from the schematic"
Follow-up: "What uncertainty exists in that estimate?"
Result: "Could be 95-105mm, requires physical verification"
```

### Technique 2: The Alternative Reality Test
**Principle**: Explore what happens if the assumption is false

**Pattern**: "What if X is not true? How would that change our requirements?"

**Examples**:
```
Assumption: "Users will always power down before service"
Challenge: "What if they service it while powered?"
Result: "Need safe access procedures and LOTO requirements"

Assumption: "The component will mount flat"
Challenge: "What if thermal expansion warps the mounting?"
Result: "Need flexible mounting system or thermal analysis"
```

### Technique 3: The Specification Probe
**Principle**: Force vague statements to become specific requirements

**Pattern**: "When you say Y, what exact specifications define Y?"

**Examples**:
```
Assumption: "Standard mounting holes"
Challenge: "Which standard? What thread? What spacing?"
Result: "M4 × 0.7 threads on 100mm centers per DIN 43880"

Assumption: "Waterproof enough"
Challenge: "What IP rating? What duration? What pressure?"  
Result: "IP65 rating, 30-minute spray test at 12.5L/min"
```

### Technique 4: The Stakeholder Multiplier
**Principle**: Different stakeholders reveal different assumption layers

**Pattern**: "How would [stakeholder] view this assumption?"

**Examples**:
```
Assumption: "Easy to assemble"  
Manufacturing view: "With what tools? In what time?"
Service view: "Can it be disassembled for repair?"
User view: "Can untrained personnel handle it?"
Safety view: "What are the injury risks during assembly?"
```

### Technique 5: The Time Dimension Probe
**Principle**: Assumptions that hold today may fail tomorrow

**Pattern**: "How might this assumption change over [time period]?"

**Examples**:
```
Assumption: "Component will remain available"
Time probe: "What's the manufacturer's lifecycle plan?"
Result: "Need second source or redesign timeline"

Assumption: "Current regulations will remain stable"  
Time probe: "What regulatory changes are under review?"
Result: "Need forward-compatibility design margins"
```

## Advanced Assumption Challenging Techniques

### The Constraint Cascade Analysis
**Purpose**: Reveal how assumptions create constraint chains

**Method**:
1. Identify the assumption
2. Map all constraints that depend on it  
3. Trace secondary and tertiary effects
4. Calculate total impact if assumption fails

**Example**:
```
Assumption: "Housing material will be ABS plastic"
↓ Constraint Cascade:
- Temperature limit: 80°C continuous
- Chemical compatibility: Limited to pH 6-8
- UV resistance: Indoor use only
- Manufacturing: Injection molding required
- Cost impact: Tooling required for quantities >1000
- Lead time: 12-week mold fabrication

Challenge Result: Need material selection matrix considering all constraints
```

### The Physics Reality Check
**Purpose**: Test assumptions against physical laws

**Method**:
1. Extract the physics implied by the assumption
2. Apply relevant equations and limits
3. Check against material properties and natural laws
4. Identify violations or edge conditions

**Example**:
```
Assumption: "Convection cooling will be sufficient"
Physics check:
- Heat generation: 15W component in 50mm³ space
- Power density: 300W/cm³ (extremely high)
- Natural convection limit: ~1W/cm² without forced air
- Violation: Requires active cooling or larger form factor
```

### The Historical Precedent Investigation
**Purpose**: Learn from similar projects' assumption failures

**Method**:
1. Identify comparable projects or systems
2. Research documented failures or issues  
3. Trace failures back to assumption errors
4. Apply lessons to current assumptions

**Example**:
```
Assumption: "Prototype tolerances will work in production"
Historical precedent: Project Delta (2019)
- Prototype: Hand-fitted, worked perfectly
- Production: 30% failure rate due to tolerance stack-up
- Lesson: Statistical tolerance analysis required before production
- Application: All critical dimensions need 6-sigma analysis
```

## The Systematic Assumption Audit Protocol

### Phase 1: Assumption Inventory
Document all assumptions embedded in the requirements:
```yaml
assumption_inventory:
  dimensional:
    - "PCB fits in housing" → Need verified PCB dimensions
    - "Connectors face outward" → Need connector orientation verification
  functional:
    - "Will operate at room temperature" → Define temperature range
    - "User has basic tools" → Define "basic tool set"
  temporal:
    - "Components remain available" → Check lifecycle status
    - "Regulations won't change" → Check regulatory roadmap
```

### Phase 2: Risk Assessment
Rate each assumption on two axes:
- **Impact**: Cost of assumption being wrong (1-5 scale)
- **Probability**: Likelihood of assumption being wrong (1-5 scale)
- **Risk Score**: Impact × Probability

### Phase 3: Verification Planning
For each high-risk assumption (score ≥ 12):
```yaml
assumption: "Component height is 43mm"
risk_score: 20 (Impact: 5, Probability: 4)
verification_plan:
  method: "Physical measurement with calibrated caliper"
  responsible: "Hardware engineer"
  deadline: "Before CAD work begins"
  backup_plan: "Vendor drawing verification if component unavailable"
```

### Phase 4: Assumption Resolution
Transform assumptions into verified facts or documented uncertainties:

**Before**: "The board should fit"
**After**: "PCB dimensions verified: 114.2 × 86.5 × 1.6mm ±0.1mm (measured 3 samples)"

## Common Assumption Categories and Challenges

### Dimensional Assumptions
**Pattern**: Physical fit, clearance, and space allocation
**Challenge Method**: Demand measurements, calculate stack-ups
**Example**: "There's room for cables" → "What is the required bend radius and volume?"

### Functional Assumptions  
**Pattern**: Performance, capability, and behavior expectations
**Challenge Method**: Define test criteria, specify conditions
**Example**: "It should be fast enough" → "What response time is required? Under what load?"

### Environmental Assumptions
**Pattern**: Operating conditions and environmental factors
**Challenge Method**: Specify ranges, test limits, define margins
**Example**: "Normal operating conditions" → "Temperature: -10°C to +60°C, Humidity: 20-80% RH"

### User Assumptions
**Pattern**: User behavior, skills, and expectations
**Challenge Method**: Task analysis, skill assessment, workflow mapping
**Example**: "Users will read the manual" → "What happens if they don't? How is critical information communicated?"

### Interface Assumptions
**Pattern**: Compatibility, protocols, and connectivity
**Challenge Method**: Protocol verification, pin-out confirmation, version checking
**Example**: "Uses standard USB" → "USB 2.0, 3.0, 3.1? Type A, B, C? Power delivery requirements?"

## The Meta-Assumption Challenge

The most dangerous assumption is that you've found all the assumptions. Guard against this through:

### The Assumption Humility Principle
Always ask: "What assumptions am I not seeing?"

### The Fresh Eyes Protocol  
Have different people review requirements to spot assumptions you've missed

### The Adversarial Review
Deliberately try to break the requirements by challenging every statement

### The Time-Delayed Review
Revisit requirements after a delay to see them with fresh perspective

## Success Metrics for Assumption Challenging

You have successfully challenged assumptions when:

1. **No approximation language** remains in critical requirements
2. **All "obvious" statements** have been questioned and justified
3. **Evidence exists** for every claimed fact
4. **Alternative scenarios** have been explored for key assumptions
5. **Verification plans** exist for all unproven assumptions
6. **Risk assessment** completed for assumption failure modes
7. **Stakeholders agree** on assumption validity or acknowledge uncertainty

## The Assumption Challenger's Oath

*"I assume nothing without evidence. I question everything that seems obvious. I probe every 'of course' until it becomes 'because of this specific verified fact'. I transform comfortable assumptions into uncomfortable questions, and then into verified answers. I am the guardian against the tyranny of the unexamined assumption."*

Remember: Challenging assumptions is not about being difficult - it's about being thorough. Every assumption you expose and verify now prevents a crisis later. The assumptions you catch are invisible victories that save exponentially more cost than the time invested in questioning them.