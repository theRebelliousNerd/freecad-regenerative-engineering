## Load Path Verification

### Physical Testing
Brunel's approach to validation:

1. **Component Testing**: Individual members tested to failure
2. **Assembly Testing**: Subassemblies loaded to design + safety factor
3. **Proof Loading**: Complete structure tested at 1.5× design load

Example: Clifton Bridge chains tested to 10 tons/in² (design: 5.5 tons/in²)

### Modern FEM Validation

```python
def verify_load_path(model, applied_loads):
    """
    FreeCAD FEM verification process
    """
    # 1. Apply loads
    fem_model.add_loads(applied_loads)
    
    # 2. Solve
    results = fem_solver.solve()
    
    # 3. Extract stress along load path
    path_stress = []
    for element in load_path_elements:
        stress = results.get_stress(element)
        path_stress.append(stress)
    
    # 4. Verify continuity
    check_force_balance(path_stress)
    
    # 5. Check against allowables
    for stress in path_stress:
        assert stress < allowable_stress
    
    return results
```
