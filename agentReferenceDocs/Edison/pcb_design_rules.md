# PCB Design Rules and Guidelines - 2024/2025 Edison Agent Reference

## Core Design Principles

### Edison's Systematic Approach to PCB Design
Following Thomas Edison's "99% perspiration" philosophy, PCB design requires methodical attention to countless technical details while maintaining the 1% inspiration that drives innovation. Every trace, via, and component placement decision must be validated through systematic analysis and testing.

## Layer Stackup Design

### Standard Stackup Configurations
**2-Layer Boards:**
- Signal layer (top)
- Ground/Power layer (bottom)
- Maximum frequency: ~100 MHz
- Cost-effective for simple designs
- Limited high-speed capability

**4-Layer Boards:**
- Signal (top)
- Ground plane
- Power plane  
- Signal (bottom)
- Recommended minimum for mixed-signal designs
- Good EMI performance with proper plane design

**6+ Layer Boards:**
- Multiple signal layers with dedicated reference planes
- Required for high-speed digital (>1 GHz)
- Better signal integrity and power distribution
- Higher cost but essential for complex designs

### 2024 Stackup Best Practices
- Use consecutive ground and power planes to create tight coupling capacitance
- Maintain symmetrical stackups to prevent board warpage
- Target 50Ω single-ended and 100Ω differential impedance
- Keep dielectric thickness consistent for controlled impedance
- Place high-speed signals adjacent to reference planes

## Trace Routing Rules

### Current Carrying Capacity
**IPC-2221 Current Tables (Updated 2024):**
- 1 oz copper: 1 mil width carries ~1 mA for 10°C rise
- 2 oz copper: 1 mil width carries ~1.4 mA for 10°C rise
- Always derate by 50% for safety margins
- Use trace width calculators for precise calculations

**High Current Design:**
- Use thick copper (2-4 oz) for power traces
- Implement copper pours for heat spreading
- Consider multiple parallel traces for very high currents
- Add thermal vias under high-current traces

### High-Speed Digital Rules

**Differential Pairs:**
- Maintain tight coupling: spacing = 0.5 × trace width
- Length matching tolerance:
  - USB 2.0: ±150 mils (3.8 mm)
  - USB 3.0: ±5 mils (0.127 mm)
  - DDR4: ±10 mils (0.254 mm)
  - HDMI: ±3 mils (0.076 mm)
  - Ethernet: ±25 mils (0.635 mm)

**Single-Ended Traces:**
- 3W rule: space between traces ≥ 3 × trace width
- 5W rule for critical signals: space ≥ 5 × trace width
- Keep traces on adjacent layers perpendicular
- Minimize layer changes (vias)

### Via Design Rules

**Standard Via Specifications:**
- Drill size: 0.1-0.4 mm (4-16 mil)
- Pad size: drill + 0.15 mm (6 mil) minimum
- Aspect ratio: <10:1 (depth:diameter)
- Annular ring: 0.05 mm (2 mil) minimum per IPC-2221

**Via Types and Applications:**
- **Through-hole vias**: Standard, lowest cost
- **Blind vias**: Top/bottom to internal layer
- **Buried vias**: Between internal layers only
- **Microvias**: <0.15 mm drill, for HDI designs

**Thermal Vias:**
- 0.2-0.4 mm diameter optimal for thermal transfer
- Grid spacing: 1.0-1.2 mm center-to-center
- Place directly under thermal pads
- Connect to internal copper planes for heat spreading

## Component Placement Rules

### General Placement Guidelines
- Orient polarized components consistently
- Group related components together
- Maintain 0.25 mm minimum component spacing
- Keep sensitive analog circuits away from switching circuits
- Place decoupling capacitors within 5 mm of power pins

### Power Management Placement
- Linear regulators: ensure adequate heatsinking
- Switching regulators: follow manufacturer layout guidelines
- Input capacitors: place close to power input
- Output capacitors: place close to load
- Feedback components: keep traces short and direct

### High-Speed Digital Placement
- Keep crystal/oscillator traces short (<12 mm)
- Place termination resistors at receiving end
- Group differential pairs together
- Isolate clock circuits from other signals
- Use ground guards around sensitive circuits

## Thermal Management

### Thermal Via Design
**Optimal Configuration:**
- Via diameter: 0.3 mm (12 mil) for best thermal conductivity
- Array spacing: 1.0-1.2 mm center-to-center
- Fill with thermal epoxy or electroplated copper
- Connect to large copper areas on multiple layers

**Thermal Performance:**
- Single 0.3 mm via: ~0.3°C/W thermal resistance
- 3×3 array of thermal vias: ~0.05°C/W thermal resistance
- Copper pour connection: additional 50% improvement

### Heat Spreading Techniques
- Large copper pours connected to thermal vias
- Thermal relief connections for manufacturing
- Strategic component placement for airflow
- Heat sink mounting considerations

## Power Distribution Network (PDN)

### Decoupling Strategy
**Capacitor Selection:**
- 0.1 μF ceramic: high-frequency noise (10 MHz-1 GHz)
- 1-10 μF ceramic: mid-frequency (1-10 MHz)  
- 100-1000 μF electrolytic: low-frequency (<1 MHz)
- Place multiple values in parallel for broadband decoupling

**Placement Rules:**
- High-frequency caps: within 5 mm of power pins
- Medium-frequency caps: within 15 mm of power pins
- Bulk caps: distribute across board regions
- Use shortest possible traces to minimize inductance

### Power Plane Design
- Minimize plane splits and slots
- Use solid planes where possible
- Bridge splits with capacitors
- Maintain low impedance paths
- Consider current density in plane design

## Design for Manufacturing (DFM)

### 2024 Manufacturing Constraints
**Minimum Feature Sizes:**
- Trace width: 0.1 mm (4 mil) standard
- Trace spacing: 0.1 mm (4 mil) standard
- Via drill: 0.15 mm (6 mil) standard
- Annular ring: 0.05 mm (2 mil) minimum

**Component Spacing:**
- Adjacent components: 0.25 mm minimum
- Component to board edge: 0.5 mm minimum
- Component to via: 0.15 mm minimum
- Fiducials: 3-5 per board, 1 mm copper circle

### Assembly Considerations
**Solder Paste Design:**
- Stencil thickness: 0.1-0.15 mm typical
- Aperture ratio: >0.66 for good paste release
- Fine-pitch components: reduce aperture by 10-20%
- Via-in-pad: requires via filling for assembly

**Pick and Place Optimization:**
- Consistent component orientation
- Adequate clearance for placement tools
- Test points for automated testing
- Panel design for manufacturing efficiency

## Signal Integrity Analysis

### Critical Timing Constraints
**Setup/Hold Time Margins:**
- Clock traces: length match within ±0.1 mm
- Data buses: length match within ±2 mm
- Critical timing paths: simulate for verification
- Account for via delays and crosstalk

**Impedance Control:**
- Target: 50Ω ±10% single-ended
- Target: 100Ω ±10% differential  
- Verify with impedance calculators
- Account for manufacturing tolerances

### Electromagnetic Compatibility (EMC)

**EMI Reduction Techniques:**
- Solid reference planes for return currents
- Minimize loop areas in circuits
- Use differential signaling where possible
- Add EMI filters at cable connections
- Shield sensitive analog circuits

**Common Mode Noise Control:**
- Maintain consistent ground references
- Use common mode chokes for cable connections
- Isolate digital and analog grounds properly
- Control ground current flow paths

## Design Verification Checklist

### Pre-Layout Verification
- [ ] Schematic review and simulation complete
- [ ] Component selection verified for availability
- [ ] Thermal analysis performed
- [ ] Power integrity analysis complete
- [ ] Signal integrity requirements defined

### Post-Layout Verification
- [ ] DRC (Design Rule Check) violations resolved
- [ ] Length matching requirements met
- [ ] Via count minimized
- [ ] Thermal vias placed under hot components
- [ ] Test points accessible
- [ ] Assembly clearances verified
- [ ] EMC guidelines followed
- [ ] Manufacturing review complete

### Final Design Review
- [ ] 3D visualization reviewed
- [ ] Pick and place simulation passed
- [ ] Mechanical constraints verified
- [ ] Cost targets met
- [ ] Schedule requirements satisfied

## Advanced Techniques for 2024

### HDI (High Density Interconnect)
- Microvias for ultra-fine pitch components
- Via-in-pad for maximum routing density
- Sequential lamination processes
- Advanced substrate materials

### Flexible and Rigid-Flex PCBs
- Dynamic flex considerations
- Conductor protection in bend areas
- Component placement restrictions
- Multilayer flex construction

### Embedded Component Technology
- Passive components embedded in substrate
- Reduced board thickness and weight
- Improved electrical performance
- Higher reliability in harsh environments

## Integration with FreeCAD MCP Environment

### Python Integration Points
- Automated DRC checking
- Component placement optimization
- Thermal via array generation
- Length matching algorithms
- BOM generation and validation

### Validation Workflows
- Real-time impedance calculations
- Thermal simulation integration
- Signal integrity pre-checks
- Manufacturing constraint validation
- Cost optimization algorithms

---

*"There's a way to do it better - find it."* - Thomas Edison

This comprehensive design rules document serves as the foundation for systematic PCB design excellence, combining time-tested principles with cutting-edge 2024 technology requirements.