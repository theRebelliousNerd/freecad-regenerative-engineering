## Assembly Verification

### Interference Checking

```python
def check_assembly_interference(assembly):
    """
    Detect part collisions in assembly
    """
    parts = assembly.get_all_parts()
    collisions = []
    
    for i, part1 in enumerate(parts):
        for part2 in parts[i+1:]:
            if part1.Shape.common(part2.Shape).Volume > 0:
                collisions.append((part1.Name, part2.Name))
    
    return collisions
```

### Clearance Verification

```python
def verify_clearances(assembly, min_clearance=2.0):
    """
    Check minimum clearances maintained
    """
    clearance_violations = []
    
    for constraint in assembly.constraints:
        if constraint.type == 'Distance':
            if constraint.value < min_clearance:
                clearance_violations.append({
                    'parts': constraint.parts,
                    'clearance': constraint.value,
                    'required': min_clearance
                })
    
    return clearance_violations
```
