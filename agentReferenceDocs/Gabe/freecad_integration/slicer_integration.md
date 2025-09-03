# Slicer Integration

Integrating FreeCAD with your slicer software is a key step in automating the production process. This can be achieved by using Python scripts to control the slicer from within FreeCAD.

## Direct Slicer Control

```python
# FreeCAD to Slicer Pipeline
class SlicerIntegration:
    def __init__(self, slicer_type='cura'):
        self.slicer = slicer_type
        self.profiles = self.load_profiles()
        
    def slice_model(self, stl_path, profile='production'):
        """Slice model with production settings"""
        if self.slicer == 'cura':
            return self.slice_with_cura(stl_path, profile)
        elif self.slicer == 'prusaslicer':
            return self.slice_with_prusa(stl_path, profile)
    
    def slice_with_cura(self, stl_path, profile):
        """Use CuraEngine for slicing"""
        cmd = [
            'CuraEngine',
            'slice',
            '-j', self.profiles[profile],
            '-l', stl_path,
            '-o', stl_path.replace('.stl', '.gcode')
        ]
        subprocess.run(cmd)
        return stl_path.replace('.stl', '.gcode')
    
    def estimate_print_metrics(self, gcode_path):
        """Extract time and material estimates"""
        with open(gcode_path, 'r') as f:
            for line in f:
                if 'TIME:' in line:
                    time_estimate = float(line.split(':')[1])
                if 'Filament used:' in line:
                    material_estimate = float(line.split(':')[1])
        
        return {
            'print_time': time_estimate,
            'material_usage': material_estimate,
            'cost_estimate': material_estimate * 0.02  # $20/kg
        }
```
