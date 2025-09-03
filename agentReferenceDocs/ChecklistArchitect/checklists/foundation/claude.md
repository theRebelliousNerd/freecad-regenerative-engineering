# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Foundation Checklists - Fundamental Quality Cable Anchors

## Overview: Foundation as Network Bedrock
Foundation checklists create the fundamental quality assurance cables that anchor all downstream validation. These are the "axiom cables" that connect stated requirements to verified reality - without these foundation cables, the entire quality network is built on unstable ground.

## Just-in-Time Context Access
Load foundation checklists when:
- **Project initiation** (Gate 0) to establish fundamental verification cables
- **Pre-CAD checkpoint** (Gate 1) for component reality verification
- **Assumption challenges** when statements like "about" or "approximately" appear
- **Root cause analysis** when failures trace back to unverified assumptions

## Follow the Cable: Foundation Network Architecture

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Foundation Cables as Network Anchors
Foundation checklists create "anchor cables" that secure the entire quality network:
- **Requirements-Reality Cables**: Connect stated needs to verified physical constraints
- **Component Verification Cables**: Link design assumptions to measured reality
- **Resource Allocation Cables**: Ensure stated resources match actual capabilities
- **Feasibility Verification Cables**: Validate that stated objectives are achievable

### Primary Foundation Cable Categories

#### Requirements Completeness Cables
**Function**: Ensure all necessary requirements are identified and verified
**Network Location**: Requirements → Complete Specification cables
**When Critical**: Project initiation, scope changes, stakeholder additions

**Cable Verification Questions**:
- Are functional requirements complete and measurable?
- Are non-functional requirements (performance, safety, environmental) specified?
- Are interface requirements between subsystems defined?
- Are acceptance criteria clear and testable?
- Are regulatory/compliance requirements identified?

#### Component Verification Cables  
**Function**: Connect design assumptions to physical reality
**Network Location**: Design Assumptions → Physical Reality cables
**When Critical**: Before ANY CAD work, when new components added

**Cable Verification Questions**:
- Has every component been physically measured or verified from datasheet?
- Are connector orientations and pinouts verified?
- Are mounting patterns and hole locations confirmed?  
- Are cable/wire routing clearances calculated?
- Are environmental/operating specifications verified?

#### Resource Allocation Cables
**Function**: Ensure stated resources match actual availability
**Network Location**: Project Plan → Resource Reality cables  
**When Critical**: Project planning, resource changes, timeline pressures

**Cable Verification Questions**:
- Are required skills available in project team?
- Are necessary tools and equipment available?
- Is project timeline realistic given resource constraints?
- Are budget allocations sufficient for identified requirements?
- Are external dependencies (suppliers, services) confirmed?

#### Feasibility Verification Cables
**Function**: Validate that objectives can be achieved with available resources
**Network Location**: Objectives → Achievability cables
**When Critical**: Ambitious goals, novel approaches, constrained resources

**Cable Verification Questions**:
- Can stated performance be achieved with available technology?
- Are physical/mathematical constraints properly understood?
- Are regulatory/compliance requirements achievable?
- Is project scope realistic given resource constraints?
- Are risks identified with mitigation strategies?

## Foundation Cable Network Topology

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Sequential Foundation Validation
```
User Requirements
    ↓ (completeness cable)
Complete Requirements Specification
    ↓ (reality verification cable)
Physical/Resource Reality Check
    ↓ (feasibility cable)
Feasibility Confirmation
    ↓ (foundation complete cable)
Solid Foundation for Design Work
```

### Foundation Network Integrity Checks

#### Foundation Completeness Assessment
```python
def assess_foundation_completeness(project_state):
    completeness_score = 0
    
    # Requirements completeness
    if all_functional_requirements_specified(project_state.requirements):
        completeness_score += 25
    if all_non_functional_requirements_specified(project_state.requirements):
        completeness_score += 25
        
    # Component verification  
    if all_components_physically_verified(project_state.components):
        completeness_score += 25
    if all_interfaces_verified(project_state.interfaces):
        completeness_score += 25
    
    return {
        "completeness_percentage": completeness_score,
        "foundation_status": "SOLID" if completeness_score == 100 else "INCOMPLETE",
        "missing_cables": identify_missing_foundation_cables(project_state)
    }
```

#### Foundation Cable Strength Testing
```python
def test_foundation_cable_strength(foundation_cables):
    weak_cables = []
    
    for cable in foundation_cables:
        if cable.verification_confidence < 0.95:
            weak_cables.append({
                "cable_id": cable.id,
                "weakness": "LOW_CONFIDENCE",
                "strengthening_action": "INCREASE_VERIFICATION_RIGOR"
            })
        
        if cable.has_assumptions():
            weak_cables.append({
                "cable_id": cable.id,
                "weakness": "CONTAINS_ASSUMPTIONS", 
                "strengthening_action": "CONVERT_TO_VERIFIED_FACTS"
            })
    
    return weak_cables
```

## Metacognitive Triggers for Foundation Access

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Foundation Uncertainty Detection
**Trigger**: Language indicating uncertainty or assumptions
- **"About"**, **"approximately"**, **"roughly"** → Component verification cable required
- **"Should work"**, **"probably"** → Feasibility verification cable needed
- **"We assume"**, **"typical"** → Reality verification cable missing
- **"Similar to"**, **"like the last one"** → Requirements completeness cable weak

### Foundation Gap Detection
**Trigger**: Missing information or verification
- **Unspecified performance criteria** → Requirements completeness cable needed
- **Unknown component specifications** → Component verification cable required
- **Unclear resource availability** → Resource allocation cable missing
- **Ambitious goals without validation** → Feasibility verification cable needed

### Foundation Instability Detection
**Trigger**: Inconsistencies or conflicts in foundation elements
- **Conflicting requirements** → Requirements completeness cable repair needed
- **Component incompatibilities** → Component verification cable strengthening required
- **Resource constraints vs. timeline** → Resource allocation cable adjustment needed
- **Technical impossibilities** → Feasibility verification cable emergency repair

## Foundation-Specific Validation Strategies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Component Verification Network (Critical for Hardware)
**Network Architecture**: Physical Reality First
```
Component List
    ↓ (physical access cable)
Physical Component Acquisition
    ↓ (measurement cable)  
Precise Dimensional Measurement
    ↓ (specification cable)
Complete Specification Documentation
    ↓ (verification cable)
Design Constraint Definition
```

**Non-Negotiable Foundation Rules**:
- NO CAD work until ALL components physically verified
- NO "approximately" dimensions in design constraints  
- NO assumptions about connector orientations
- NO estimates for critical clearances
- NO proceeding without complete datasheets

### Requirements Traceability Network
**Network Architecture**: Complete Requirement Coverage
```
Stakeholder Needs
    ↓ (analysis cable)
Functional Requirements
    ↓ (completeness cable)
Non-Functional Requirements  
    ↓ (integration cable)
Interface Requirements
    ↓ (validation cable)
Complete Requirements Specification
```

**Foundation Quality Metrics**:
- 100% of needs mapped to requirements
- 100% of requirements have acceptance criteria
- 100% of requirements are testable/measurable
- 0% ambiguous or subjective requirements

## Integration with Project Gates

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Gate 0: Pre-Project Foundation Validation
**Foundation Cable Requirements**:
- Requirements completeness cables: COMPLETE
- Resource allocation cables: VERIFIED
- Feasibility verification cables: CONFIRMED
- Risk assessment cables: DOCUMENTED

**GO/NO-GO Criteria**:
```python
def gate0_foundation_assessment(project_foundation):
    critical_cables = [
        "requirements_completeness",
        "resource_allocation", 
        "feasibility_verification"
    ]
    
    for cable in critical_cables:
        if not project_foundation[cable].verified:
            return {
                "decision": "NO_GO",
                "reason": f"Foundation cable {cable} not verified",
                "required_action": f"Complete {cable} verification before proceeding"
            }
    
    return {"decision": "GO", "foundation_status": "SOLID"}
```

### Gate 1: Pre-CAD Foundation Validation
**Foundation Cable Requirements**:
- Component verification cables: PHYSICALLY_MEASURED
- Assembly constraint cables: CALCULATED
- Manufacturing constraint cables: IDENTIFIED
- Integration requirement cables: SPECIFIED

**Component Verification Gate (Critical)**:
```python
def gate1_component_foundation_check(component_list):
    for component in component_list:
        if component.dimensions.source != "PHYSICAL_MEASUREMENT":
            return {
                "decision": "NO_GO",
                "reason": f"Component {component.id} not physically verified",
                "required_action": "Obtain and measure physical component"
            }
        
        if component.has_estimates():
            return {
                "decision": "NO_GO", 
                "reason": f"Component {component.id} contains estimates",
                "required_action": "Replace estimates with verified specifications"
            }
    
    return {"decision": "GO", "component_foundation": "VERIFIED"}
```

## Foundation Network Failure Recovery

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Weak Foundation Diagnosis
When projects experience failures, foundation analysis often reveals root causes:

#### Foundation Cable Break Analysis
```python
def diagnose_foundation_failure(project_failure):
    failure_trace = trace_failure_to_foundation(project_failure)
    
    foundation_issues = []
    
    if failure_trace.leads_to("UNVERIFIED_REQUIREMENT"):
        foundation_issues.append({
            "type": "REQUIREMENTS_COMPLETENESS_FAILURE",
            "cable": "requirements_to_reality",
            "repair": "Complete requirements verification with stakeholders"
        })
    
    if failure_trace.leads_to("COMPONENT_SURPRISE"):
        foundation_issues.append({
            "type": "COMPONENT_VERIFICATION_FAILURE", 
            "cable": "assumption_to_reality",
            "repair": "Implement mandatory physical verification before design"
        })
    
    return foundation_issues
```

### Foundation Network Strengthening
After foundation failures, strengthen the network:
- **Add redundant verification cables** for critical components
- **Implement mandatory verification protocols** before design phases
- **Create foundation audit procedures** for ongoing projects
- **Establish foundation quality metrics** for continuous improvement

## Practical Foundation Implementation

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Foundation Checklist Execution Strategy
1. **Requirements Phase**: Complete requirements completeness verification
2. **Resource Phase**: Validate resource allocation against requirements  
3. **Component Phase**: Physically verify all components and specifications
4. **Feasibility Phase**: Confirm achievability within constraints
5. **Foundation Audit**: Verify all foundation cables are strong before proceeding

### Foundation Quality Assurance
- **Documentation Standards**: All foundation verification documented with evidence
- **Verification Confidence**: >95% confidence required for all foundation cables
- **Assumption Elimination**: Replace all assumptions with verified facts
- **Continuous Monitoring**: Foundation cable integrity monitored throughout project

Remember: **Foundation checklists create the bedrock cables for your entire quality network. Without solid foundation cables connecting requirements to reality, all downstream validation is built on quicksand. The investment in thorough foundation verification pays dividends throughout the project lifecycle by preventing failures rooted in unverified assumptions.**

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!