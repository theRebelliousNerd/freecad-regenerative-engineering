# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Domain Specializations - Context Menu

This directory contains specialized interrogation approaches for different types of projects, each with domain-specific failure patterns and prevention strategies. Each domain has unique **cable architectures** that require specialized interrogation techniques.

## Cable Network Architecture by Domain

Each engineering domain creates different types of dependency cables that require specialized extraction techniques:

### Physical Products Cable Networks
- **Component Reality Cables**: Physical dimensions, materials, and mounting methods
- **Assembly Logic Cables**: Tool access, sequence constraints, and fitment dependencies  
- **Thermal Management Cables**: Heat dissipation paths and temperature limits
- **Service Access Cables**: Maintenance procedures and component replaceability

### Software Applications Cable Networks  
- **User Journey Cables**: Workflow paths and interaction dependencies
- **Performance Constraint Cables**: Response time, throughput, and scalability limits
- **Security Boundary Cables**: Authentication, authorization, and data protection requirements
- **Integration Interface Cables**: API contracts, data formats, and protocol specifications

### Systems Integration Cable Networks
- **Protocol Dependency Cables**: Communication standards and message formats
- **Data Flow Cables**: Information routing and transformation requirements  
- **Compatibility Matrix Cables**: Version dependencies and backward compatibility constraints
- **Boundary Responsibility Cables**: System ownership and interface management

### Safety-Critical Cable Networks
- **Hazard Propagation Cables**: Failure modes and cascade effects
- **Regulatory Compliance Cables**: Standard requirements and certification dependencies
- **Safety Margin Cables**: Redundancy requirements and failure tolerance levels
- **Verification Traceability Cables**: Testing requirements and audit trail needs

## JITC Domain Context Loading

Your domain specialization follows Just-in-Time principles - load domain knowledge when uncertainty signals indicate need:

## Directory Contents

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### 1. physical-products.md
**When to read**: For any physical product, enclosure, or mechanical assembly project
**Contains**: 
- Component reality check protocols (MANDATORY for enclosures)
- Assembly sequence validation and tool access analysis
- Thermal and environmental interrogation techniques
- Service and maintenance accessibility requirements
**Triggers**: Enclosure design, mechanical assemblies, physical components integration, manufacturing projects

### 2. software-applications.md
**When to read**: For web applications, mobile apps, or software system projects
**Contains**:
- Business problem and value proposition deep-dive
- User persona analysis and workflow mapping
- Non-functional requirements extraction (performance, security)
- Integration architecture and platform requirements
**Triggers**: Software development, web applications, system integration, digital products

### 3. systems-integration.md
**When to read**: For projects involving multiple subsystems or complex interfaces
**Contains**:
- Interface specification and protocol definition
- Data flow analysis and integration mapping
- Compatibility and interoperability requirements
- System boundary and responsibility matrix
**Triggers**: Multi-system projects, API integrations, embedded systems, complex architectures

### 4. safety-critical-systems.md
**When to read**: For medical devices, automotive, aerospace, or any safety-critical application
**Contains**:
- Hazard analysis and risk assessment protocols
- Regulatory compliance requirement extraction
- Failure mode analysis and safety margin definition
- Certification and testing requirement identification
**Triggers**: Medical devices, safety systems, regulatory compliance needed, human safety implications

## Reading Priority & Dependencies

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**PROJECT TYPE DETERMINES PRIORITY**:

**Physical Product Project**:
1. **physical-products.md** (PRIMARY)
2. systems-integration.md (if electronics/software involved)
3. safety-critical-systems.md (if safety implications)

**Software Application Project**:
1. **software-applications.md** (PRIMARY)  
2. systems-integration.md (if multiple systems involved)
3. safety-critical-systems.md (if safety/compliance critical)

**Complex System Project**:
1. **systems-integration.md** (PRIMARY)
2. physical-products.md (if hardware components)
3. software-applications.md (if software components)
4. safety-critical-systems.md (if safety implications)

**Safety-Critical Project**:
1. **safety-critical-systems.md** (PRIMARY)
2. Domain-specific file based on implementation type
3. systems-integration.md (for interface safety analysis)

## Integration with Other Directories

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


- **References FROM**: core-philosophy (applies Socratic method to domain specifics)
- **References FROM**: interrogation-protocols (uses conversation patterns for domain contexts)
- **Flows TO**: blueprint-generation (domain-specific requirements formats)
- **Coordinates WITH**: validation-methods (domain-specific validation approaches)

## Domain Selection Criteria

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### Physical Products Domain
- Mechanical assemblies, enclosures, housings
- 3D printed or machined parts
- Component integration with dimensional constraints
- Assembly, service, or maintenance requirements
- Thermal or environmental considerations

### Software Applications Domain  
- Web applications, mobile apps, desktop software
- User interfaces and user experience requirements
- Database and data processing systems
- API development and integration
- Performance and scalability requirements

### Systems Integration Domain
- Multiple subsystems working together
- Hardware-software integration
- Communication protocols and interfaces
- Legacy system integration
- Complex data flows between systems

### Safety-Critical Systems Domain
- Medical devices and healthcare systems
- Automotive or transportation systems
- Industrial control and automation
- Aerospace and defense applications
- Any system where failure could harm humans

## Cross-Domain Considerations

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Many projects span multiple domains - use appropriate combinations:

**IoT Device**: Physical Products + Software Applications + Systems Integration
**Medical Device**: Safety-Critical + Physical Products + Software Applications  
**Industrial Automation**: Safety-Critical + Systems Integration + Software Applications
**Smart Enclosure**: Physical Products + Systems Integration

## Success Indicators by Domain

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Physical Products Success**:
- All components physically verified with measurements
- Assembly sequences proven feasible with tool access
- Thermal and environmental requirements quantified
- Service procedures documented and validated

**Software Applications Success**:
- User personas and workflows detailed
- Performance requirements quantified with test criteria
- Security and compliance framework established
- Integration points mapped with data flows

**Systems Integration Success**:
- Interface specifications complete with protocols
- System boundaries and responsibilities clear
- Compatibility matrices developed and verified
- Integration testing strategies defined

**Safety-Critical Success**:
- Hazard analysis complete with risk mitigation
- Regulatory requirements identified and planned
- Safety margins calculated and verified
- Certification pathways established

## Warning Signs for Wrong Domain Focus

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Missing Physical Product Focus**:
- Accepting "standard" components without verification
- No assembly sequence consideration
- Thermal requirements ignored
- Service access not planned

**Missing Software Application Focus**:
- Vague user requirements and success criteria
- Performance requirements undefined
- Security considerations deferred
- Integration complexity underestimated

**Missing Systems Integration Focus**:
- Interface specifications incomplete
- Data flow undefined between systems
- Compatibility assumptions untested
- System boundaries unclear

**Missing Safety-Critical Focus**:
- Risk assessment not performed
- Regulatory requirements unknown
- Safety margins not calculated
- Certification path not established

## Integration Notes

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


Each domain specialization builds upon the universal interrogation protocol and conversation patterns while adding domain-specific techniques, failure patterns, and validation approaches. The goal is comprehensive requirements extraction tailored to the unique challenges of each problem domain.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!