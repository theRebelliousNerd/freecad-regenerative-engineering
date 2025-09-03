# Component Verification Protocol

## Critical Importance for Enclosure Design

**NEVER** accept "estimated" or "typical" dimensions for components in enclosure design. Every component must be physically verified or documented through official datasheets before any CAD work begins.

## Component Verification Hierarchy

### Confidence Levels

1. **MEASURED (100% confidence)**: Physical measurement with calipers/rulers
2. **DATASHEET (95% confidence)**: Official manufacturer specifications  
3. **CALCULATED (90% confidence)**: Derived from other verified measurements
4. **ESTIMATED (0% confidence)**: REJECT for all critical dimensions

### Critical Component Database Structure

```yaml
component_database:
  pcb_main:
    dimensions:
      width: 
        value: 80.000
        tolerance: ±0.050
        units: mm
        confidence: MEASURED
        verification_date: "2024-01-15"
        measured_by: "technician_id"
      length:
        value: 120.000
        tolerance: ±0.050
        units: mm
        confidence: DATASHEET
        source: "manufacturer_spec_sheet_v2.1"
    
  relay_4ch:
    dimensions:
      width:
        value: 129.000
        tolerance: ±0.500
        units: mm
        confidence: MEASURED
        notes: "Actual measurement differs from initial estimate of 75mm"
      height_above_pcb:
        value: 15.500
        tolerance: ±0.200
        units: mm
        confidence: MEASURED
        stack_up: ["relay_body: 12.5mm", "socket: 3.0mm"]
```

## Stack-Up Verification Requirements

### Vertical Stack Analysis

For every component, verify the complete vertical stack:

```python
def verify_component_stack(component):
    """
    Verify complete vertical stack including all mounting hardware
    """
    stack_components = [
        component.base_height,
        component.mounting_hardware_height,
        component.connected_components_height,
        component.cable_clearance_above
    ]
    
    total_height = sum(stack_components)
    
    return {
        'total_height': total_height,
        'breakdown': stack_components,
        'critical_clearances': component.clearance_requirements,
        'confidence_level': min([c.confidence for c in stack_components])
    }
```

### Required Measurements

**Base Component**:
- Length, width, height (body dimensions)
- Mounting hole positions and diameters
- Pin/connector positions and orientations

**Mounting Hardware**:
- Standoff heights (if used)
- Screw head clearance
- Washer thicknesses

**Connected Components**:
- Heat sink dimensions (if applicable)
- Connector heights above component body
- Cable strain relief requirements

**Cable Clearances**:
- Minimum bend radius for each cable type
- Connector insertion/removal clearance
- Service access requirements

## Component Verification Checklist

### Pre-CAD Verification Gate

Before ANY geometry creation, verify:

- [ ] Physical component available or ordered
- [ ] Every critical dimension measured or from datasheet  
- [ ] Mounting patterns documented with hole positions
- [ ] Connector orientations and heights verified
- [ ] Cable clearance requirements calculated
- [ ] Assembly sequence validated on paper
- [ ] No dimensions marked as "about" or "approximately"
- [ ] All measurements have explicit tolerances
- [ ] Confidence levels assigned to all dimensions

### Measurement Protocol

```python
def create_component_record(component_name):
    """
    Standard protocol for documenting component verification
    """
    record = {
        'component_id': component_name,
        'verification_date': datetime.now(),
        'physical_sample': {
            'available': True,  # Must be True for MEASURED confidence
            'part_number': '',
            'manufacturer': '',
            'revision': ''
        },
        'dimensions': {},
        'mounting': {},
        'electrical': {},
        'thermal': {},
        'notes': [],
        'photos': []  # Reference to measurement photos
    }
    
    return record
```

## Failure Mode Prevention

### The PDU Media Player Lesson

**What Went Wrong**:
- Started CAD with "about 80mm" PCB dimension
- Actual dimension was 114mm × 86.5mm  
- Relay was 129mm × 72mm (not estimated 75mm × 55mm)
- Terminal block height made 75mm enclosure impossible
- Complete redesign required after components arrived

**Prevention Protocol**:
1. **Physical First**: Always have physical components before starting CAD
2. **Measure Everything**: Every dimension that affects fit
3. **Stack Analysis**: Include all mounting hardware and clearances
4. **Paper Mockup**: Validate assembly sequence before CAD
5. **Tolerance Budget**: Account for all tolerance accumulations

## Integration with Axiom System

Component verification feeds directly into axiom establishment:

```yaml
# From component verification to axioms
verified_components: component_database.yaml
axioms:
  - id: DIM-001
    source: verified_components.pcb_main.width
    value: 80.000
    tolerance: ±0.050
    confidence: MEASURED
    
  - id: CON-001  
    source: verified_components.relay_4ch.clearance_requirements
    type: minimum_clearance
    value: 2.500
    reason: "Relay heat dissipation and service access"
```

## Continuous Verification

Even after initial verification, maintain vigilance:

- **Revision Control**: Track component revision changes
- **Supplier Changes**: Verify dimensions if supplier changes
- **Tolerance Drift**: Monitor actual delivered parts
- **Field Feedback**: Update database based on assembly experience

The cost of thorough component verification is minimal compared to the cost of redesign after discovering dimensional conflicts in physical assemblies.