# Research Prompt: The Tesla Agent - Master of Electromagnetic Design and Electric Motor Engineering

## Core Research Directive

You are tasked with creating a comprehensive philosophical and practical framework for a claude code subagent using its an agent using https://github.com/contextform/freecad-mcp . this AI agent that embodies the principles of electromagnetic engineering and electric motor design. This agent, named after Nikola Tesla, should represent the pinnacle of understanding in electromagnetic phenomena, motor design, and energy conversion systems.

## Research Requirements

Please produce a detailed essay (minimum 10,000 words) that covers the following aspects:

### Part 1: Historical and Philosophical Foundation
- Research Nikola Tesla's approach to electromagnetic design and his revolutionary understanding of rotating magnetic fields
- Explore the fundamental principles that allowed Tesla to visualize complex electromagnetic interactions in his mind
- Investigate how Tesla's rivalry with Edison shaped different approaches to electrical system design
- Analyze Tesla's method of "seeing" magnetic fields and how this can be translated into computational visualization

### Part 2: Core Electromagnetic Principles
- Deep dive into Maxwell's equations and their practical application in motor design
- Explain the physics of rotating magnetic fields and how they create torque
- Detail the relationship between electrical and mechanical energy conversion
- Explore losses in electromagnetic systems (core losses, copper losses, friction, windage)
- Investigate electromagnetic compatibility (EMC) and interference (EMI) considerations

### Part 3: Modern Electric Motor Design Methodologies
- Research contemporary motor types: BLDC, PMSM, induction, synchronous reluctance, switched reluctance
- Analyze design trade-offs: efficiency vs. cost vs. power density vs. reliability
- Investigate advanced materials: rare earth magnets, soft magnetic composites, Litz wire
- Explore cooling strategies: air cooling, liquid cooling, oil cooling, potting compounds
- Detail winding configurations: concentrated vs. distributed, fractional slot, hairpin windings

### Part 4: Computational Methods and Simulation
- Research finite element analysis (FEA) for electromagnetic field simulation
- Investigate multi-physics simulation: electromagnetic-thermal-structural coupling
- Explore optimization algorithms for motor design: genetic algorithms, particle swarm, topology optimization
- Detail parametric design approaches for rapid motor prototyping
- Analyze co-simulation with control systems and power electronics

### Part 5: Integration with FreeCAD and the Agent Ecosystem
- How should the Tesla agent interact with FreeCAD's geometry kernel for motor component design?
- What Python libraries and tools should the agent leverage (FEniCS, FEMM, MotorCAD alternatives)?
- How should the agent collaborate with other specialists (thermal analysis from Watt, materials from Curie)?
- What verification and validation procedures should the agent implement?

### Part 6: Practical Design Workflows
- Step-by-step process for designing a motor from specifications to final geometry
- Critical design checks and validation procedures
- Manufacturing considerations: tolerances, assembly, magnetization
- Testing protocols: back-EMF, cogging torque, efficiency mapping
- Documentation standards for electromagnetic designs

### Part 7: Advanced Topics and Future Considerations
- Research emerging technologies: axial flux motors, transverse flux, Halbach arrays
- Investigate application-specific requirements: automotive traction, aerospace, robotics, renewable energy
- Explore sustainability: motor recycling, rare earth alternatives, lifecycle assessment
- Analyze Industry 4.0 integration: digital twins, predictive maintenance, IoT sensors

## Specific Questions to Address

1. How should the agent approach the fundamental trade-off between copper losses and iron losses?
2. What mental models should the agent use to visualize 3D magnetic field distributions?
3. How can the agent ensure designs are manufacturable with real-world tolerances?
4. What iterative optimization strategies should be employed for multi-objective motor design?
5. How should the agent handle the coupling between electromagnetic, thermal, and structural domains?
6. What heuristics can accelerate the design process while maintaining accuracy?
7. How should the agent validate designs against industry standards (IEC, NEMA, IEEE)?

## Deliverable Format

The essay should:
- Be written in a technical yet accessible style
- Include specific mathematical formulations where necessary
- Provide concrete examples and case studies
- Reference current best practices and standards
- Suggest specific Python code structures and algorithms
- Define clear interfaces with other agents in the system
- Include a philosophical framework that captures Tesla's visionary approach while grounding it in modern computational methods

## Research Sources to Consider

- IEEE Transactions on Magnetics, Industry Applications, and Energy Conversion
- Modern textbooks on electric machine design (Hanselman, Hendershot, Miller, Pyrhonen)
- Open-source electromagnetic simulation tools and their methodologies
- Industry white papers from motor manufacturers (ABB, Siemens, WEG, Nidec)
- Recent advances in wide-bandgap semiconductors and their impact on motor design
- Sustainability reports on electric motor lifecycle and recycling

The final essay should serve as the definitive guide for implementing an electromagnetic design agent that can work within the FreeCAD MCP environment, collaborating with other specialized agents to create optimized, manufacturable electric motor designs.