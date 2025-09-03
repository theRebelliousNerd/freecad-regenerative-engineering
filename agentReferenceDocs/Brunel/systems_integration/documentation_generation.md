## Documentation Generation

### Assembly Drawing Creation

```python
def generate_assembly_drawings(assembly):
    """
    Create technical drawings following Brunel's documentation standards
    """
    import TechDraw
    
    # Create drawing page
    page = FreeCAD.ActiveDocument.addObject(
        'TechDraw::DrawPage',
        'AssemblyDrawing'
    )
    page.Template = 'A3_Landscape_ISO7200TD.svg'
    
    # Add orthographic views
    views = {
        'front': (0, 0, 1),
        'top': (0, 1, 0),
        'side': (1, 0, 0),
        'isometric': (1, 1, 1)
    }
    
    for name, direction in views.items():
        view = FreeCAD.ActiveDocument.addObject(
            'TechDraw::DrawViewPart',
            f'View_{name}'
        )
        view.Source = assembly
        view.Direction = direction
        view.Scale = 0.1
        page.addView(view)
    
    # Add section view
    section = FreeCAD.ActiveDocument.addObject(
        'TechDraw::DrawViewSection',
        'SectionView'
    )
    section.BaseView = view
    section.SectionDirection = (0, 1, 0)
    section.SectionOrigin = (0, 0, 0)
    
    # Add dimensions
    add_critical_dimensions(page, assembly)
    
    # Add BOM table
    bom = generate_bom_table(assembly)
    page.addView(bom)
    
    # Add notes
    notes = [
        "1. All dimensions in mm unless noted",
        "2. Break sharp edges 0.5mm × 45°",
        f"3. Safety factor: {assembly.SafetyFactor}",
        "4. Assembly sequence: See separate document"
    ]
    add_notes_to_drawing(page, notes)
    
    return page
```

### Bill of Materials Generation

```python
def generate_bom(assembly):
    """
    Create BOM following Brunel's standardization approach
    """
    import csv
    
    bom = []
    standard_parts = load_standard_parts_database()
    
    for part in assembly.Parts:
        entry = {
            'item': part.Label,
            'description': part.Description,
            'material': part.Material,
            'quantity': count_instances(part, assembly),
            'dimensions': get_key_dimensions(part),
            'weight': part.Shape.Mass,
            'standard': is_standard_part(part, standard_parts),
            'source': get_supplier(part) if is_standard_part else 'Fabricate',
            'cost_estimate': calculate_cost(part)
        }
        bom.append(entry)
    
    # Sort by assembly order
    bom.sort(key=lambda x: x['assembly_sequence'])
    
    # Write to CSV
    with open('assembly_bom.csv', 'w', newline='') as file:
        writer = csv.DictWriter(file, fieldnames=entry.keys())
        writer.writeheader()
        writer.writerows(bom)
    
    # Generate summary
    summary = {
        'total_parts': len(bom),
        'unique_parts': len(set(p['item'] for p in bom)),
        'standard_parts': sum(1 for p in bom if p['standard']),
        'total_weight': sum(p['weight'] * p['quantity'] for p in bom),
        'estimated_cost': sum(p['cost_estimate'] for p in bom)
    }
    
    return bom, summary
```
