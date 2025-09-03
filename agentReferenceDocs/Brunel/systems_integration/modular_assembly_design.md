## Modular Assembly Design

### Creating Standardized Interfaces

```python
def create_standard_interface(name, bolt_pattern):
    """
    Create Brunel-style standardized connection interface
    """
    import Part
    import PartDesign
    
    # Create base mounting plate
    plate = PartDesign.Body()
    sketch = plate.newObject('Sketcher::SketchObject', 'MountingPlate')
    
    # Standard bolt pattern (like Great Eastern's standardization)
    bolt_holes = []
    for i, position in enumerate(bolt_pattern):
        sketch.addGeometry(Part.Circle(
            App.Vector(position[0], position[1], 0),
            App.Vector(0, 0, 1),
            6  # M12 clearance hole
        ))
    
    # Add alignment features
    sketch.addGeometry(Part.Circle(
        App.Vector(0, 0, 0),
        App.Vector(0, 0, 1),
        5  # 10mm dowel pin
    ))
    
    # Pad to create 3D interface
    pad = plate.newObject('PartDesign::Pad', 'Interface')
    pad.Profile = sketch
    pad.Length = 10  # mm
    
    # Save as template
    FreeCAD.ActiveDocument.saveAs(f'StandardInterface_{name}.FCStd')
    
    return plate
```

### Assembly Pattern Generation

```python
def create_assembly_pattern(base_component, pattern_type, parameters):
    """
    Generate assembly patterns like Paddington Station's arches
    """
    import Draft
    
    if pattern_type == 'linear':
        # Like Box Tunnel's repeated sections
        array = Draft.makeArray(
            base_component,
            App.Vector(parameters['spacing'], 0, 0),
            App.Vector(0, 0, 0),
            parameters['count'],
            1
        )
        
    elif pattern_type == 'polar':
        # Like wheel spokes or radial structures
        array = Draft.makeArray(
            base_component,
            App.Vector(0, 0, 0),
            App.Vector(0, 0, 1),
            360 / parameters['count'],
            parameters['count']
        )
        
    elif pattern_type == 'grid':
        # Like Great Eastern's plate arrangement
        array = Draft.makeArray(
            base_component,
            App.Vector(parameters['x_spacing'], 0, 0),
            App.Vector(0, parameters['y_spacing'], 0),
            parameters['x_count'],
            parameters['y_count']
        )
    
    return array
```
