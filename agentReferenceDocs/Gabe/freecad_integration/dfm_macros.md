# DFAM Macros and Plugins for FreeCAD

This guide covers the use of Python macros and plugins to automate Design for Additive Manufacturing (DFAM) compliance checking in FreeCAD.

## Automated Design Validation

### Python Script for DFM Checking
```python
# DFAM Compliance Checker for FreeCAD
import FreeCAD as App
import Part
import Mesh

class DFAMValidator:
    def __init__(self, document):
        self.doc = document
        self.violations = []
        self.MIN_WALL_THICKNESS = 1.0  # mm
        self.MAX_OVERHANG_ANGLE = 45   # degrees
        self.MIN_FEATURE_SIZE = 3.0    # mm
        
    def check_wall_thickness(self, shape):
        """Check minimum wall thickness compliance"""
        # Analyze shape for thin walls
        edges = shape.Edges
        for edge in edges:
            if edge.Length < self.MIN_WALL_THICKNESS:
                self.violations.append({
                    'type': 'WALL_THICKNESS',
                    'location': edge.CenterOfMass,
                    'value': edge.Length,
                    'requirement': self.MIN_WALL_THICKNESS
                })
    
    def check_overhangs(self, shape):
        """Identify overhangs exceeding 45 degrees"""
        faces = shape.Faces
        for face in faces:
            normal = face.normalAt(0.5, 0.5)
            angle = normal.getAngle(App.Vector(0, 0, 1))
            if angle > self.MAX_OVERHANG_ANGLE * (3.14159/180):
                self.violations.append({
                    'type': 'OVERHANG',
                    'location': face.CenterOfMass,
                    'angle': angle * (180/3.14159),
                    'requirement': self.MAX_OVERHANG_ANGLE
                })
    
    def generate_report(self):
        """Generate DFAM compliance report"""
        if not self.violations:
            return "PASS: Design is DFAM compliant"
        
        report = "DFAM VIOLATIONS DETECTED:\n"
        for v in self.violations:
            report += f"- {v['type']}: {v}\n"
        return report

# Usage example
validator = DFAMValidator(App.ActiveDocument)
for obj in App.ActiveDocument.Objects:
    if hasattr(obj, 'Shape'):
        validator.check_wall_thickness(obj.Shape)
        validator.check_overhangs(obj.Shape)
print(validator.generate_report())
```

### FreeCAD Plugin: FusedFilamentDesign

The FusedFilamentDesign plugin by Rahix adds critical DFAM features to FreeCAD.

**Installation**:
```bash
# Via FreeCAD Addon Manager
1. Tools → Addon Manager
2. Search "FusedFilamentDesign"
3. Install
4. Restart FreeCAD
```

**Key Features**:
- **Hole Wizard**: Automatic teardrop hole generation
- **Support-free geometries**: Built-in DFAM shapes
- **Chamfer automation**: Apply 45° chamfers automatically
- **Bridge optimizer**: Calculate optimal bridge parameters

```