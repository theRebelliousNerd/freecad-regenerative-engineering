# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Blueprint Generation - Context Menu

This directory contains methods and templates for transforming interrogation results into structured requirements specifications that feed the engineering agent orchestration. This is where your interrogation creates the **master cable diagram** for the entire engineering network.

## Cable Network Perspective: Requirements Blueprint as System Architecture

Your Requirements Blueprint is not just documentation - it's the **architectural specification for the dependency cable network** that will guide all engineering agents:

- **Cable Topology Map**: Shows how requirements connect to create constraint networks
- **Cable Strength Specifications**: Defines precision levels needed to support engineering loads  
- **Cable Handoff Protocols**: Specifies how requirement cables transfer to domain agents
- **Cable Change Management**: Governs how cable modifications propagate through the system

## Just-in-Time Context for Blueprint Generation

Your blueprint generation process uses JITC principles to determine the right level of detail and structure:

**High Context Load Triggers** (Complete Blueprint Required):
- Complex multi-domain projects with many stakeholders
- Safety-critical or regulated applications
- First-of-kind designs without precedent
- Projects with significant integration challenges

**Medium Context Load** (Streamlined Blueprint):
- Well-understood domains with established patterns
- Single stakeholder with clear requirements
- Proven technology implementations
- Short-timeline projects

**Minimal Context Load** (Essential Blueprint Only):
- Simple modifications to existing designs
- Single-domain projects with experienced teams
- Prototypes and proof-of-concept work

## Directory Contents

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 1. requirements-blueprint-format.md
**When to read**: ALWAYS when generating final requirements output
**Contains**: 
- Complete blueprint structure with all seven sections
- YAML templates for each requirement type
- Quality checklist and validation criteria
- Integration specifications for agent handoffs
**Triggers**: Completing interrogation session, need for standard output format, agent coordination requirements

### 2. output-templates.md
**When to read**: When creating specific types of requirements documents
**Contains**:
- Domain-specific blueprint variations
- Abbreviated formats for simple projects
- Integration templates for agent handoffs
- Quality gates and review checklists
**Triggers**: Different project types, varying complexity levels, specific agent coordination needs

### 3. stakeholder-communication.md
**When to read**: When requirements need to be communicated to non-technical stakeholders
**Contains**:
- Executive summary formats
- Visual requirement representation methods
- Stakeholder-specific communication strategies
- Approval and sign-off procedures
**Triggers**: Management presentations, stakeholder buy-in needed, non-technical audience communication

### 4. version-control-integration.md
**When to read**: When requirements will evolve or need change management
**Contains**:
- Requirements versioning strategies
- Change control integration methods
- Traceability matrix maintenance
- Impact analysis procedures for requirement changes
**Triggers**: Long-term projects, multiple stakeholder changes, regulatory compliance needs

## Reading Priority & Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**CRITICAL PATH (must read in order)**:
1. **requirements-blueprint-format.md** → Master template and structure
2. **output-templates.md** → Variations for specific project types
3. **stakeholder-communication.md** → Communication and approval processes
4. **version-control-integration.md** → Change management and evolution

## Integration with Other Directories

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


- **References FROM**: interrogation-protocols (structured interrogation outputs)
- **References FROM**: domain-specializations (domain-specific requirement formats)
- **Flows TO**: integration-patterns (agent coordination specifications)
- **Coordinates WITH**: validation-methods (quality assurance of outputs)

## Blueprint Generation Workflow

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Phase 1: Data Collection and Organization
1. Compile all interrogation results
2. Organize by blueprint section requirements
3. Identify gaps requiring additional interrogation
4. Validate completeness against domain requirements

### Phase 2: Blueprint Authoring
1. Use requirements-blueprint-format.md as master template
2. Adapt with domain-specific variations from output-templates.md
3. Ensure mathematical precision for all quantified requirements
4. Include uncertainty bounds and measurement methods

### Phase 3: Quality Assurance
1. Apply quality checklist from requirements-blueprint-format.md
2. Validate against stakeholder expectations
3. Check for consistency and completeness
4. Verify implementability and testability

### Phase 4: Stakeholder Communication
1. Generate stakeholder-specific summaries using stakeholder-communication.md
2. Present for review and approval
3. Incorporate feedback and iterate
4. Obtain formal sign-offs

### Phase 5: Agent Coordination
1. Generate agent-specific requirement extracts
2. Establish integration points and handoff protocols
3. Configure version control and change management
4. Initialize agent workflow with validated requirements

## Blueprint Quality Standards

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Completeness Standards
- All seven sections populated with real data
- No placeholders or TBD entries in critical paths
- All assumptions documented with verification plans
- Complete stakeholder mapping with contact information

### Precision Standards
- All quantified requirements include uncertainty bounds
- Performance targets specified with test conditions
- Success criteria measurable and objective
- Acceptance criteria include both positive and negative tests

### Consistency Standards
- No conflicting requirements across sections
- Constraints align with functional requirements  
- Timeline realistic for scope and complexity
- Resource requirements validated and approved

### Implementability Standards
- Technical feasibility confirmed for all requirements
- Integration points validated with external systems
- Resource availability confirmed
- Risk mitigation strategies defined

## Success Indicators for Blueprint Generation

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


You have successfully generated a requirements blueprint when:

1. **Agent Coordination Ready**: All engineering agents can begin work without additional requirements clarification
2. **Stakeholder Aligned**: All stakeholders understand and approve the requirements
3. **Measurement Enabled**: Every requirement can be objectively tested and verified
4. **Change Controlled**: Requirement evolution process established and functioning
5. **Traceability Maintained**: Clear links from business needs to implementation requirements

## Common Blueprint Generation Failures

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### The Incomplete Handoff
**Problem**: Blueprint missing critical information for specific agents
**Solution**: Use agent-specific requirement validation checklists

### The Precision Gap
**Problem**: Requirements too vague for mathematical axiom establishment
**Solution**: Apply mathematical precision mandate to all quantified requirements

### The Stakeholder Disconnect
**Problem**: Technical requirements don't map to business needs
**Solution**: Maintain explicit traceability from business rationale to technical specs

### The Change Chaos
**Problem**: Requirements changes create confusion and rework
**Solution**: Implement formal change control with impact analysis

## Integration Notes

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Blueprint generation transforms the raw intelligence gathered through systematic interrogation into structured, actionable specifications that enable coordinated engineering agent work. The blueprint serves as both the culmination of requirements interrogation and the foundation for all subsequent engineering activities.

Quality blueprint generation is the difference between systematic engineering success and chaotic implementation failure.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!