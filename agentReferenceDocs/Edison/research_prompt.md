# Research Prompt: The Edison Agent - Master of Electronics, Circuits, and PCB Design

## Core Research Directive

You are tasked with creating a comprehensive philosophical and practical framework for an AI agent that embodies the principles of electronic circuit design, PCB layout, and practical electrical engineering. This agent, named after Thomas Edison whose systematic approach to invention and his "Muckers" team at Menlo Park created the modern R&D laboratory, should represent mastery in electronic system design, from schematic capture through manufacturing.

## Research Requirements

Please produce a detailed essay (minimum 10,000 words) that covers the following aspects:

### Part 1: Historical and Philosophical Foundation
- Research Thomas Edison's systematic approach to invention and his "99% perspiration" philosophy
- Explore the rivalry with Tesla and how it shaped AC vs. DC system design
- Investigate Edison's laboratory methodology and team-based innovation model
- Analyze the evolution from Edison's discrete components to integrated circuits
- Examine the philosophical shift from analog to digital design paradigms

### Part 2: Electronic Circuit Fundamentals
- Deep dive into circuit analysis: Kirchhoff's laws, Thevenin/Norton, superposition
- Explain passive components: resistors, capacitors, inductors, transformers
- Detail active components: diodes, transistors (BJT, MOSFET), op-amps
- Explore digital logic: gates, flip-flops, counters, state machines
- Investigate power electronics: rectifiers, inverters, switching regulators
- Analyze mixed-signal design: ADCs, DACs, PLLs, analog/digital partitioning

### Part 3: PCB Design and Layout Principles
- Research stackup design: layer count, impedance control, material selection
- Explore routing strategies: Manhattan, 45-degree, differential pairs, length matching
- Investigate power distribution: planes, decoupling, PDN impedance
- Detail thermal management: copper pours, thermal vias, heat spreading
- Analyze high-speed design: transmission lines, termination, crosstalk
- Explore flex and rigid-flex design considerations

### Part 4: Signal and Power Integrity
- Signal integrity: reflections, ringing, eye diagrams, jitter
- Power integrity: voltage drop, ground bounce, decoupling strategies
- EMI/EMC: common mode, differential mode, shielding, filtering
- Grounding strategies: star, multipoint, ground planes, isolation
- Clock distribution: tree, mesh, source synchronous
- Return current paths and loop area minimization

### Part 5: Component Selection and Management
- Component parametrics: tolerance, temperature coefficient, aging
- Package types: through-hole, SMD, BGA, chip-scale, bare die
- Sourcing strategies: availability, obsolescence, second sources
- Cost optimization: value engineering, design for cost
- Reliability: MTBF, derating, stress analysis, burn-in
- Library management: symbols, footprints, 3D models, parameters

### Part 6: Design for Manufacturing (DFM)
- Assembly processes: wave, reflow, selective, hand soldering
- Solder paste and stencil design
- Component placement: orientation, spacing, courtyards
- Via design: types, aspect ratio, filling, tenting
- Testability: test points, boundary scan, flying probe, ICT
- Panelization: rails, tabs, fiducials, tooling holes

### Part 7: Embedded Systems and Firmware Considerations
- Microcontroller/microprocessor selection criteria
- Memory architectures: RAM, ROM, Flash, external interfaces
- Peripheral interfaces: I2C, SPI, UART, USB, Ethernet
- Power management: sleep modes, clock gating, voltage scaling
- Bootloaders and firmware update mechanisms
- Hardware-software co-design and partitioning

### Part 8: Specialized Circuit Applications
- Power supplies: linear, switching, isolated, PFC
- RF/wireless: matching networks, baluns, filters, amplifiers
- Sensor interfaces: amplification, filtering, calibration
- Motor drives: H-bridges, PWM, current sensing, protection
- Audio: amplifiers, codecs, noise management
- Battery management: charging, protection, fuel gauging

### Part 9: Integration with FreeCAD and the Agent Ecosystem
- How should the Edison agent manage the 2D schematic to 3D PCB workflow?
- What Python libraries should be leveraged (KiCad, SKiDL, PySpice)?
- How should the agent interface with mechanical constraints from FreeCAD models?
- How should thermal analysis (Curie/Watt) influence component placement?
- How should RF requirements (Hertz) affect PCB layout decisions?
- What validation procedures should verify electrical performance?

### Part 10: Modern Design Methodologies and Tools
- Simulation: SPICE, IBIS, S-parameters, field solvers
- Constraint-driven design: electrical, physical, assembly rules
- Autorouting vs. manual routing strategies
- Design reuse: modules, templates, reference designs
- Version control and collaboration in hardware design
- AI-assisted placement and routing optimization

### Part 11: Testing and Validation
- Design verification: simulation, breadboarding, prototyping
- Compliance testing: FCC, CE, UL, RoHS, REACH
- Environmental testing: temperature, humidity, vibration, shock
- Functional testing: parametric, boundary scan, system test
- Failure analysis: root cause, corrective actions
- Production testing strategies and yield optimization

## Specific Questions to Address

1. How should the agent balance circuit performance with cost and manufacturability?
2. What heuristics can identify potential signal integrity issues early?
3. How should analog and digital sections be partitioned and isolated?
4. What strategies minimize EMI while maintaining signal quality?
5. How can the agent ensure robust operation across component tolerances?
6. What methods should validate designs against industry standards?
7. How should the agent handle multi-board system design and interconnects?
8. What are the key trade-offs in layer count vs. routing complexity?
9. How should power distribution be optimized for efficiency and stability?
10. What role should simulation play vs. prototype testing?

## Deliverable Format

The essay should:
- Include circuit analysis techniques with practical examples
- Provide PCB design rules and best practices
- Reference current industry standards (IPC, IEEE, JEDEC)
- Suggest computational workflows for circuit and PCB design
- Define clear interfaces with other agents in the system
- Include troubleshooting guides for common electronic problems
- Balance theoretical understanding with practical implementation
- Address both analog and digital design challenges
- Provide guidelines for design review and verification

## Research Sources to Consider

- Classic texts: "Art of Electronics" (Horowitz & Hill), "High-Speed Digital Design" (Johnson & Graham)
- PCB design: "Signal and Power Integrity" (Bogatin), IPC-2221/2222 standards
- Industry resources: Application notes from TI, Analog Devices, Intel
- Open source tools: KiCad, NgSpice, OpenEMS
- Journals: IEEE Transactions on Circuits and Systems, EDN, Signal Integrity Journal
- Component databases: Digi-Key, Mouser, Octopart APIs
- Simulation tools: LTspice, Cadence, Altium documentation
- Manufacturing: IPC standards, assembly house design guides
- Recent advances in HDI, embedded components, and additive electronics

The final essay should serve as the definitive guide for implementing an electronics and PCB design agent that can work within the FreeCAD MCP environment, designing everything from simple breakout boards to complex multi-layer high-speed digital systems while ensuring manufacturability, reliability, and regulatory compliance.