## Calculating Load Distribution

### Method of Joints (Trusses)
```python
def analyze_joint(forces, angles):
    """
    Equilibrium at each joint:
    ΣFx = 0, ΣFy = 0
    """
    # For each joint
    sum_fx = sum(F * cos(θ) for F, θ in zip(forces, angles))
    sum_fy = sum(F * sin(θ) for F, θ in zip(forces, angles))
    
    assert abs(sum_fx) < tolerance
    assert abs(sum_fy) < tolerance
```

### Method of Sections
```python
def analyze_section(cut_members, loads, distances):
    """
    Cut through structure, analyze equilibrium
    ΣF = 0, ΣM = 0
    """
    # Take moments about convenient point
    moment_sum = sum(F * d for F, d in zip(loads, distances))
    
    # Solve for unknown member forces
    return solve_equilibrium(moment_sum)
```

### Finite Element Approach
```python
# Stiffness method
[K]{u} = {F}

where:
K = Global stiffness matrix
u = Displacement vector
F = Force vector

# Solve for displacements
u = K^(-1) * F

# Calculate stresses
σ = [D][B]{u}
where:
D = Material matrix
B = Strain-displacement matrix
```
