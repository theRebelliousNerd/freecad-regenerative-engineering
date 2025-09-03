## Structural Analysis Integration

### Load Path Definition in FreeCAD

```python
def define_load_paths(assembly):
    """
    Map load paths through FreeCAD assembly
    Following Brunel's complete path principle
    """
    import FreeCAD
    import FemGui
    
    # 1. Identify load application points
    load_points = []
    for obj in assembly.Objects:
        if hasattr(obj, 'LoadMagnitude'):
            load_points.append({
                'location': obj.Placement.Base,
                'magnitude': obj.LoadMagnitude,
                'direction': obj.LoadDirection
            })
    
    # 2. Trace through constraints
    load_paths = []
    for load in load_points:
        path = trace_load_to_ground(load, assembly.Constraints)
        load_paths.append(path)
    
    # 3. Identify critical members
    critical_members = find_max_stress_members(load_paths)
    
    # 4. Calculate safety factors
    for member in critical_members:
        member.FOS = calculate_safety_factor(member)
    
    return load_paths, critical_members
```

### FEM Validation Workflow

```python
def brunel_fem_validation(assembly):
    """
    Systematic FEM validation following Brunel's testing philosophy
    """
    # 1. Convert assembly to FEM mesh
    import ObjectsFem
    
    analysis = ObjectsFem.makeAnalysis(FreeCAD.ActiveDocument)
    
    # 2. Define materials (like Brunel's wrought iron specs)
    material = ObjectsFem.makeMaterialSolid(FreeCAD.ActiveDocument)
    material.Material = {
        'Name': 'Structural Steel',
        'YoungsModulus': '210 GPa',
        'YieldStrength': '250 MPa',
        'UltimateTensileStrength': '400 MPa',
        'PoissonRatio': '0.3'
    }
    
    # 3. Apply constraints and loads
    fixed = ObjectsFem.makeConstraintFixed(FreeCAD.ActiveDocument)
    fixed.References = assembly.FixedFaces
    
    force = ObjectsFem.makeConstraintForce(FreeCAD.ActiveDocument)
    force.Force = 1000  # N
    force.Direction = (0, 0, -1)
    force.References = assembly.LoadFaces
    
    # 4. Mesh generation
    mesh = ObjectsFem.makeMeshGmsh(FreeCAD.ActiveDocument)
    mesh.CharacteristicLengthMax = 10  # mm
    mesh.create_mesh()
    
    # 5. Solve
    solver = ObjectsFem.makeSolverCalculixCcx(FreeCAD.ActiveDocument)
    solver.GeometricalNonlinearity = 'linear'
    solver.ThermoMechSteadyState = False
    solver.MatrixSolverType = 'default'
    
    # 6. Run analysis
    from femtools import ccxtools
    fea = ccxtools.FemToolsCcx(analysis, solver)
    fea.run()
    
    # 7. Validate results against requirements
    results = validate_against_requirements(fea.results)
    
    return results
```
