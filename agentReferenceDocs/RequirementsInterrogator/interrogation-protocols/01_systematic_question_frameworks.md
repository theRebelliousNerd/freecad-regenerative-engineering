# Systematic Question Frameworks

## The Architecture of Inquiry

Effective requirements interrogation is not random questioning but follows systematic frameworks that ensure comprehensive coverage, logical progression, and measurable outcomes. This document provides the foundational question architectures that drive successful requirements extraction.

## Framework 1: The Question Hierarchy Pyramid

### Level 1: Foundational Questions (The Base)
**Purpose**: Establish context and fundamental understanding
**Characteristics**: Broad, open-ended, exploratory
**Response Goal**: Rich narrative and context

**Core Questions**:
- "What problem are you trying to solve?"
- "Why does this problem matter?"
- "What happens if this problem isn't solved?"
- "Who is affected by this problem?"

### Level 2: Analytical Questions (The Body) 
**Purpose**: Break down complex problems into manageable components
**Characteristics**: Structured, comparative, prioritizing
**Response Goal**: Categorized information with relationships

**Core Questions**:
- "What are the different aspects of this problem?"
- "Which aspects are most critical?"
- "How do these aspects interact with each other?"
- "What constraints limit possible solutions?"

### Level 3: Specification Questions (The Peak)
**Purpose**: Define precise, measurable requirements
**Characteristics**: Specific, quantitative, verifiable
**Response Goal**: Implementable specifications

**Core Questions**:
- "What exactly must be achieved?"
- "How will success be measured?"
- "What are the acceptance criteria?"
- "How will this be verified?"

## Framework 2: The 5W+2H Systematic Coverage

### Who Questions (Stakeholder Discovery)
- **Who** is the primary user?
- **Who** else is affected by this system?
- **Who** makes the final decisions?
- **Who** maintains or services it?
- **Who** pays for it?
- **Who** has veto power over design choices?

### What Questions (Functional Discovery)
- **What** must this system accomplish?
- **What** are the inputs and outputs?
- **What** performance levels are required?
- **What** interfaces must it support?
- **What** should it NOT do?
- **What** happens when it fails?

### When Questions (Temporal Discovery)
- **When** will this be used?
- **When** must it be completed?
- **When** are peak usage periods?
- **When** does maintenance occur?
- **When** might requirements change?
- **When** will this become obsolete?

### Where Questions (Environmental Discovery)
- **Where** will this be installed or used?
- **Where** are the environmental extremes?
- **Where** do space constraints apply?
- **Where** are the interfaces located?
- **Where** does service access occur?
- **Where** are the regulatory jurisdictions?

### Why Questions (Purpose Discovery)
- **Why** is this needed now?
- **Why** are these specific requirements stated?
- **Why** not use existing solutions?
- **Why** these particular constraints?
- **Why** this timeline?
- **Why** this approach?

### How Questions (Method Discovery)
- **How** will this be used day-to-day?
- **How** will it be manufactured or built?
- **How** will quality be verified?
- **How** will changes be managed?
- **How** will success be measured?
- **How** will failures be handled?

### How Much/Many Questions (Quantitative Discovery)
- **How much** will this cost?
- **How many** units are needed?
- **How much** space is available?
- **How much** time is available?
- **How much** performance is required?
- **How much** risk is acceptable?

## Framework 3: The Requirement Type Classification System

### Functional Requirements Framework
**Purpose**: Capture what the system must do

**Question Pattern**: 
```
"The system shall [action] [object] [condition]"
Validation: "How do we verify this behavior?"
```

**Example Sequence**:
```
Q: "What must the system do when the user presses the start button?"
A: "Begin the heating cycle"
Q: "What specific actions constitute 'begin the heating cycle'?"
A: "Turn on heating element, start timer, display status"
Q: "How do we verify each of these actions occurs?"
A: "LED indicators, temperature sensor feedback, display status"
```

### Non-Functional Requirements Framework
**Purpose**: Capture quality attributes and constraints

**Question Categories**:

#### Performance Questions
- "How fast must [operation] complete?"
- "What throughput is required under normal load?"
- "What response time is acceptable to users?"
- "How many concurrent [operations] must be supported?"

#### Reliability Questions
- "What availability level is required?"
- "How often can the system be unavailable for maintenance?"
- "What is the mean time between failures target?"
- "How long can maintenance take?"

#### Usability Questions
- "What is the acceptable learning curve for new users?"
- "How many steps should common tasks require?"
- "What error rate is acceptable?"
- "What accessibility requirements apply?"

#### Security Questions
- "What information needs protection?"
- "Who should have access to what functions?"
- "How will user identity be verified?"
- "What happens if security is compromised?"

### Constraint Requirements Framework
**Purpose**: Capture limitations and boundaries

**Constraint Categories**:

#### Physical Constraints
- "What space limitations exist?"
- "What weight restrictions apply?"
- "What environmental conditions must be handled?"
- "What materials are required or prohibited?"

#### Interface Constraints
- "What existing systems must this connect to?"
- "What communication protocols are required?"
- "What data formats must be supported?"
- "What legacy compatibility is needed?"

#### Regulatory Constraints
- "What standards must be met?"
- "What certifications are required?"
- "What testing must be performed?"
- "What documentation must be provided?"

## Framework 4: The Assumption Interrogation Matrix

### Assumption Detection Triggers
Watch for these language patterns that indicate hidden assumptions:

#### Certainty Language
- "Obviously" → "What makes this obvious?"
- "Clearly" → "What evidence makes this clear?"
- "Of course" → "What course of reasoning leads here?"
- "Everyone knows" → "How do we verify this knowledge?"

#### Approximation Language
- "About" → "What's the exact value and uncertainty?"
- "Roughly" → "What precision is actually required?"
- "Around" → "What's the acceptable range?"
- "More or less" → "What's the tolerance specification?"

#### Authority Language
- "The vendor says" → "What's the source document?"
- "Industry standard" → "Which specific standard?"
- "Best practice" → "According to whom, and when?"
- "Common knowledge" → "What's the authoritative source?"

### Assumption Validation Framework

#### Step 1: Assumption Identification
"I notice you said [assumption]. Let's explore that."

#### Step 2: Source Investigation  
"What's the basis for that assumption?"

#### Step 3: Evidence Demand
"What evidence supports this assumption?"

#### Step 4: Consequence Analysis
"What happens if this assumption is wrong?"

#### Step 5: Verification Planning
"How can we verify this assumption?"

## Framework 5: The Stakeholder Perspective Matrix

### Multi-Stakeholder Question Set

#### For Each Identified Stakeholder:

**Context Questions**:
- "What is [stakeholder]'s role in this system?"
- "What does success look like to [stakeholder]?"
- "What are [stakeholder]'s main concerns?"
- "How does [stakeholder] measure value?"

**Interaction Questions**:
- "How often does [stakeholder] interact with this system?"
- "What skills does [stakeholder] bring to these interactions?"
- "What tools does [stakeholder] typically have available?"
- "What constraints does [stakeholder] operate under?"

**Satisfaction Questions**:
- "What would delight [stakeholder] about this system?"
- "What would frustrate [stakeholder] most?"
- "What would cause [stakeholder] to reject this system?"
- "How will [stakeholder] measure the system's success?"

### Stakeholder Conflict Resolution Framework

**Conflict Detection**:
- "I notice [stakeholder A] wants X, but [stakeholder B] wants Y. Help me understand this difference."

**Priority Investigation**:
- "If you had to choose between satisfying [stakeholder A] and [stakeholder B], which would you choose and why?"

**Compromise Exploration**:
- "What would a solution that partially satisfies both look like?"
- "Where is there flexibility in each stakeholder's requirements?"

**Win-Win Discovery**:
- "Is there a way to frame this that benefits both stakeholders?"
- "What underlying need do both stakeholders share?"

## Framework 6: The Requirements Completeness Audit

### The Checklist Framework

#### Coverage Verification Questions:
- "What aspects of this system haven't we discussed?"
- "What questions would [other team member] ask that we haven't covered?"
- "What could go wrong that we haven't considered?"
- "What scenarios haven't we explored?"

#### Detail Sufficiency Questions:
- "Is there enough information to start implementation?"
- "What details would the implementer need to know?"
- "How will we know when each requirement is satisfied?"
- "What could be misunderstood in these requirements?"

#### Consistency Validation Questions:
- "Do any of these requirements conflict with each other?"
- "Are the performance and cost requirements realistic together?"
- "Do all stakeholders agree with this prioritization?"
- "Are the timeline and scope aligned?"

## Framework Application Guidelines

### Choosing the Right Framework

**For New Projects**: Start with Question Hierarchy Pyramid
**For Complex Systems**: Use 5W+2H Systematic Coverage
**For Stakeholder Conflicts**: Apply Stakeholder Perspective Matrix
**For Assumption-Heavy Projects**: Focus on Assumption Interrogation Matrix
**For Final Validation**: Use Requirements Completeness Audit

### Framework Combination Strategies

**Sequential Application**: Start broad (Pyramid Level 1) → Get systematic (5W+2H) → Go deep (Assumption Matrix) → Validate (Completeness Audit)

**Parallel Application**: Apply multiple frameworks simultaneously to cross-check coverage

**Iterative Application**: Repeat frameworks at increasing levels of detail

### Success Metrics for Framework Application

You are successfully using systematic question frameworks when:

1. **Coverage is Comprehensive**: No major requirement area is missed
2. **Detail is Appropriate**: Questions yield implementable specifications
3. **Assumptions are Surfaced**: Hidden assumptions become explicit requirements
4. **Stakeholders are Aligned**: Different perspectives are captured and reconciled
5. **Validation is Planned**: Methods for verification are established
6. **Progression is Logical**: Questions build upon each other systematically

## Framework Customization Guidelines

### Domain-Specific Adaptations

**For Physical Products**: Emphasize dimensional, thermal, and assembly questions
**For Software Systems**: Focus on functional, performance, and interface questions
**For Services**: Prioritize workflow, stakeholder, and quality questions
**For Systems Integration**: Highlight interface, compatibility, and protocol questions

### Project Phase Adaptations

**Early Phase**: Broad, exploratory questions from Level 1 of Pyramid
**Middle Phase**: Systematic coverage using 5W+2H framework
**Late Phase**: Detailed validation using Completeness Audit

## Common Framework Application Errors

1. **Skipping Levels**: Jumping to detailed questions without broad understanding
2. **Framework Rigidity**: Following frameworks too mechanically without adaptation
3. **Question Overload**: Applying too many frameworks simultaneously
4. **Coverage Gaps**: Missing systematic application of complete frameworks
5. **Validation Neglect**: Not using completeness frameworks to verify coverage

Remember: These frameworks are guides, not rigid scripts. Adapt them to your specific context while maintaining their systematic nature and comprehensive coverage goals. The goal is complete requirements, not perfect framework compliance.