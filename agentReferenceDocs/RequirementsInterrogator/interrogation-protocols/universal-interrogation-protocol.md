# Universal Interrogation Protocol

## The Master Interrogation Framework

This protocol provides the systematic approach to extracting complete requirements from any project type. It follows a structured progression from broad understanding to precise specifications.

## The Four-Phase Interrogation Structure

### Phase 1: Context & Purpose Discovery
**Goal**: Understand the fundamental "why" behind the request
**Duration**: 15-20% of total interrogation time
**Output**: Clear problem statement and success criteria

### Phase 2: Constraint & Boundary Identification
**Goal**: Map all limitations and non-negotiable requirements
**Duration**: 25-30% of total interrogation time
**Output**: Complete constraint matrix with priorities

### Phase 3: Stakeholder & Workflow Mapping
**Goal**: Identify all affected parties and use cases
**Duration**: 25-30% of total interrogation time  
**Output**: Stakeholder analysis and workflow documentation

### Phase 4: Specification & Validation
**Goal**: Convert understanding into precise, measurable requirements
**Duration**: 25-35% of total interrogation time
**Output**: Complete requirements blueprint ready for implementation

## Phase 1: Context & Purpose Discovery

### The Opening Questions
Start every interrogation with these fundamental probes:

1. **The Prime Mover Question**
   - "What is the single most important problem this solves?"
   - Follow-up: "What happens if this problem is not solved?"

2. **The Value Proposition Probe**
   - "What job is the user hiring this product to do?"
   - Follow-up: "How is that job being done today, and why is that inadequate?"

3. **The Success Definition**
   - "How will you know when this is successful?"
   - Follow-up: "What are the measurable criteria for success?"

4. **The Failure Mode Exploration**
   - "What would make this project a failure?"
   - Follow-up: "What are you most worried about going wrong?"

### Context Mapping Techniques

#### The Five Whys Deep Dive
Apply the "Five Whys" to the core purpose:
```
User: "I need an enclosure for electronics"
Q1: "Why do the electronics need an enclosure?"
A1: "To protect them from weather"
Q2: "Why will they be exposed to weather?"
A2: "Because they're installed outdoors"
Q3: "Why must they be installed outdoors?"
A3: "Because indoor space isn't available"
Q4: "Why isn't indoor space available?"
A4: "Because of building size constraints"
Q5: "Why are there building size constraints?"
A5: "Because of zoning setback requirements"
```

**Result**: The real requirement is "compact outdoor installation that meets zoning requirements" - much more specific than "weather protection."

#### The Temporal Scope Analysis
- "How long must this solution last?"
- "What changes are expected over time?"
- "How will maintenance needs evolve?"
- "What happens when components become obsolete?"

### Context Validation Checklist
- [ ] Core problem clearly articulated
- [ ] Success criteria measurable and specific
- [ ] Failure modes identified and prioritized
- [ ] Timeline and lifecycle requirements understood
- [ ] Business/personal context documented

## Phase 2: Constraint & Boundary Identification

### The Constraint Discovery Matrix

#### Physical Constraints
- "What space limitations exist?"
- "What environmental conditions must be handled?"
- "Are there weight, size, or mounting restrictions?"
- "What materials are prohibited or required?"

#### Performance Constraints
- "What are the minimum performance requirements?"
- "What are the maximum operating conditions?"
- "What reliability/availability targets must be met?"
- "Are there speed, capacity, or throughput minimums?"

#### Economic Constraints
- "What is the target cost per unit?"
- "What is the development budget?"
- "Are there recurring vs. non-recurring cost priorities?"
- "What drives the cost sensitivity?"

#### Regulatory/Safety Constraints
- "What standards or regulations apply?"
- "Are there safety certifications required?"
- "What compliance documentation is needed?"
- "Are there liability or insurance implications?"

#### Temporal Constraints
- "When is the absolute deadline?"
- "What are the key milestone dates?"
- "How does timing affect requirements?"
- "What constraints exist on development phases?"

### The Constraint Priority Protocol

Classify each constraint using the MoSCoW method:

#### Must Have (Non-negotiable)
- Safety requirements
- Regulatory compliance
- Physical impossibilities
- Absolute deadlines

#### Should Have (High Priority)
- Performance targets
- Quality standards
- Cost objectives
- User experience goals

#### Could Have (Nice to Have)
- Convenience features
- Aesthetic preferences
- Future expansion capabilities
- Optimization opportunities

#### Won't Have (Explicitly Excluded)
- Features for later versions
- Requirements outside scope
- Conflicting alternatives
- Resource-intensive extras

### Constraint Validation Questions
- "What happens if this constraint is violated?"
- "Who enforces this constraint and how?"
- "Is this constraint absolute or can it be negotiated?"
- "What is the cost/impact of meeting this constraint?"

## Phase 3: Stakeholder & Workflow Mapping

### The Stakeholder Discovery Process

#### Primary Stakeholders (Direct Users)
- "Who will use this directly?"
- "What is their skill level and training?"
- "How frequently will they interact with it?"
- "What tools/equipment do they typically have available?"

#### Secondary Stakeholders (Indirect Impact)
- "Who is affected by this but doesn't use it directly?"
- "Who maintains, repairs, or services it?"
- "Who installs or configures it?"
- "Who pays for it and who approves purchases?"

#### Hidden Stakeholders (Often Overlooked)
- "Who must approve or certify this?"
- "Who transports, stores, or handles it?"
- "Who disposes of it at end of life?"
- "Who investigates when something goes wrong?"

### The Workflow Deep Dive

#### Happy Path Analysis
- "Walk me through the ideal use scenario step by step"
- "What happens before the user interacts with this?"
- "What happens after they're done with it?"
- "What information or resources do they need at each step?"

#### Error Recovery Analysis  
- "What happens when something goes wrong?"
- "How does the user know there's a problem?"
- "What can they do to fix problems themselves?"
- "When do they need to call for help?"

#### Edge Case Exploration
- "What's the most extreme use case you can imagine?"
- "What happens during peak usage?"
- "How is this used differently by different types of users?"
- "What seasonal or cyclical variations exist?"

### Workflow Documentation Template
```yaml
workflow_name: "Component Replacement"
trigger: "Failure indication or scheduled maintenance"
frequency: "Monthly for preventive, ad-hoc for failures"
duration: "Target: 15 minutes maximum"
actors:
  - name: "Field Technician"
    skills: "Basic electrical, standard tools"
    context: "Often working in cramped conditions"
steps:
  1. 
    action: "Power down system"
    time: "30 seconds"
    tools: "None"
    failure_modes: ["Live work if power not available"]
  2:
    action: "Remove access panel"
    time: "2 minutes"
    tools: ["Phillips screwdriver"]
    failure_modes: ["Screws seized", "Panel warped"]
```

## Phase 4: Specification & Validation

### The Specification Extraction Process

#### From Qualitative to Quantitative
Transform descriptive requirements into measurable specifications:

**Example Transformation**:
- Qualitative: "Easy to access for maintenance"
- Quantitative: "All serviceable components accessible with standard tools within 15-minute MTTR"

#### The Measurement Challenge
For each requirement, demand:
- "How will you measure this?"
- "What tools or methods are needed for verification?"
- "What constitutes pass vs. fail?"
- "Who performs the verification and when?"

### The Specification Completeness Matrix

#### Functional Requirements
- [ ] What the system must do (behavior)
- [ ] Performance levels (speed, capacity, accuracy)
- [ ] Input/output specifications
- [ ] Interface requirements

#### Non-Functional Requirements  
- [ ] Quality attributes (reliability, usability, security)
- [ ] Environmental conditions
- [ ] Maintainability and serviceability
- [ ] Scalability and upgradability

#### Design Constraints
- [ ] Technology or material restrictions
- [ ] Standards and regulations compliance
- [ ] Compatibility requirements
- [ ] Physical limitations

#### Process Requirements
- [ ] Development methodology constraints
- [ ] Documentation requirements
- [ ] Testing and validation procedures
- [ ] Acceptance criteria and procedures

### The Requirements Validation Protocol

#### Completeness Check
- "Is there any requirement we haven't discussed that could impact the design?"
- "What questions might other team members ask that we haven't covered?"
- "Are there any assumptions we're making that should be stated explicitly?"

#### Consistency Check
- "Do any of these requirements conflict with each other?"
- "Are the performance and cost requirements realistic together?"
- "Do the timeline and scope requirements align?"

#### Testability Check
- "How will we verify that each requirement has been met?"
- "What evidence will demonstrate compliance?"
- "Who has authority to accept or reject the implementation?"

## Universal Red Flag Indicators

Stop and drill deeper when you hear:

### Vagueness Flags
- "About", "roughly", "approximately"
- "Standard", "typical", "normal"
- "Adequate", "sufficient", "reasonable"
- "Simple", "basic", "straightforward"

### Assumption Flags
- "Obviously", "of course", "naturally"
- "Everyone knows", "it's common practice"
- "That's standard in the industry"
- "We've always done it this way"

### Deferral Flags
- "We'll figure that out later"
- "That's a detail for implementation"
- "Let's not worry about that now"
- "Cross that bridge when we come to it"

### Overconfidence Flags
- "Trust me", "I'm sure", "definitely"
- "It should work", "it'll be fine"
- "No problem", "piece of cake"
- "Just like the last project"

## Protocol Success Indicators

You have successfully completed the Universal Interrogation Protocol when:

1. **Purpose is Crystal Clear**: Anyone can understand what problem is being solved and why
2. **Constraints are Documented**: All limitations are explicit with priorities
3. **Stakeholders are Mapped**: All affected parties identified with their needs
4. **Workflows are Detailed**: Step-by-step processes documented including error cases
5. **Specifications are Measurable**: Every requirement has quantifiable acceptance criteria
6. **Validation Plan Exists**: Clear methods for verifying requirements are met
7. **No Assumptions Remain**: All unstated assumptions have been surfaced and documented

## Closing Protocol

End every interrogation session with:

1. **Requirement Summary Review**: "Let me summarize what I understand..."
2. **Gap Identification**: "What questions remain unanswered?"
3. **Action Item Assignment**: "What research or measurement needs to happen next?"
4. **Stakeholder Validation**: "Who else needs to review these requirements?"
5. **Change Control**: "How will we handle requirement changes going forward?"

The Universal Interrogation Protocol transforms vague user intentions into precise engineering specifications through systematic, thorough questioning. Master this protocol, and you will prevent the vast majority of requirements failures that plague engineering projects.