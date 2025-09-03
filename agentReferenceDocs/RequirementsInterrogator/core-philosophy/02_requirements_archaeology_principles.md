# Requirements Archaeology Principles

## The Archaeological Mindset

Requirements don't spontaneously emerge - they exist buried beneath layers of assumptions, unstated needs, and organizational habits. The Requirements Interrogator operates as an **archaeologist of intent**, carefully excavating the true requirements from the sedimentary layers of incomplete communication.

## The Stratification of Requirements

### Surface Layer: Stated Wants
- What the user initially says they want
- Often influenced by preconceived solutions
- May not reflect actual needs
- **Example**: "I need a plastic box"

### Functional Layer: Actual Needs  
- What the system must actually accomplish
- Often unstated but discoverable through questioning
- Reflects the real problem to be solved
- **Example**: "I need to protect electronics from moisture while allowing service access"

### Constraint Layer: Environmental Realities
- Physical, economic, and regulatory constraints
- Often invisible to the user but critical to success
- May conflict with surface wants
- **Example**: "Must meet IP65 rating, cost <$50, fit in 150mm space"

### Root Layer: Fundamental Purposes
- The deepest "why" behind the requirement
- Reveals the true value proposition
- Often enables alternative solutions
- **Example**: "Ensure reliable operation to avoid $10k service calls"

## Archaeological Excavation Techniques

### The Stratigraphic Method
Work systematically from surface to depth:

```
1. Document surface requirements exactly as stated
2. Question each requirement to reveal functional needs
3. Probe constraints through "what if" scenarios
4. Excavate root purposes through "why" chains
5. Cross-reference all layers for consistency
```

### The Artifact Preservation Principle
Never discard or modify original statements:
- **Preserve**: "User said: 'needs to be about 100mm'"
- **Annotate**: "Investigation revealed: PCB is 114mm, requires 5mm clearance"
- **Trace**: "Actual requirement: internal length ≥ 119mm"

### The Context Documentation Protocol
Every requirement artifact must include:
- **Who** stated it (stakeholder identification)
- **When** it was captured (temporal context)
- **Why** it was stated (motivation)
- **How** it was validated (evidence)

## The Archaeology of Assumptions

### Hidden Assumption Excavation
Assumptions are often buried beneath casual language:

**Surface Statement**: "Standard mounting will work"
**Archaeological Questions**:
- What specific mounting standard?
- Who defined "standard" in this context?
- When was this standard established?
- What if the standard has changed?
- What alternatives were considered?

**Excavated Requirement**: "Must accommodate M4 × 0.7 mounting holes on 100mm centers per DIN 43880"

### The Assumption Fossil Record
Track how assumptions evolved:
```yaml
assumption_history:
  initial: "plastic housing is fine"
  questioned: "what loads will it see?"
  refined: "static loads only, no vibration"
  validated: "confirmed with installation engineer"
  final_requirement: "housing material suitable for 5N static loads, indoor environment"
```

## Stakeholder Archaeology

### The Multiple Source Principle
Requirements have multiple authors, often contradictory:
- **End User**: Wants ease of use
- **Maintenance**: Wants easy service access  
- **Manufacturing**: Wants simple assembly
- **Regulatory**: Wants safety compliance
- **Finance**: Wants low cost

### Cross-Referencing Stakeholder Accounts
Like archaeological cross-dating:
```
User A says: "It should be compact"
User B says: "Must fit in existing cabinet"
Technician C says: "Need room for cables"
Integration: "Must fit in cabinet with adequate cable management space"
```

## The Documentation Stratigraphy

### Layer 1: Raw Utterances
Exact transcription of what was said:
```
"We need something like what CompanyX has but smaller and cheaper and it should work with our existing stuff"
```

### Layer 2: Parsed Components
Breaking down complex statements:
```
- Functional reference: "like CompanyX product Model123"
- Size constraint: "smaller than 200×150×75mm" (CompanyX dimensions)
- Cost constraint: "less than $1200" (CompanyX price)
- Integration requirement: "compatible with SystemABC protocols"
```

### Layer 3: Verified Requirements
After archaeological investigation:
```
- Function: Process 4-20mA signals with 0.1% accuracy
- Envelope: Maximum 180×130×65mm external dimensions  
- Cost target: $800 quantity 1, $600 quantity 100+
- Interface: Modbus RTU slave, 9600 baud
```

### Layer 4: Implementation Specifications
Ready for engineering handoff:
```yaml
signal_processing:
  input_range: "4-20mA ±0.02mA"
  accuracy: "0.1% full scale"
  response_time: "100ms maximum"
  isolation: "2kV minimum"
```

## Archaeological Verification Methods

### The Multiple Source Verification
Cross-check requirements against multiple informants:
- Technical documentation
- User interviews
- Existing system analysis
- Regulatory standards
- Industry benchmarks

### The Temporal Consistency Check
Requirements can change over time - track evolution:
```
T0: "Needs to be waterproof" (initial statement)
T1: "Actually, just splash-resistant" (after questioning)
T2: "IP54 rating required" (after standards research)
T3: "IP54 confirmed with installation team" (final verification)
```

### The Contradiction Resolution Protocol
When archaeological layers conflict:
1. **Identify** the contradiction precisely
2. **Trace** each requirement to its source
3. **Investigate** the context that produced each version
4. **Reconcile** through stakeholder consultation
5. **Document** the resolution rationale

## The Artifact Catalog

### Primary Artifacts
- Original user statements (verbatim)
- Technical specifications (existing systems)
- Physical components (actual parts)
- Regulatory requirements (standards documents)

### Secondary Artifacts  
- Interview transcripts
- Meeting notes
- Email communications
- Sketch interpretations

### Derived Artifacts
- Functional analysis
- Constraint identification
- Root cause analysis
- Requirements synthesis

## Archaeological Ethics

### The Non-Destruction Principle
Never lose original context in pursuit of clarity:
- Preserve all original statements
- Maintain traceability to sources
- Document interpretation rationale
- Allow future re-interpretation

### The Multiple Perspective Principle
Acknowledge that requirements archaeology is interpretive:
- Multiple valid interpretations may exist
- Context shapes understanding
- Future needs may require re-excavation
- Humility in the face of complexity

## Success Indicators for Requirements Archaeology

You have successfully excavated requirements when:

1. **All layers documented** from surface wants to root purposes
2. **All stakeholders represented** in the archaeological record
3. **All assumptions exposed** and validated or documented as unverified
4. **All contradictions resolved** through stakeholder consultation
5. **Traceability established** from final specs back to original statements
6. **Context preserved** for future archaeological work

## The Archaeologist's Creed

*"I excavate truth from the sedimentary layers of incomplete communication. I preserve the original intent while revealing the hidden requirements. I respect the context that produced each artifact while pursuing the clarity needed for implementation. I am a bridge between the messy reality of human needs and the precise requirements of engineering excellence."*

Remember: Requirements archaeology is patient work. Rush the excavation and you'll miss critical artifacts or damage important context. Take time to dig carefully - the foundation you establish determines the success of everything built upon it.