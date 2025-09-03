## Assembly Validation

### Interference Detection

```python
def check_assembly_interference(assembly, clearance=2.0):
    """
    Detect part collisions and insufficient clearances
    Essential for Brunel's "buildable" requirement
    """
    import Part
    
    issues = []
    parts = assembly.Shape.Solids
    
    for i, part1 in enumerate(parts):
        for j, part2 in enumerate(parts[i+1:], i+1):
            # Check for interference
            common = part1.common(part2)
            if common.Volume > 0.001:  # Tolerance for numerical errors
                issues.append({
                    'type': 'interference',
                    'parts': (i, j),
                    'volume': common.Volume,
                    'severity': 'critical'
                })
            
            # Check minimum clearance
            distance = part1.distToShape(part2)[0]
            if distance < clearance and common.Volume == 0:
                issues.append({
                    'type': 'insufficient_clearance',
                    'parts': (i, j),
                    'distance': distance,
                    'required': clearance,
                    'severity': 'warning'
                })
    
    return issues
```

### Assembly Sequence Validation

```python
def validate_assembly_sequence(assembly, sequence):
    """
    Verify assembly can be built in specified order
    Like validating Thames Tunnel shield advance sequence
    """
    import FreeCAD
    from FreeCAD import Base
    
    # Start with empty assembly
    temp_assembly = FreeCAD.newDocument("TempAssembly")
    assembled_parts = []
    
    for step in sequence:
        part = assembly.getPart(step['part_name'])
        
        # Check if part can be inserted
        insertion_path = calculate_insertion_path(
            part,
            step['start_position'],
            step['end_position']
        )
        
        # Check for collisions along path
        collision = check_path_collision(
            insertion_path,
            assembled_parts
        )
        
        if collision:
            return {
                'valid': False,
                'failed_step': step,
                'reason': f"Collision with {collision}"
            }
        
        # Add part to temp assembly
        assembled_parts.append(part)
        
        # Apply constraints for this step
        for constraint in step['constraints']:
            if not can_apply_constraint(constraint, assembled_parts):
                return {
                    'valid': False,
                    'failed_step': step,
                    'reason': f"Cannot apply {constraint}"
                }
    
    return {'valid': True, 'sequence': sequence}
```
