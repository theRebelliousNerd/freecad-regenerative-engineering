## Modern Assembly Methods

### FreeCAD Assembly Workbench

```python
# Assembly constraint types
def create_assembly_constraints():
    assembly = App.ActiveDocument.Assembly
    
    # Coincident - faces touch
    assembly.add_constraint(
        type='Coincident',
        part1='Base.Face1',
        part2='Top.Face2',
        offset=0
    )
    
    # Parallel - maintain orientation
    assembly.add_constraint(
        type='Parallel',
        part1='Rail1.Axis',
        part2='Rail2.Axis'
    )
    
    # Distance - fixed separation
    assembly.add_constraint(
        type='Distance',
        part1='Part1.Vertex1',
        part2='Part2.Vertex2',
        distance=100  # mm
    )
```

### Assembly Features in PartDesign

```python
# Pattern-based assembly
def create_pattern_assembly():
    # Linear pattern for repeated elements
    pattern = Part.make_linear_pattern(
        base_feature=bolt_hole,
        direction=Vector(1,0,0),
        length=500,
        count=10
    )
    
    # Polar pattern for circular assemblies
    circular = Part.make_polar_pattern(
        base_feature=support_rib,
        axis=Vector(0,0,1),
        angle=360,
        count=8
    )
    
    # Mirror for symmetric assemblies
    mirrored = Part.mirror_feature(
        base_feature=side_plate,
        plane='YZ'
    )
```
