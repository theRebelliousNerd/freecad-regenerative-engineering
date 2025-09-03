# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Requirements Interrogator - Validation Methods Context Guide

This directory contains knowledge for validating requirements completeness and ensuring the foundational cable network has integrity before engineering begins.

## Validation as Cable Network Quality Assurance

Your validation process ensures that the **requirement cables** you've established can bear the load of the entire engineering process. Each validation method tests a different aspect of cable strength and connectivity.

### Metacognitive Validation Framework

Use these uncertainty signals to determine when validation is needed:

**High Uncertainty Indicators (Immediate Validation Required):**
- Requirements use vague language ("good," "fast," "reliable")
- Stakeholder alignment unclear or assumed
- Performance targets lack measurement methods
- Interfaces defined without protocols or standards
- Dependencies mentioned without verification

**Medium Uncertainty (Systematic Validation Needed):**
- Requirements complete but not mathematically precise
- All stakeholders heard from but consensus not verified
- Component specifications gathered but not validated
- Assembly sequences planned but not verified

**Low Uncertainty (Spot Check Validation):**
- Requirements mathematically precise and verified
- Stakeholder consensus documented and signed off
- All components physically measured or datasheet-verified
- Assembly sequence tested with mockups or experience

## Just-in-Time Context for Validation Methods

### Validation Context Retrieval Strategy

**Load Immediately When:**
- Creating Requirements Blueprint (need completeness criteria)
- Stakeholder conflicts emerge (need alignment techniques)
- Engineering agents report missing context (need gap analysis methods)
- Requirements change during project (need impact validation)

**Load Based on Project Type:**

**Physical Products:**
- Component verification checklists
- Dimensional stack-up validation
- Assembly sequence verification
- Manufacturing constraint validation

**Software Applications:**
- User story completeness validation
- Non-functional requirement validation
- Interface specification validation
- Security requirement validation

**System Integration:**
- Interface boundary validation
- Data flow validation
- Performance requirement validation
- Integration sequence validation

## Directory Contents (Future Structure)

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Core Validation Files (Create as Needed)

**requirements-completeness-verification.md**
- Systematic checklists for requirement coverage
- Gap analysis methods for missing domains
- Traceability verification procedures
- *Cable Integrity*: Ensures all requirement cables properly connected

**consistency-checking-protocols.md**
- Conflict detection between requirements
- Requirement hierarchy validation
- Constraint compatibility verification
- *Cable Integrity*: Prevents contradictory cable tensions

**feasibility-assessment-methods.md**
- Technical feasibility validation
- Economic feasibility assessment
- Timeline feasibility verification
- *Cable Integrity*: Ensures cables don't exceed system capacity

**stakeholder-review-processes.md**
- Stakeholder alignment verification
- Requirements approval protocols
- Change management procedures
- *Cable Integrity*: Validates cable endpoints are properly connected

**change-management-procedures.md**
- Requirements evolution tracking
- Impact analysis for requirement changes
- Version control integration
- *Cable Integrity*: Manages cable modifications without breaking network

## Validation Trigger Algorithm

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


```python
def validate_requirements_completeness(requirements_set):
    uncertainty_score = calculate_requirements_uncertainty()
    
    if uncertainty_score > HIGH_THRESHOLD:
        # Critical validation needed
        return trigger_full_validation_suite()
    
    elif uncertainty_score > MEDIUM_THRESHOLD:
        # Systematic validation needed
        return trigger_domain_specific_validation()
    
    else:
        # Spot check validation sufficient
        return trigger_minimal_validation()

def calculate_requirements_uncertainty():
    # Check for vague language
    vague_language_score = count_vague_terms() / total_requirements
    
    # Check for unverified components
    unverified_components_score = count_unverified_components() / total_components
    
    # Check for missing stakeholder sign-off
    stakeholder_alignment_score = count_unsigned_stakeholders() / total_stakeholders
    
    # Check for unmeasured parameters
    imprecision_score = count_unmeasured_parameters() / total_parameters
    
    return weighted_average([
        vague_language_score,
        unverified_components_score,
        stakeholder_alignment_score,
        imprecision_score
    ])
```

## Cable Network Validation Checklist

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Foundation Cables (Always Validate)
- [ ] **User Need Cables**: Every requirement traces back to verified user need
- [ ] **Success Criteria Cables**: Every requirement has measurable acceptance criteria
- [ ] **Constraint Cables**: Every requirement identifies its constraint boundaries
- [ ] **Responsibility Cables**: Every requirement assigned to specific engineering agent

### Domain-Specific Cables (Validate by Project Type)

**Physical Product Cables:**
- [ ] **Component Reality Cables**: All parts measured or datasheet-verified
- [ ] **Assembly Logic Cables**: Assembly sequence physically verified
- [ ] **Manufacturing Constraint Cables**: Production method capabilities confirmed
- [ ] **Environmental Cables**: Operating conditions and testing standards specified

**Software Application Cables:**
- [ ] **User Journey Cables**: All user paths mapped and validated
- [ ] **Performance Cables**: All performance targets quantified and testable
- [ ] **Integration Cables**: All interfaces specified with protocols
- [ ] **Security Cables**: All security requirements linked to standards

**System Integration Cables:**
- [ ] **Data Flow Cables**: All data paths mapped and validated
- [ ] **Interface Boundary Cables**: All system boundaries precisely defined
- [ ] **Performance Chain Cables**: End-to-end performance requirements verified
- [ ] **Failure Mode Cables**: All failure scenarios identified and mitigated

### Validation Cable Integrity Tests

**Test 1: Traceability Test**
- Can every design decision be traced back to a requirement?
- Can every requirement be traced back to a user need?
- Are there any orphaned requirements with no clear purpose?

**Test 2: Completeness Test**
- Are all stakeholder needs addressed?
- Are all technical domains covered?
- Are all interfaces specified?
- Are all constraints identified?

**Test 3: Precision Test**
- Are all performance targets quantified?
- Are all physical parameters measured?
- Are all quality criteria defined?
- Are all acceptance criteria testable?

**Test 4: Consistency Test**
- Are there conflicting requirements?
- Are there impossible constraint combinations?
- Are there circular dependencies?
- Are priorities clearly established?

## Emergency Validation Protocols

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**When Engineering Agents Report Missing Context:**
1. Immediately identify the knowledge gap category
2. Trace the gap back to original requirement source
3. Determine if gap represents missing requirement or unclear specification
4. Re-interrogate stakeholders for missing context
5. Update Requirements Blueprint with clarified information
6. Validate change impact across all affected cables

**When Stakeholder Conflicts Emerge:**
1. Map conflicting requirements to stakeholder origins
2. Identify underlying needs driving each position
3. Facilitate negotiation based on user value priorities
4. Document agreed resolution with all parties
5. Update requirement hierarchy and priorities
6. Validate no new conflicts created by resolution

**When Requirements Change Mid-Project:**
1. Analyze impact on existing cable network
2. Identify all dependent requirements and constraints
3. Validate feasibility of change within project constraints
4. Update Requirements Blueprint with change impact analysis
5. Obtain stakeholder approval for propagated changes
6. Ensure all engineering agents notified of changes

## Integration with Mental Models

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Your validation process embodies the **Just-in-Time Context** philosophy:

- **Proactive Scoping**: Anticipate validation needs based on project type and complexity
- **Metacognitive Monitoring**: Continuously assess uncertainty in requirements quality
- **Dynamic Context Management**: Load specific validation methods based on detected gaps
- **Utility-Theoretic Decisions**: Balance validation thoroughness against project timeline

Remember: Validation is not bureaucracy - it's **quality assurance for the foundational cable network**. Every validation step you perform prevents exponentially more expensive failures downstream in the engineering process.

The strength of the entire engineering system depends on the integrity of the requirement cables you establish and validate.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!