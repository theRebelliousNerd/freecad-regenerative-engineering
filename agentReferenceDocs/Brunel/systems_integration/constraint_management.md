## Constraint Management

### Kinematic Constraint Strategy

```python
def apply_kinematic_constraints(assembly):
    """
    Apply minimum necessary constraints (Brunel's efficiency principle)
    Avoid over-constraining
    """
    # Calculate degrees of freedom
    num_parts = len(assembly.Parts)
    total_dof = num_parts * 6  # 6 DOF per part
    
    constraints_needed = total_dof - 6  # 6 DOF for fixed assembly
    
    # Priority order for constraints (most restrictive first)
    constraint_priority = [
        'Fixed',      # Removes 6 DOF
        'Coincident', # Removes 3 DOF
        'Parallel',   # Removes 2 DOF
        'Distance',   # Removes 1 DOF
        'Angle'       # Removes 1 DOF
    ]
    
    applied_constraints = []
    remaining_dof = total_dof - 6
    
    for part in assembly.Parts[1:]:  # First part is fixed
        if remaining_dof > 0:
            constraint = determine_best_constraint(part, applied_constraints)
            assembly.addConstraint(constraint)
            applied_constraints.append(constraint)
            remaining_dof -= constraint.dof_removed
    
    return applied_constraints
```

### Load Transfer Constraints

```python
def create_load_transfer_constraint(part1, part2, load_type):
    """
    Define constraints that properly transfer loads
    Like Brunel's chain-to-deck connections on bridges
    """
    import Assembly
    
    if load_type == 'compression':
        # Face-to-face contact
        constraint = Assembly.ConstraintCoincident(
            part1.Face,
            part2.Face,
            offset=0
        )
        constraint.Properties['TransferCompression'] = True
        
    elif load_type == 'tension':
        # Pinned or bolted connection
        constraint = Assembly.ConstraintCoaxial(
            part1.Cylinder,
            part2.Cylinder
        )
        constraint.Properties['TransferTension'] = True
        
    elif load_type == 'moment':
        # Rigid connection
        constraints = [
            Assembly.ConstraintCoincident(part1.Face, part2.Face),
            Assembly.ConstraintParallel(part1.Edge1, part2.Edge1),
            Assembly.ConstraintParallel(part1.Edge2, part2.Edge2)
        ]
        for c in constraints:
            c.Properties['TransferMoment'] = True
    
    return constraint
```
