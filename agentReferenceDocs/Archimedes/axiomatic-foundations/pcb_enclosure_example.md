# Practical Application: PCB Enclosure Example

## Initial Requirements (Vague)
- "Board is about 80mm wide"
- "Needs some clearance"
- "Wall should be strong enough"

## Transformed to Axioms
```yaml
axioms:
  dimensional:
    - id: DIM-001
      param: pcb_width
      value: 80.000
      tolerance: ±0.050
      units: mm
      
    - id: DIM-002
      param: pcb_length
      value: 120.000
      tolerance: ±0.050
      units: mm
      
  constraints:
    - id: CON-001
      type: minimum_clearance
      value: 1.500
      units: mm
      applies_to: [pcb, enclosure_walls]
      
    - id: CON-002
      type: minimum_thickness
      value: 2.000
      units: mm
      applies_to: enclosure_walls
      
  material:
    - id: MAT-001
      property: tensile_strength
      min_value: 30.0
      units: MPa
      material: ABS
```

## Derived Dimensions
```python
# From axioms, derive all other dimensions
enclosure_internal_width = pcb_width + 2 * clearance
enclosure_external_width = enclosure_internal_width + 2 * wall_thickness

# Result with propagated tolerances
enclosure_external_width = 85.000 ± 0.054 mm
```
