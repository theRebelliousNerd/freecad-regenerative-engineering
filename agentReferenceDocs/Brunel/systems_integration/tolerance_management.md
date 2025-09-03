## Tolerance Management

### Fit Classifications

```
Clearance Fit:
│  ████  │  Shaft smaller than hole
│        │  Allows movement/assembly

Transition Fit:
│████████│  Close tolerance
│████████│  Locate parts precisely

Interference Fit:
████████    Shaft larger than hole
│██████│    Requires force/heat to assemble
```

### Tolerance Stack-Up

```python
def calculate_tolerance_stack(parts):
    """
    Calculate cumulative tolerance in assembly
    """
    # Statistical method (RSS - Root Sum Square)
    total_tolerance = sqrt(sum(t**2 for t in part_tolerances))
    
    # Worst case method
    worst_case = sum(part_tolerances)
    
    # Brunel's approach: 2× statistical
    design_clearance = 2 * total_tolerance
    
    return {
        'statistical': total_tolerance,
        'worst_case': worst_case,
        'design': design_clearance
    }
```

### Field Adjustments

Royal Albert Bridge assembly:
```
Adjustment Mechanisms:
1. Shim plates: 1-10mm compensation
2. Slotted holes: ±5mm lateral adjustment
3. Turnbuckles: Length adjustment in chains
4. Wedges: Vertical alignment
5. Jacking points: Major positioning
```
