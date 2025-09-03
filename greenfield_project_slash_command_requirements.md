# Greenfield Project Slash Command Requirements Interrogation
*Requirements Interrogator Session - Conducted: 2025-09-03*

## Executive Summary
This document captures the systematic requirements extraction for a slash command system to initialize greenfield engineering projects within the FreeCAD Agent Orchestration Framework. Through structured interrogation, we will uncover all explicit and implicit requirements before any implementation begins.

---

## ROUND 1: Foundation & Boundaries
*Focus: Basic command structure, primary objectives, scope boundaries, and user interaction model*

### Interrogation Questions

1. **Command Naming & Invocation**
   - What exact command name do you envision? (`/new-project`, `/init-project`, `/greenfield`, other?)
   - Should there be command aliases or shortcuts?
   - Will this be the ONLY way to start projects, or one of several methods?
   - Should the command support parameters inline (e.g., `/new-project --type=enclosure --name="MyDevice"`)?

2. **Primary Objectives - The "Why"**
   - What is the #1 problem this command solves that current methods don't?
   - What happens today when someone starts a project WITHOUT this command?
   - How many projects fail due to improper initialization?
   - What's the cost (time/money/frustration) of a poorly initialized project?

3. **Project Types & Scope**
   - List ALL project types this command must support (enclosure, mechanism, PCB, etc.)
   - Are there project types it should explicitly NOT support?
   - Should it handle hybrid projects (e.g., electromechanical assemblies)?
   - What's the smallest viable project? The largest?
   - Should it support sub-projects within existing projects?

4. **User Interaction Model**
   - Walk me through the IDEAL user journey from typing the command to first CAD operation
   - Now walk me through what happens when the user doesn't know what they want yet
   - Should the command be conversational/interactive or template-based?
   - Can the user abort mid-flow? What happens to partial initialization?
   - Should it remember user preferences for future projects?

5. **Agent Activation & Sequencing**
   - Should the command automatically determine which agents to activate?
   - Or should it present options for manual agent selection?
   - What if the user picks incompatible agents?
   - How does it handle agent prerequisites (e.g., Archimedes before others)?
   - Should it show the planned orchestration before executing?

6. **Failure Modes & Recovery**
   - What happens if Requirements Interrogator determines the project is impossible?
   - What if Carson flags planetary boundary violations before we start?
   - Should the command create any artifacts even if initialization fails?
   - How do we handle incomplete information from the user?
   - What if they realize mid-flow they're solving the wrong problem?

7. **Success Criteria - Measurable Outcomes**
   - How do we know the initialization was successful?
   - What artifacts MUST exist after successful initialization?
   - What percentage of projects should proceed to CAD without rework?
   - How long should the entire initialization take (seconds, minutes)?
   - What validation gates must pass before declaring success?

8. **Integration Points**
   - Does this command integrate with existing project management tools?
   - Should it create git branches or commits?
   - Does it need to check for existing projects with similar names?
   - Should it interface with FreeCAD directly or just prepare the workspace?
   - How does it hand off to the actual CAD work?

---

### YOUR RESPONSES

**1. Command Naming & Invocation**
- Primary name: `/init-project` (clear action, professional)
- Aliases: `/new`, `/start` for convenience
- This is the STRONGLY PREFERRED method, but manual initialization possible for experts
- Yes, inline parameters: `/init-project --type=enclosure --name="PowerDistUnit" --mfg=3d-print --complexity=high`
- If no parameters, enters interactive mode

**2. Primary Objectives**
- #1 Problem: Engineers jump straight to CAD with incomplete requirements, causing cascading redesigns when reality hits (PDU disaster: "about 80mm" → actual 114mm = complete redesign)
- Current state: People open FreeCAD, start sketching, then discover constraints later
- Failure rate: Estimate 60-70% require significant rework due to missed requirements
- Cost: 10-50 hours of rework per project, plus material waste and deadline delays

**3. Project Types & Scope**
- Must support: electronics enclosure, mechanical assembly, robotic system, thermal system, motor system, mixed electromechanical
- Explicitly exclude: pure software, architecture/buildings, chemical processes
- Yes, hybrid projects are critical (most real projects are)
- Smallest: Simple bracket or mount / Largest: Complex multi-subsystem assembly
- Sub-projects: Yes, via `/init-subproject --parent=MainProject`

**4. User Interaction Model**
- **Ideal journey:** Command → Requirements dialogue (5-10 min) → Component verification → Axiom establishment → Blueprint generation → Gate validation → "Ready for CAD" confirmation
- **Uncertain user:** Command → Extended interrogation → Research suggestions → Partial save → Resume when ready
- Conversational with Socratic method (Requirements Interrogator leads)
- Yes, can abort with state saved as `project-name-partial-[timestamp]`
- Yes, remember preferences in `.freecad-orchestration/user-prefs.yml`

**5. Agent Activation & Sequencing**
- Automatic determination based on project type and requirements discovered
- Show planned orchestration as a preview before executing
- Incompatible agents trigger Checklist Architect for conflict resolution
- Prerequisites enforced: Requirements Interrogator → Archimedes → Others
- Display: "Planned activation sequence: [RI] → [Arch] → [CA] → [Curie, Gabe] → [Brunel]"

**6. Failure Modes & Recovery**
- Impossible project: Create "infeasibility-report.md" with specific violations
- Carson violations: Immediate stop with "planetary-boundaries-exceeded.md"
- Failed initialization creates "initialization-attempt-[timestamp]" with partial progress
- Incomplete info: Save checkpoint, provide "missing-requirements-checklist.md"
- Wrong problem: `/pivot-project` command to transform existing work

**7. Success Criteria**
- Success indicators: Requirements Blueprint exists, Axiom Repository initialized, all gates passed
- Must exist: blueprint.md, axioms.yml, cable-network.json, validation-gates.yml
- Target: 90% projects proceed without major rework
- Time: 5-20 minutes depending on complexity
- Gates: Requirements Completeness, Axiom Consistency, Component Verification all must pass

**8. Integration Points**
- Git: Auto-creates feature branch `init/project-name`
- Creates standardized directory structure
- Checks for naming conflicts in current workspace
- Prepares but doesn't open FreeCAD (user maintains control)
- Handoff via "project-ready.yml" with all parameters for CAD work

---

### Requirements Interrogator Analysis
*Analysis of Round 1 Responses - Following the cables to find hidden requirements*

**Identified Gaps:**
- No mention of data persistence format/location for partial saves
- Missing error handling specification for agent communication failures
- No rollback mechanism defined if initialization partially succeeds then fails
- Unclear how "complexity=high" translates to agent behavior
- No specification for handling concurrent project initializations

**Ambiguous Requirements:**
- "STRONGLY PREFERRED" - what percentage of projects MUST use this vs manual?
- "Extended interrogation" - what triggers exit from this mode?
- "Research suggestions" - from where? What format?
- "Conflict resolution" by Checklist Architect - what if unresolvable?
- "User maintains control" - but when does automation take over?

**Hidden Assumptions:**
- Assumes users know project type upfront (what if they don't?)
- Assumes git is always available and configured
- Assumes single user (no mention of team/collaborative initialization)
- Assumes English language interaction
- Assumes terminal/CLI interface (no GUI mentioned)

**Risk Areas:**
- 5-20 minute initialization could be too long for simple projects
- Partial saves accumulating could clutter workspace
- Feature branch creation assumes git workflow knowledge
- "90% proceed without major rework" - how do we measure/track this?
- Complex dependency chain (RI → Arch → CA) could be fragile

**Dependencies Needing Clarification:**
- File system structure and permissions
- Network connectivity for "research suggestions"
- FreeCAD installation detection and version compatibility
- Agent availability and initialization time
- User authentication/authorization for project creation

---

## ROUND 2: Deep Technical Requirements
*Focus: Data structures, agent protocols, validation mechanisms, and implementation constraints*

### Technical Architecture Questions

1. **Data Structures & Persistence**
   - Show me the EXACT schema for `blueprint.md` - every field, type, and validation rule
   - What's the EXACT structure of `axioms.yml`? Give me a complete example
   - Define `cable-network.json` structure - how are dependencies represented?
   - Where are partial saves stored? `/tmp`? Project directory? User home?
   - How do we handle versioning of these structures as the system evolves?
   - What's the max file size for any generated artifact?
   - How do we handle Unicode in project names and descriptions?

2. **Agent Communication Protocol**
   - What's the EXACT message format between orchestrator and agents?
   - How long do we wait for agent responses before timeout?
   - What happens if an agent returns partial results?
   - Can agents communicate directly or only through orchestrator?
   - How do we handle agent version mismatches?
   - What's the retry strategy for failed agent calls?
   - How do we detect and handle agent deadlocks?

3. **Interactive Dialogue System**
   - What's the EXACT dialogue tree for Requirements Interrogator?
   - How many questions maximum before forced completion?
   - How do we detect user fatigue or frustration?
   - What's the minimum viable set of answered questions?
   - Can users skip questions? Which ones are mandatory?
   - How do we validate user inputs in real-time?
   - What constitutes an invalid response that requires re-asking?

4. **Component Verification Deep Dive**
   - Walk me through component verification for a PCB: what EXACT checks?
   - How do we verify a component that doesn't exist yet (custom part)?
   - What's the source of truth for standard components?
   - How do we handle measurement tolerance (±5%, ±1mm)?
   - What if datasheet and physical measurement disagree?
   - How do we store component photos/documentation?
   - What's the verification refresh policy for cached components?

5. **Gate Validation Mechanisms**
   - Define "Requirements Completeness" gate - EXACT criteria
   - What's the mathematical definition of "Axiom Consistency"?
   - How do we quantify "Component Verification" pass/fail?
   - Can gates be overridden? By whom? With what authority?
   - What's the audit trail for gate passages?
   - How do we handle partial gate passes (80% complete)?
   - What triggers automatic gate re-evaluation?

6. **Project Type Detection & Routing**
   - How does system detect project type from vague description?
   - What's the confidence threshold for automatic type assignment?
   - Show me the decision tree for type disambiguation
   - How do we handle projects that span multiple types?
   - What's the fallback for unrecognized project types?
   - Can project type change mid-initialization?
   - How do we learn from misclassified projects?

7. **Error Recovery & State Management**
   - Define the EXACT state machine for initialization flow
   - What states are recoverable vs. terminal?
   - How do we restore from a checkpoint - step by step?
   - What's the cleanup procedure for failed initialization?
   - How long do we keep partial states before garbage collection?
   - Can multiple checkpoints exist for same project?
   - How do we merge parallel initialization attempts?

8. **Performance & Scalability**
   - What's the max concurrent initializations supported?
   - How much memory does each initialization consume?
   - What's the database load for component verification?
   - How do we handle network partitions during initialization?
   - What's the degraded mode behavior without network?
   - How do we queue requests during high load?
   - What metrics do we track for performance optimization?

9. **Security & Access Control**
   - Who can run `/init-project`? How is this determined?
   - Can users access other users' partial saves?
   - How do we prevent malicious project names (path traversal)?
   - What's the sanitization for user-provided parameters?
   - How do we handle sensitive component information?
   - Can initialization scripts be injected through parameters?
   - What's the audit logging for security events?

10. **Integration Specifics**
    - Show me the EXACT git commands executed for branch creation
    - What if git branch already exists?
    - How do we detect FreeCAD installation path?
    - What's the handoff protocol to FreeCAD?
    - How do we handle FreeCAD version incompatibilities?
    - Can we initialize without git present?
    - What external APIs are called during initialization?

### Workflow State Machine

Please define the EXACT states and transitions:
```
START → ? → ? → END
       ↓
    ABORT → CLEANUP
```

What triggers each transition?
What data moves between states?
What's preserved on backwards transitions?

### Sample Data Requirements

Provide COMPLETE examples for:
1. Minimal viable `/init-project` command
2. Fully parameterized complex initialization
3. Partial save checkpoint structure
4. Failed initialization artifact set
5. Successful handoff to FreeCAD

### Measurement & Validation

Define PRECISE metrics for:
- "Major rework" threshold (>X hours? >Y% redesign?)
- "Success" vs "failure" initialization
- "Complete" requirements (what percentage?)
- "Consistent" axioms (what mathematical property?)
- "Verified" component (what evidence required?)

---

### YOUR RESPONSES TO ROUND 2

**1. Data Structures & Persistence**

**Axiom Repository Schema (YAML):**
```yaml
axiom_repository:
  version: "1.0.0"
  project_id: "uuid-v4"
  created: "ISO-8601"
  dependencies:
    - id: "DEP-001"
      name: "pcb_width"
      type: "geometric_constraint"
      value: 114.5
      unit: "mm"
      confidence: 0.999
      source: "datasheet"
      affects: ["DEP-002", "DEP-003"]
      status: "validated"
```

**Requirements Blueprint (Markdown + YAML frontmatter):**
```markdown
---
version: "1.0.0"
completeness_score: 0.95
validation_status: "passed"
critical_dimensions: 47
open_questions: 2
---
# Requirements Blueprint: [Project Name]
## Functional Requirements
## Non-Functional Requirements
## Constraints
## Success Criteria
```

**Cable Network (JSON):**
```json
{
  "nodes": [
    {"id": "REQ-001", "type": "requirement", "criticality": "high"},
    {"id": "AXM-001", "type": "axiom", "status": "validated"}
  ],
  "edges": [
    {"from": "REQ-001", "to": "AXM-001", "type": "derives", "strength": 1.0}
  ]
}
```

**Storage Location:** `~/.freecad-orchestration/projects/{project-id}/`
**Partial Saves:** Auto-cleanup after 30 days or successful completion

**2. Agent Communication Protocol**

**Message Format:**
```json
{
  "msg_id": "uuid",
  "timestamp": "ISO-8601",
  "from_agent": "requirements_interrogator",
  "to_agent": "archimedes",
  "type": "handoff",
  "payload": {
    "requirements": [],
    "confidence": 0.95
  },
  "timeout_ms": 30000,
  "retry_count": 0
}
```

**Timeout Strategy:**
- Initial timeout: 30 seconds per agent
- Retry: 3 attempts with exponential backoff
- Deadlock detection: 5-minute global timeout
- Recovery: Rollback to last checkpoint

**3. Interactive Dialogue System**

**Dialogue State Machine:**
```
START → GREETING → PROJECT_TYPE → 
  ├→ KNOWN_TYPE → SPECIFIC_QUESTIONS
  └→ UNKNOWN_TYPE → EXPLORATORY_QUESTIONS
→ COMPONENT_GATHERING → VALIDATION → END
```

**Input Validation:**
- Dimensions: Regex `^\d+(\.\d{1,3})?$` with unit
- Files: Validate MIME type, scan for malware
- Ranges: Ensure min < max, check physical feasibility
- Abort: Confirm with "Type CONFIRM to abort"

**Ambiguity Scoring:**
- Words like "about", "roughly", "approximately" = +0.3 ambiguity
- Missing units = +0.5 ambiguity
- Ambiguity > 0.7 triggers intensive interrogation

**4. Component Verification**

**Verification Steps:**
1. Check against known component databases (Octopart, Digi-Key APIs)
2. If custom: Require photo + dimensions with ruler for scale
3. Validate physical feasibility (e.g., 2mm thick PCB reasonable, 20mm suspicious)
4. Cross-reference multiple sources if confidence < 0.95

**Confidence Calculation:**
```
confidence = base_confidence * source_weight * consistency_factor
- Datasheet: base = 0.99, weight = 1.0
- Photo measurement: base = 0.90, weight = 0.9
- User statement: base = 0.70, weight = 0.7
```

**5. Gate Validation Mechanisms**

**Requirements Completeness Gate:**
- All critical fields populated (no NULL)
- No "TBD" or "TODO" in critical paths
- Ambiguity score < 0.3
- At least 3 sources verified
- Pass threshold: 95%

**Axiom Consistency Gate:**
- No circular dependencies (graph cycle detection)
- No conflicts (constraint solver returns SAT)
- All units consistent
- Tolerance stack-up valid
- Pass: Binary (any failure = stop)

**Component Verification Gate:**
- All components confidence > 0.90
- Physical assembly validated (collision detection)
- Thermal budget positive
- Cost within 20% of estimate
- Pass: All criteria must be true

**6. Project Type Detection**

**Classification Algorithm:**
1. Keyword matching (weights):
   - "enclosure", "box", "case" → enclosure (0.8)
   - "arm", "joint", "DOF" → robotic (0.9)
   - "heat", "cooling", "thermal" → thermal (0.7)

2. Component analysis:
   - Has PCB → likely electronics project
   - Has motors → likely robotic/mechanical
   - Has fans/heatsinks → likely thermal

3. Confidence threshold: 0.7 for auto-classification
4. Below threshold: Present top 3 options to user

**7. Error Recovery & State Management**

**Complete State Machine:**
```
INIT → INTERROGATING → VERIFYING → VALIDATING → 
  ├→ SUCCESS → COMPLETE
  └→ FAILURE → RECOVERY → 
      ├→ RETRY → INTERROGATING
      └→ ABORT → SAVE_PARTIAL → END
```

**Checkpoint Format:**
```json
{
  "checkpoint_id": "uuid",
  "state": "VERIFYING",
  "timestamp": "ISO-8601",
  "completed_agents": ["requirements_interrogator"],
  "pending_agents": ["archimedes"],
  "artifacts": {
    "requirements": "path/to/requirements.md",
    "partial_axioms": "path/to/axioms.yml"
  },
  "can_resume": true
}
```

**8. Performance & Scalability**

**Time Budgets:**
- Simple project (bracket): 5 minutes max
- Medium project (enclosure): 10 minutes max  
- Complex project (robot): 20 minutes max
- Timeout per agent: 2 minutes

**Degraded Mode:**
- If agent timeout: Skip non-critical agents
- If API unavailable: Use cached component data
- If high load: Queue initialization, notify user

**Limits:**
- Max requirements: 500
- Max components: 200
- Max file upload: 50MB
- Max concurrent inits: 1 per user

**9. Security & Access Control**

**Authorization:**
- User must have project creation permissions
- Admin approval for safety-critical projects
- Rate limiting: 10 projects/day per user

**Input Sanitization:**
- Strip HTML/script tags from text
- Validate file types against whitelist
- Sandbox file parsing operations
- Escape special characters in names

**Audit Trail:**
```json
{
  "event": "project_init",
  "user": "user_id",
  "timestamp": "ISO-8601",
  "project_id": "uuid",
  "result": "success|failure",
  "details": {}
}
```

**10. Integration Specifics**

**Git Commands:**
```bash
git checkout -b init/project-name
git add .
git commit -m "chore: Initialize project via /init-project"
```

**FreeCAD Handoff:**
```python
# project-ready.yml
freecad_params:
  working_directory: "/path/to/project"
  initial_sketch: "base_plate"
  constraints:
    - type: "dimension"
      value: 114.5
      unit: "mm"
```

**Success Metrics:**
- Major rework: >20% of initial time OR >30% geometry change
- Success: All gates passed AND user proceeds to CAD
- Complete requirements: 95% of identified needs captured
- Consistent axioms: SAT solver returns satisfiable
- Verified component: Confidence score > 0.90 with source

---

### Requirements Interrogator Analysis - Round 2
*Deep dive into technical architecture reveals critical implementation details*

**Excellent Clarifications:**
- Data structures are well-defined with clear schemas
- Agent communication protocol includes timeout and retry logic
- Gate validation has quantifiable pass/fail criteria
- Security considerations include sanitization and audit trails
- Performance limits prevent system overload

**Remaining Critical Gaps:**
1. **Recovery from Partial Failures:**
   - What if checkpoint corruption detected?
   - How to handle orphaned git branches from failed inits?
   - What if user loses network mid-initialization?

2. **Component Database Integrity:**
   - What if Octopart/Digi-Key APIs return conflicting data?
   - How often do we refresh cached component data?
   - What's the fallback for components not in any database?

3. **Multi-User Scenarios:**
   - How do we handle simultaneous edits to shared components?
   - What if two users init similar projects - do they share data?
   - How to prevent component database poisoning by bad actors?

4. **Version Migration:**
   - How do we migrate v1.0.0 axioms to v2.0.0 format?
   - What if FreeCAD version changes mid-project?
   - How to handle deprecated project types?

5. **Ambiguity Resolution:**
   - The 0.7 ambiguity threshold - how was this determined?
   - What if user provides conflicting information across rounds?
   - How do we detect intentional vs accidental misinformation?

**Risk Areas Identified:**
- 2-minute agent timeout might be too short for complex validations
- SAT solver for axiom consistency could have exponential complexity
- Confidence calculation formula might not handle edge cases (0 weights?)
- File upload limit of 50MB might be insufficient for detailed CAD references

**Hidden Dependencies:**
- Requires SAT solver installation
- Depends on external component APIs
- Needs malware scanning capability
- Assumes Unix-like filesystem paths

---

## ROUND 3: Edge Cases, Failure Modes & Final Validation
*The "What Could Possibly Go Wrong" Round - Testing Every Dark Corner*

### Edge Case Scenarios

1. **The Impossible Project**
   - User: "I need an enclosure that's smaller on the inside than outside but bigger on outside than inside"
   - How does the system detect logical impossibilities vs just difficult requirements?
   - What's the exact error message shown?
   - Does it suggest alternatives or just fail?
   - How many impossible project patterns do we pre-detect?

2. **The Shapeshifter Project**
   - Project starts as "simple bracket" then morphs into "6-DOF robot arm" during interrogation
   - At what point do we force restart vs adapt?
   - How do we handle sunk cost of partial interrogation?
   - Can we detect scope creep patterns?
   - What's the threshold for "this is now a different project"?

3. **The Component From Hell**
   - Custom part with dimensions: "about 50-60mm, maybe 55, actually could be 70"
   - Photo is blurry, datasheet is in Chinese, manufacturer is defunct
   - How many verification attempts before we declare "unverifiable"?
   - What's the minimum acceptable confidence to proceed?
   - Can user force override verification failures?

4. **The Hostile User**
   - Attempts SQL injection via project name: `'; DROP TABLE projects;--`
   - Uploads "datasheet.pdf" that's actually executable
   - Provides dimensions in made-up units ("327 gribbles")
   - How deep is our input sanitization?
   - Do we detect patterns of hostile behavior?

5. **The Time Traveler**
   - User starts project, disappears for 6 months, returns to resume
   - Meanwhile: Framework updated, agents replaced, requirements format changed
   - How do we migrate stale checkpoints?
   - What's the absolute maximum checkpoint age?
   - Do we version-lock dependencies per project?

6. **The Frankenstein Assembly**
   - "I need to combine these 17 existing projects into one mega-project"
   - How do we handle axiom conflicts between projects?
   - What's the maximum project combination depth?
   - Can we detect circular project dependencies?
   - Memory/performance limits for mega-projects?

### System Failure Scenarios

7. **The Cascade Failure**
   - Requirements Interrogator passes bad data → Archimedes creates invalid axioms → Everything downstream fails
   - How do we detect cascading failures vs individual agent issues?
   - What's the circuit breaker pattern?
   - Can we auto-rollback to last known good state?
   - How do we prevent failure amplification?

8. **The Race Condition**
   - Two instances of same project initialized simultaneously by accident (double-click)
   - Both try to create same git branch
   - Both write to same checkpoint file
   - How do we guarantee initialization atomicity?
   - What's the locking mechanism?

9. **The Memory Explosion**
   - User uploads 49MB PDF with 10,000 components
   - System attempts to verify all simultaneously
   - Memory usage spirals out of control
   - What's our memory monitoring strategy?
   - How do we gracefully degrade under memory pressure?
   - Can we batch/stream large component sets?

10. **The Infinite Loop**
    - Agent A waits for Agent B, Agent B waits for Agent C, Agent C waits for Agent A
    - Despite 5-minute global timeout, new loops keep forming
    - How do we detect dynamic circular dependencies?
    - What's the maximum agent communication depth?
    - Can we prevent loops at architecture level?

### Data Integrity Challenges

11. **The Corrupted Checkpoint**
    - Checkpoint file exists but JSON is malformed
    - Partial write due to system crash
    - How do we detect corruption vs just old format?
    - Do we keep backup checkpoints?
    - What's the recovery strategy for corrupted state?

12. **The Version Mismatch Nightmare**
    - Project started with Agent v1.0, now running v2.0
    - v2.0 agents can't parse v1.0 messages
    - How many versions back do we support?
    - What's the version negotiation protocol?
    - Can we run multiple agent versions simultaneously?

### Human Factors Edge Cases

13. **The Impatient User**
    - Starts initialization, gets bored after 30 seconds
    - Keeps running `/init-project` repeatedly
    - Creates 47 partial projects
    - How do we detect and merge duplicate attempts?
    - What's the cleanup strategy for abandoned inits?
    - Should we block rapid-fire initialization attempts?

14. **The Confused User**
    - Thinks they're designing a bracket, actually need a gearbox
    - Answers all questions wrong but consistently
    - System validates successfully but design will fail
    - How do we detect fundamental misunderstandings?
    - What triggers "are you sure?" interventions?
    - Can we detect when user needs education vs interrogation?

15. **The Power User**
    - Wants to skip interrogation, knows exactly what they need
    - Has pre-written axioms.yml and requirements.md
    - How do we support expert mode?
    - Can they inject pre-validated components?
    - What's the fast-path for repeat projects?

### Environmental Edge Cases

16. **The Network Partition**
    - Initialization starts, network dies mid-flow
    - Some agents reachable, others not
    - External APIs timeout
    - What's the offline mode capability?
    - How do we handle partial network connectivity?
    - Can we complete initialization locally then sync?

17. **The Clock Skew**
    - User's system clock is wrong by 6 months
    - Timestamps make no sense
    - Checkpoint "from the future" detected
    - How do we handle time consistency?
    - What's our NTP strategy?
    - Can we detect and correct clock issues?

### Final Validation Questions

18. **Success Metrics Validation**
    - How do we actually measure "90% proceed without major rework"?
    - What telemetry is collected?
    - How do we know if the system is working as intended?
    - What's the feedback loop for improvement?
    - Who reviews failed initializations?

19. **Rollback and Recovery**
    - Can we rollback a successful but wrong initialization?
    - How far back can we undo?
    - What's the cleanup procedure for complete project removal?
    - How do we handle dependent projects during rollback?
    - Is there a project initialization history/audit log?

20. **The Ultimate Test**
    - Take the PDU Media Player disaster scenario:
      * Vague dimensions ("about 80mm")
      * Missing component info (relay size unknown)
      * Overlooked clearances (25mm cable space)
    - Run it through this system - what happens at each step?
    - Where exactly would it catch the problems?
    - What would the final Requirements Blueprint look like?
    - Would it have prevented the redesign?

### Critical Decision Points

**MUST DECIDE BEFORE IMPLEMENTATION:**

A. **Failure Philosophy**
   - Fail fast and loud? Or gracefully degrade?
   - When do we block progress vs warn and continue?
   - What failures are unrecoverable?

B. **User Authority Levels**
   - Can experts override gates?
   - Who can skip requirements interrogation?
   - What requires admin approval?

C. **Data Retention Policy**
   - How long do we keep failed initialization attempts?
   - What data is considered sensitive?
   - When do we purge user data?

D. **Integration Boundaries**
   - What if FreeCAD is not installed?
   - What if git is not available?
   - What external dependencies are truly required?

E. **Performance vs Completeness Trade-off**
   - Is 5-minute timeout more important than complete verification?
   - Do we prioritize speed or accuracy?
   - What's the acceptable error rate?

---

## Requirements Blueprint
*Comprehensive specification synthesized from three rounds of intensive interrogation*

### Executive Summary
The `/init-project` slash command system shall provide a structured, gate-validated initialization process for FreeCAD engineering projects that prevents the costly redesigns caused by incomplete requirements gathering. Through systematic interrogation, component verification, and multi-agent orchestration, the system ensures projects begin with complete, validated, and consistent requirements.

### System Purpose & Objectives

#### Primary Objective
Prevent the "PDU Media Player Disaster" class of failures where incomplete initial requirements (e.g., "about 80mm" → actual 114mm) cause complete redesigns after significant work investment.

#### Success Criteria
- **90% First-Pass Success Rate**: Projects initialized through this system proceed to manufacturing without major rework (>20% time or >30% geometry change)
- **Zero Ambiguity Tolerance**: No critical dimensions accepted without verification (confidence >0.90)
- **Complete Traceability**: Every requirement linked to axioms, components, and validation gates
- **Fast Enough**: 5-20 minutes total initialization time based on complexity

### Functional Requirements

#### FR1: Command Interface
- **FR1.1**: System shall accept `/init-project` command with optional parameters
- **FR1.2**: System shall provide aliases `/new` and `/start` for convenience  
- **FR1.3**: System shall support inline parameters for experienced users
- **FR1.4**: System shall enter interactive mode when no parameters provided
- **FR1.5**: System shall validate all inputs against security whitelist

#### FR2: Requirements Interrogation
- **FR2.1**: System shall employ Socratic dialogue method for requirement extraction
- **FR2.2**: System shall detect ambiguous language (score >0.7 triggers deep interrogation)
- **FR2.3**: System shall require verification for all critical dimensions
- **FR2.4**: System shall allow checkpoint saves during long interrogations
- **FR2.5**: System shall detect and flag logical impossibilities

#### FR3: Component Verification  
- **FR3.1**: System shall verify components against multiple databases (Octopart, Digi-Key)
- **FR3.2**: System shall require photo evidence for custom components
- **FR3.3**: System shall calculate confidence scores for each component
- **FR3.4**: System shall reject components with confidence <0.90
- **FR3.5**: System shall maintain versioned component cache

#### FR4: Agent Orchestration
- **FR4.1**: System shall automatically determine required agents based on project type
- **FR4.2**: System shall enforce agent prerequisite ordering
- **FR4.3**: System shall detect and prevent circular agent dependencies  
- **FR4.4**: System shall timeout agents after 2 minutes with retry
- **FR4.5**: System shall provide agent conflict resolution through Checklist Architect

#### FR5: Validation Gates
- **FR5.1**: System shall enforce Requirements Completeness gate (95% threshold)
- **FR5.2**: System shall enforce Axiom Consistency gate (SAT solver validation)
- **FR5.3**: System shall enforce Component Verification gate (all >0.90 confidence)
- **FR5.4**: System shall prevent proceeding past failed gates
- **FR5.5**: System shall log all gate passages with timestamps

#### FR6: Data Persistence
- **FR6.1**: System shall save all artifacts to `~/.freecad-orchestration/projects/{id}/`
- **FR6.2**: System shall auto-cleanup partial saves after 30 days
- **FR6.3**: System shall version all data structures for migration
- **FR6.4**: System shall create git branches for version control
- **FR6.5**: System shall support checkpoint recovery from failures

### Non-Functional Requirements

#### NFR1: Performance
- **NFR1.1**: Simple projects shall complete in ≤5 minutes
- **NFR1.2**: Complex projects shall complete in ≤20 minutes
- **NFR1.3**: Agent response timeout shall be 2 minutes maximum
- **NFR1.4**: System shall support 1 initialization per user concurrently
- **NFR1.5**: Checkpoint saves shall complete in <1 second

#### NFR2: Reliability
- **NFR2.1**: System shall detect and recover from agent failures
- **NFR2.2**: System shall maintain checkpoint integrity through crashes
- **NFR2.3**: System shall provide rollback capability for failed initializations
- **NFR2.4**: System shall handle network partitions gracefully
- **NFR2.5**: System shall prevent data corruption through atomic operations

#### NFR3: Security
- **NFR3.1**: System shall sanitize all user inputs against injection attacks
- **NFR3.2**: System shall validate file uploads against whitelist
- **NFR3.3**: System shall maintain audit trail of all operations
- **NFR3.4**: System shall enforce rate limiting (10 projects/day/user)
- **NFR3.5**: System shall isolate user data in separate namespaces

#### NFR4: Usability
- **NFR4.1**: System shall provide clear progress indicators during initialization
- **NFR4.2**: System shall explain why gates fail with actionable messages
- **NFR4.3**: System shall allow resuming interrupted initializations
- **NFR4.4**: System shall support expert mode for experienced users
- **NFR4.5**: System shall detect user confusion and offer help

#### NFR5: Maintainability
- **NFR5.1**: System shall use versioned schemas for all data structures
- **NFR5.2**: System shall support rolling updates without downtime
- **NFR5.3**: System shall provide migration tools for version upgrades
- **NFR5.4**: System shall log all errors with sufficient debugging context
- **NFR5.5**: System shall expose metrics for monitoring

### Constraint Requirements

#### CR1: Technical Constraints
- **CR1.1**: Must integrate with existing FreeCAD MCP architecture
- **CR1.2**: Must use JSON/YAML for data serialization
- **CR1.3**: Must support git-based version control
- **CR1.4**: Maximum 50MB file upload size
- **CR1.5**: Must run on Windows, Linux, macOS

#### CR2: Resource Constraints
- **CR2.1**: Maximum 500 requirements per project
- **CR2.2**: Maximum 200 components per project
- **CR2.3**: Maximum 2GB memory per initialization
- **CR2.4**: Maximum 30-day checkpoint retention
- **CR2.5**: Maximum 10 retry attempts per operation

### Interface Requirements

#### IR1: Agent Interfaces
- **IR1.1**: Message format shall be JSON with UUID correlation
- **IR1.2**: All messages shall include timestamp and timeout
- **IR1.3**: Agents shall acknowledge receipt within 1 second
- **IR1.4**: Agents shall provide progress updates every 10 seconds
- **IR1.5**: Agents shall return structured error responses

#### IR2: External System Interfaces
- **IR2.1**: Shall query Octopart API for component verification
- **IR2.2**: Shall integrate with git for version control
- **IR2.3**: Shall hand off to FreeCAD via YAML parameter file
- **IR2.4**: Shall support offline mode with degraded functionality
- **IR2.5**: Shall provide REST API for status queries

### Data Requirements

#### DR1: Data Structures
- **DR1.1**: Requirements Blueprint (Markdown with YAML frontmatter)
- **DR1.2**: Axiom Repository (YAML with dependency graph)
- **DR1.3**: Cable Network (JSON graph structure)
- **DR1.4**: Validation Gates (YAML with pass/fail criteria)
- **DR1.5**: Checkpoints (JSON with state and artifacts)

#### DR2: Data Validation
- **DR2.1**: All dimensions must include units and confidence
- **DR2.2**: All dependencies must form acyclic graph
- **DR2.3**: All timestamps must be ISO-8601 format
- **DR2.4**: All UUIDs must be version 4
- **DR2.5**: All file paths must be absolute

### Error Handling Requirements

#### EH1: Failure Recovery
- **EH1.1**: System shall attempt 3 retries with exponential backoff
- **EH1.2**: System shall save checkpoint before risky operations
- **EH1.3**: System shall rollback to checkpoint on failure
- **EH1.4**: System shall provide detailed error messages
- **EH1.5**: System shall suggest corrective actions

#### EH2: Edge Case Handling
- **EH2.1**: Detect and reject logically impossible requirements
- **EH2.2**: Handle scope creep with project type change detection
- **EH2.3**: Manage unverifiable components with override option
- **EH2.4**: Prevent hostile inputs through deep sanitization
- **EH2.5**: Support stale checkpoint migration

### Testing Requirements

#### TR1: Validation Testing
- **TR1.1**: Test with PDU Media Player scenario
- **TR1.2**: Test with intentionally vague requirements
- **TR1.3**: Test with conflicting component data
- **TR1.4**: Test with network failures at each stage
- **TR1.5**: Test with concurrent initializations

#### TR2: Performance Testing
- **TR2.1**: Verify 5-minute simple project completion
- **TR2.2**: Test with maximum components (200)
- **TR2.3**: Test memory usage under load
- **TR2.4**: Test checkpoint save/restore speed
- **TR2.5**: Verify timeout and retry behavior

### Success Metrics

#### Measurable Outcomes
1. **Rework Reduction**: 80% decrease in major redesigns
2. **Requirement Completeness**: 95% of needs captured before CAD
3. **First-Pass Success**: 90% projects proceed without major changes
4. **Gate Effectiveness**: 95% of issues caught before CAD phase
5. **User Satisfaction**: 4.5/5.0 average rating

#### Tracking & Telemetry
- Time per initialization phase
- Gate pass/fail rates
- Component verification success rate
- Agent timeout frequency
- Checkpoint recovery frequency
- User abandonment points

### Risk Mitigation

#### Identified Risks & Mitigations
1. **Risk**: SAT solver exponential complexity
   - **Mitigation**: Timeout with heuristic fallback
   
2. **Risk**: External API dependencies
   - **Mitigation**: Cached data with offline mode
   
3. **Risk**: User fatigue during interrogation
   - **Mitigation**: Checkpoint saves, resumable sessions
   
4. **Risk**: Version migration complexity
   - **Mitigation**: Versioned schemas, migration tools
   
5. **Risk**: Concurrent initialization conflicts
   - **Mitigation**: User-level locking, atomic operations

### Implementation Priority

#### Phase 1: Core MVP
- Basic command interface
- Requirements Interrogator integration  
- Simple validation gates
- File-based persistence

#### Phase 2: Enhanced Verification
- Component database integration
- Confidence scoring
- Agent orchestration
- Git integration

#### Phase 3: Production Hardening
- Advanced error recovery
- Performance optimization
- Security hardening
- Telemetry & monitoring

### Acceptance Criteria

The system shall be considered complete when:
1. ✓ PDU Media Player scenario detected and prevented
2. ✓ All functional requirements implemented and tested
3. ✓ All validation gates operational with defined thresholds
4. ✓ 90% first-pass success rate achieved in testing
5. ✓ Expert mode available for power users
6. ✓ Complete audit trail for all operations
7. ✓ Graceful degradation under failure conditions
8. ✓ Security scan passed with no critical vulnerabilities
9. ✓ Documentation complete for users and developers
10. ✓ Integration tests pass with all external systems

### Conclusion

This Requirements Blueprint, extracted through systematic interrogation, defines a comprehensive initialization system that addresses the root causes of project failures. By enforcing rigorous requirements gathering, component verification, and validation gates BEFORE any CAD work begins, we transform the engineering process from "hope it works" to "know it works."

The system's success will be measured not in features delivered, but in redesigns prevented, time saved, and engineer frustration eliminated. Every question asked during initialization saves hours of rework later.

Remember: **"Measure twice, cut once"** becomes **"Interrogate completely, verify thoroughly, THEN design with confidence."**

---

## Appendix: Interrogation Notes
- Using "Follow the Cable" methodology to trace requirement dependencies
- Applying JITC (Just-In-Time-Clarification) for progressive detail extraction
- Each requirement must be measurable and testable
- No implementation details until requirements are complete