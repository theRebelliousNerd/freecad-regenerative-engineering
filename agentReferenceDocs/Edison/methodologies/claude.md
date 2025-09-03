# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Edison Methodologies - Circuit Design Through Cable Dependencies

## What's in This Folder

This directory contains specific methodologies for electronics design implementation, focused on how design decisions create cascading dependencies through interconnected "cable" networks.

### Core Documents
- `01_component_selection_framework.md` - Systematic component choice methodology
- `design_for_manufacturing.md` - Manufacturing constraint integration
- `systematic_iteration.md` - Structured design iteration processes

## When to Read These Files (Just-in-Time Context)

### **Component Selection Uncertainty Triggers**
Read `01_component_selection_framework.md` when:
- Choosing between multiple component options with trade-offs
- Component parameters affect multiple design domains (thermal, mechanical, cost)
- Supply chain constraints require alternative component evaluation
- Performance requirements conflict with cost/availability constraints

### **Manufacturing Integration Triggers**
Read `design_for_manufacturing.md` when:
- PCB design rules conflict with circuit requirements
- Component placement affects assembly processes
- Design complexity exceeds manufacturing capabilities
- Cost optimization requires manufacturing-driven design changes

### **Iteration Process Uncertainty**
Read `systematic_iteration.md` when:
- Design convergence is slow or failing
- Multiple design variables interact unpredictably
- Need structured approach to design space exploration
- Knowledge capture from iterations is inadequate

## The Component Selection Cable Network

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **The Primary Selection Cables**
Every component choice creates immediate dependencies:

**Electrical Cables:**
- Voltage/current ratings define power delivery requirements
- Frequency response affects signal integrity throughout system
- Noise characteristics couple to sensitive circuit nodes
- Temperature coefficients affect system accuracy

**Thermal Cables:**
- Power dissipation demands cooling solutions
- Junction temperatures limit operating conditions
- Thermal resistance affects heat flow paths
- Package thermal properties define heat sink requirements

**Mechanical Cables:**
- Component dimensions affect PCB routing density
- Package types determine assembly processes
- Lead pitch affects PCB trace/via capabilities
- Weight affects mechanical support requirements

**Supply Chain Cables:**
- Availability affects production schedules
- Cost affects system economics
- Alternative sourcing affects design validation
- End-of-life affects product lifecycle

### **The Manufacturing Cable Network**

**PCB Process Cables:**
- Minimum trace/space limits signal routing
- Via sizes affect signal integrity and routing density
- Layer count affects cost and manufacturing complexity
- Surface finish affects component assembly and reliability

**Assembly Process Cables:**
- Component placement density affects pick-and-place efficiency
- Mixed package types affect assembly line configuration
- Thermal profiles affect component selection compatibility
- Test access affects debugging and validation capability

**Quality Cables:**
- Defect rates affect manufacturing yield
- Inspection requirements affect assembly cost
- Rework capability affects defect recovery
- Statistical process control affects quality consistency

## Circuit Complexity-Based Retrieval Strategy

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Level 1: Basic Circuits (Single function blocks)**
**Metacognitive Trigger:** Standard components with well-known characteristics
- Minimal methodology retrieval needed
- Focus on basic electrical parameter matching
- Simple cost-performance trade-offs

### **Level 2: Moderate Circuits (Multi-function integration)**
**Metacognitive Trigger:** Component interactions affect system performance
- Retrieve component selection framework for systematic evaluation
- Consider thermal and mechanical interactions
- Apply manufacturing constraints early in selection

### **Level 3: Complex Circuits (High-performance, multi-domain)**
**Metacognitive Trigger:** Component choices cascade across multiple domains
- Full methodology engagement required
- Systematic iteration methodology essential
- Manufacturing integration from concept phase

### **Level 4: System-Level Integration**
**Metacognitive Trigger:** Component decisions affect entire product architecture
- All methodologies must be integrated
- Cross-domain optimization required
- Holistic cable network analysis essential

## Dependency-Driven Decision Framework

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **Component Selection Process**
```
1. TRIGGER: Performance requirement uncertainty
2. RETRIEVE: Relevant component selection criteria
3. ANALYZE: Multi-domain cable impact
   - Electrical performance cables
   - Thermal management cables  
   - Mechanical integration cables
   - Manufacturing feasibility cables
4. OPTIMIZE: Multi-objective trade-offs
5. VALIDATE: Critical cable integrity
6. DOCUMENT: Decision rationale and dependencies
```

### **Manufacturing Integration Process**
```
1. TRIGGER: Design-manufacturing conflict detected
2. RETRIEVE: Relevant DFM guidelines
3. ANALYZE: Manufacturing cable constraints
   - Process capability limits
   - Assembly complexity factors
   - Quality control requirements
4. NEGOTIATE: Design vs. manufacturing trade-offs
5. ITERATE: Design modifications
6. VERIFY: Manufacturing feasibility
```

## Inter-Agent Cable Handoffs

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


### **To Thermal Domain (Watt Agent)**
- Component power dissipation specifications
- Thermal resistance models  
- Junction temperature limits
- Cooling requirement calculations

### **To Mechanical Domain (DaVinci/Brunel Agents)**
- Component physical dimensions and tolerances
- Mounting and connector requirements
- Vibration and shock specifications
- Assembly access requirements

### **To Manufacturing Domain (Gabe Agent)**  
- PCB process requirements and constraints
- Component package compatibility
- Assembly process optimization
- Quality control and testing requirements

### **To Supply Chain Domain (Requirements Interrogator)**
- Component availability and lead times
- Cost targets and volume requirements
- Alternative sourcing strategies
- Lifecycle management plans

## Metacognitive Uncertainty Recognition

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!


**Component Selection Uncertainty Signals:**
- Multiple components meet electrical specs with different trade-offs
- Thermal analysis reveals power dissipation concerns
- Mechanical constraints conflict with electrical performance
- Supply chain risks threaten design viability

**Manufacturing Integration Uncertainty Signals:**
- PCB design rules prevent optimal circuit layout
- Component placement conflicts with assembly processes
- Design complexity exceeds manufacturing capabilities
- Quality requirements conflict with cost targets

**Response Protocol:**
1. Identify specific uncertainty type (electrical, thermal, mechanical, manufacturing)
2. Retrieve relevant methodology documents
3. Apply systematic evaluation framework
4. Document decision rationale for future reference
5. Update design rule database with new knowledge

---

The methodologies establish that electronics design decisions are never isolated - they create cascading dependencies through cable networks that span electrical, thermal, mechanical, and manufacturing domains. Systematic methodologies provide the framework for navigating these interconnected constraint networks while maintaining design integrity and optimization across all domains.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!