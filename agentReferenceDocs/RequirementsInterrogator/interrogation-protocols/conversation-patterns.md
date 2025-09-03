# Conversation Patterns for Requirements Interrogation

## Master Conversation Frameworks

This document provides proven conversation patterns and dialogue structures for systematic requirements extraction. Each pattern is designed to elicit specific types of information while maintaining user engagement and building comprehensive understanding.

## Pattern 1: The Dimensional Probe Sequence

**Use Case**: When users provide vague dimensional requirements
**Goal**: Extract precise measurements with uncertainty bounds

### The Basic Sequence
```
User: "I need a box about 100mm wide"
Interrogator: "What determines that 100mm dimension?"
User: "The circuit board inside"
Interrogator: "Have you physically measured the circuit board?"
User: "No, but the schematic says 100mm"
Interrogator: "Schematics can have errors. What's your plan to verify the actual dimension?"
User: "I could measure it when I get the board"
Interrogator: "When will you have the physical board?"
User: "Next week"
Interrogator: "What tolerance do you expect between schematic and actual board?"
User: "Maybe 2-3mm"
Interrogator: "So the board could be as large as 103mm. What clearance do you need around the board?"
User: "I don't know, maybe 5mm?"
Interrogator: "What determines that clearance requirement?"
```

### Advanced Dimensional Follow-ups
- "What's the measurement uncertainty of your measuring tool?"
- "How do you account for thermal expansion?"
- "What manufacturing tolerances apply to your enclosure?"
- "How do dimensional errors compound through the assembly?"

### Pattern Outcome
Transforms "about 100mm" into:
- Verified board dimension: TBD (measurement required)
- Expected tolerance: ±2-3mm
- Required clearance: TBD (analysis required)
- Minimum internal width: 108mm (preliminary)

## Pattern 2: The Assumption Excavation Protocol

**Use Case**: When users state requirements as obvious facts
**Goal**: Surface and validate hidden assumptions

### The Basic Sequence
```
User: "Obviously it needs to be plastic"
Interrogator: "What makes plastic the obvious choice?"
User: "It's cheaper than metal"
Interrogator: "Cheaper in what sense - material cost, manufacturing cost, or total cost?"
User: "Material cost, I think"
Interrogator: "What's your target cost per unit?"
User: "I don't know, just cheap"
Interrogator: "Help me understand - are we talking $1, $10, or $100 per unit?"
User: "Maybe $20 per unit"
Interrogator: "What percentage of that $20 can the enclosure represent?"
User: "Probably 20-30%"
Interrogator: "So $4-6 per enclosure. What plastic costs have you researched?"
User: "I haven't really looked into it"
Interrogator: "What properties does the enclosure need besides low cost?"
```

### Advanced Assumption Challenges
- "What evidence supports that assumption?"
- "Who else shares that assumption, and what's their expertise?"
- "What would happen if that assumption is wrong?"
- "What alternative approaches haven't been considered?"

### Pattern Outcome
Transforms "obviously plastic" into:
- Cost target: $4-6 per enclosure
- Required properties: TBD (analysis needed)
- Material comparison: Required
- Manufacturing method: Impacts material choice

## Pattern 3: The Workflow Deep-Dive Framework

**Use Case**: When users describe processes or use cases
**Goal**: Capture detailed step-by-step workflows with edge cases

### The Basic Sequence
```
User: "The technician needs to access the fuses"
Interrogator: "Walk me through exactly how the technician accesses those fuses"
User: "They open the cover and replace them"
Interrogator: "Let's start at the beginning. The technician arrives at the installation. What do they see?"
User: "A wall-mounted box with a cover"
Interrogator: "How do they know they need to service this particular box?"
User: "There's a fault indicator light"
Interrogator: "Where is that light located, and is it visible from the normal approach angle?"
User: "On the front cover, I think"
Interrogator: "What tools does the technician typically carry?"
User: "Standard electrical tools"
Interrogator: "Can you be more specific about the screwdriver types and sizes?"
User: "Phillips head screwdriver, maybe some pliers"
Interrogator: "How many screws secure the cover, and what size are they?"
User: "I haven't thought about that"
Interrogator: "Once the cover is open, how does the technician identify which fuse has failed?"
```

### Advanced Workflow Probes
- "What happens if there are cables connected when they need to open the cover?"
- "How much space does the technician need to manipulate their tools?"
- "What if the technician is left-handed?"
- "What if they're working in a cramped space or overhead?"

### Pattern Outcome
Transforms "access the fuses" into:
- Fault indication: LED on front cover
- Cover fastening: TBD (screw type and quantity)
- Tool requirements: Phillips screwdriver (size TBD)
- Fuse identification: Method required
- Working space: Clearances required

## Pattern 4: The Component Reality Check

**Use Case**: When physical components must be integrated
**Goal**: Verify all component specifications and interactions

### The Basic Sequence
```
User: "It has a relay board and a power supply"
Interrogator: "Do you have photos or datasheets for these components?"
User: "I can get them"
Interrogator: "Let's start with what you know. What are the exact part numbers?"
User: "The relay board is a generic 8-channel board from Amazon"
Interrogator: "Can you show me the specific listing you're referring to?"
User: "I'll find the link"
Interrogator: "While you're doing that, what dimensions are shown on the listing?"
User: "It says about 170mm x 80mm"
Interrogator: "Have you ordered this part yet?"
User: "Not yet"
Interrogator: "When you measure the actual part, what tolerance do you expect?"
User: "Maybe ±5mm"
Interrogator: "That's quite large. What drives that uncertainty?"
User: "Generic parts aren't always precise"
Interrogator: "How will that tolerance affect your enclosure design?"
```

### Advanced Component Validation
- "What mounting hardware comes with the component?"
- "Which direction do the connectors face?"
- "How much clearance do you need above connectors for cables?"
- "What's the power dissipation and thermal requirements?"

### Pattern Outcome
Transforms generic component into:
- Specific part identification: Required
- Measured dimensions: Required
- Mounting method: TBD
- Connector orientations: TBD
- Thermal characteristics: TBD

## Pattern 5: The Edge Case Explorer

**Use Case**: When requirements seem simple but edge cases are critical
**Goal**: Identify boundary conditions and failure modes

### The Basic Sequence
```
User: "Users just plug in a USB cable"
Interrogator: "Let's explore some scenarios. What's the longest USB cable they might use?"
User: "Probably the standard 6-foot cable"
Interrogator: "What about special installations - could they need a 10-foot cable?"
User: "Maybe in some cases"
Interrogator: "How does cable weight affect the connector?"
User: "I hadn't thought about that"
Interrogator: "What if the user plugs and unplugs frequently?"
User: "How frequently are we talking?"
Interrogator: "What if they disconnect it every day?"
User: "That seems excessive"
Interrogator: "But possible. How many insertion cycles should the connector handle?"
User: "I don't know the standard"
Interrogator: "What happens if the connector fails after 500 insertions?"
```

### Advanced Edge Case Techniques
- "What's the most extreme environment this could be used in?"
- "What if the user does exactly what they shouldn't do?"
- "How does this behave at minimum and maximum operating temperatures?"
- "What if power fails during a critical operation?"

### Pattern Outcome
Transforms "just plug in USB" into:
- Cable length range: 6-10 feet
- Cable weight impact: Analysis required
- Insertion cycle requirement: TBD (research industry standard)
- Connector reliability: Specification needed

## Pattern 6: The Cost-Benefit Interrogation

**Use Case**: When trade-offs between requirements exist
**Goal**: Establish priority and acceptable compromises

### The Basic Sequence
```
User: "It needs to be both lightweight and strong"
Interrogator: "Help me understand the trade-off. How lightweight is lightweight?"
User: "As light as possible"
Interrogator: "What's the absolute maximum weight you could tolerate?"
User: "I don't know, maybe 2 pounds?"
Interrogator: "What drives that weight limit?"
User: "Easier installation"
Interrogator: "Who performs the installation and what's their capability?"
User: "Electricians with normal strength"
Interrogator: "How does installation weight compare to what they typically handle?"
User: "They install 50-pound panels regularly"
Interrogator: "So 2 pounds seems very conservative. What strength do you need?"
User: "It can't break if dropped"
Interrogator: "From what height?"
User: "Normal handling height, maybe 3 feet"
Interrogator: "What's the cost difference between materials that achieve this?"
```

### Advanced Cost-Benefit Analysis
- "If you had to choose between light weight and low cost, which wins?"
- "What's the business impact of a 10% cost increase vs. 10% weight increase?"
- "How do customer priorities rank these requirements?"

### Pattern Outcome
Transforms competing requirements into:
- Weight target: <2 pounds (conservative)
- Strength requirement: 3-foot drop survival
- Priority ranking: TBD (cost vs. weight vs. strength)
- Material trade-offs: Analysis required

## Pattern 7: The Stakeholder Perspective Switch

**Use Case**: When requirements depend on multiple viewpoints
**Goal**: Capture different stakeholder needs and conflicts

### The Basic Sequence
```
User: "The interface should be simple"
Interrogator: "Simple from whose perspective?"
User: "The user"
Interrogator: "Who is the user in this case?"
User: "The person operating the system"
Interrogator: "Are there different types of operators with different skill levels?"
User: "Yes, some are experienced technicians, others are basic operators"
Interrogator: "How do their needs for 'simple' differ?"
User: "Experienced users want quick access to advanced features"
Interrogator: "And basic operators?"
User: "They need step-by-step guidance"
Interrogator: "Those seem like conflicting requirements. Who else has an opinion about the interface?"
User: "The maintenance team has to troubleshoot problems"
Interrogator: "What does 'simple' mean to them?"
User: "Clear status indicators and diagnostic information"
Interrogator: "How do we reconcile these different definitions of simple?"
```

### Advanced Stakeholder Analysis
- "Who pays for complexity vs. simplicity?"
- "Which stakeholder has veto power over design decisions?"
- "How do we handle conflicting stakeholder requirements?"

### Pattern Outcome
Transforms "simple interface" into:
- Operator types: Experienced vs. basic
- Feature access: Quick vs. guided
- Maintenance needs: Status and diagnostics
- Conflict resolution: Priority matrix needed

## Advanced Conversation Management

### Handling Resistance
When users resist detailed questioning:

```
User: "Can't we just start building and figure it out as we go?"
Interrogator: "I understand the urge to move quickly. Let me share why these questions matter. Last project, we discovered a critical dimension error during manufacturing that cost three weeks and $15,000 to fix. This 20-minute conversation could prevent that same disaster here."
```

### Maintaining Engagement
Keep users involved and motivated:

- **Acknowledge expertise**: "Your experience with this domain is exactly what we need"
- **Explain purpose**: "This question helps prevent [specific problem]"
- **Show progress**: "We're 60% through the critical requirements"
- **Promise payoff**: "This thoroughness will save weeks during implementation"

### Managing Information Overload
When too much information emerges:

- **Categorize in real-time**: "That's a great point about thermal management - let me capture that in our constraints section"
- **Defer appropriately**: "That's important for later phases - let me note it for follow-up"
- **Summarize frequently**: "So far we've established..."

## Conversation Pattern Success Metrics

Effective use of these patterns results in:

1. **Progressive Refinement**: Each question makes requirements more specific
2. **Assumption Surfacing**: Hidden assumptions become explicit
3. **Edge Case Discovery**: Boundary conditions are identified
4. **Stakeholder Alignment**: Different perspectives are captured and reconciled
5. **Validation Planning**: Methods for verifying requirements are established

## Anti-Patterns to Avoid

### The Interrogation Trap
- Asking questions without explaining relevance
- Making users feel defensive about their knowledge
- Pursuing perfect information on non-critical items

### The Solution Bias
- Leading questions that favor specific implementations
- Assuming technical approaches during requirements gathering
- Mixing "what" with "how" prematurely

### The Completeness Fallacy
- Trying to answer every possible question
- Getting stuck on unknowns that don't affect the design
- Analysis paralysis from over-questioning

Remember: These patterns are tools, not scripts. Adapt them to your specific context while maintaining the core principles of systematic inquiry, assumption surfacing, and precision achievement.