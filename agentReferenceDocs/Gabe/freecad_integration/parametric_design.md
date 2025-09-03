# Parametric Design for Mass Customization

Parametric design is a powerful feature in FreeCAD that allows you to create flexible designs that can be easily modified to create different variations of a product. This is particularly useful for mass customization, where you need to produce a large number of unique products.

## Design Table Integration

One way to manage parametric designs is to use a spreadsheet to define the parameters for each variant. This is known as design table integration.

```python
# Parametric Product Family Generator
import FreeCAD as App
import Spreadsheet

class ProductVariantGenerator:
    def __init__(self, base_model, spreadsheet_name):
        self.base = base_model
        self.sheet = App.ActiveDocument.getObject(spreadsheet_name)
        
    def generate_variant(self, row):
        """Generate product variant from spreadsheet row"""
        # Read parameters from spreadsheet
        length = float(self.sheet.get(f'A{row}'))
        width = float(self.sheet.get(f'B{row}'))
        height = float(self.sheet.get(f'C{row}'))
        
        # Update model parameters
        self.base.Length = length
        self.base.Width = width
        self.base.Height = height
        
        # Recompute and export
        App.ActiveDocument.recompute()
        return self.export_stl(f'variant_{row}')
    
    def batch_generate(self, start_row, end_row):
        """Generate multiple variants"""
        variants = []
        for row in range(start_row, end_row + 1):
            variants.append(self.generate_variant(row))
        return variants
```
