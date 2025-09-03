# Orientation Optimization

Optimizing the orientation of a part is a critical step in the DFAM process. The optimal orientation will depend on the specific requirements of the part, but it is often a trade-off between strength, surface quality, print time, and cost.

## Automated Orientation Analysis

It is possible to automate the process of finding the optimal orientation for a part using a Python script.

```python
# Print Orientation Optimizer
import FreeCAD as App
import numpy as np
from scipy.optimize import minimize

class OrientationOptimizer:
    def __init__(self, part):
        self.part = part
        self.orientations = self.generate_orientations()
        
    def generate_orientations(self):
        """Generate candidate orientations"""
        angles = []
        for x in [0, 45, 90]:
            for y in [0, 45, 90]:
                for z in [0, 45, 90]:
                    angles.append((x, y, z))
        return angles
    
    def evaluate_orientation(self, angles):
        """Score orientation based on multiple criteria"""
        x_rot, y_rot, z_rot = angles
        
        # Rotate part
        self.part.Placement.Rotation = App.Rotation(x_rot, y_rot, z_rot)
        App.ActiveDocument.recompute()
        
        # Calculate metrics
        support_volume = self.calculate_support_volume()
        z_height = self.part.Shape.BoundBox.ZLength
        bed_contact = self.calculate_bed_contact_area()
        
        # Weighted score (lower is better)
        score = (support_volume * 0.5 + 
                z_height * 0.3 + 
                (100 - bed_contact) * 0.2)
        
        return score
    
    def optimize(self):
        """Find optimal orientation"""
        best_score = float('inf')
        best_orientation = None
        
        for orientation in self.orientations:
            score = self.evaluate_orientation(orientation)
            if score < best_score:
                best_score = score
                best_orientation = orientation
        
        return best_orientation, best_score
```
