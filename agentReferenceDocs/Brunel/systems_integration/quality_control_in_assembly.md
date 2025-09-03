## Quality Control in Assembly

### Dimensional Control

```
Survey Points:
- Establish baseline before assembly
- Check after each major operation
- Maximum deviation: L/1000
- Corrective action if exceeded

Example - Box Tunnel:
- Length: 2937m
- Allowable error: 3m
- Actual error: 0.05m (2 inches)
- Method: Theodolite + steel tape
```

### Joint Quality Verification

```python
def verify_joint_quality(joint):
    """
    Check assembled joint meets specifications
    """
    checks = {
        'alignment': measure_alignment(joint) < 1.0,  # mm
        'gap': measure_gap(joint) < 0.5,  # mm
        'torque': verify_torque(joint.bolts) == spec_torque,
        'surface': check_mating_surfaces(joint) == 'clean',
        'sealant': verify_sealant_application(joint)
    }
    
    joint.quality_score = sum(checks.values()) / len(checks)
    return joint.quality_score > 0.95
```
