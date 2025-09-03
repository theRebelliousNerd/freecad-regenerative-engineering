## Real-Time Constraint Monitoring

### Live Validation During Design
```python
class RealTimeConstraintMonitor:
    """
    Monitor and validate constraints in real-time during design
    """
    
    def __init__(self, document):
        self.doc = document
        self.validators = {
            'sketch': SketchConstraintValidator,
            'assembly': AssemblyConstraintValidator,
            'parametric': ParametricValidator,
            'tolerance': ToleranceValidator
        }
        self.history = []
        
    def on_object_change(self, obj, prop):
        """
        Triggered when any object property changes
        """
        # Determine what type of validation is needed
        if obj.TypeId == 'Sketcher::SketchObject':
            validator = self.validators['sketch'](obj)
            result = validator.verify_all_constraints()
        elif obj.TypeId.startswith('Assembly'):
            validator = self.validators['assembly'](self.doc.Assembly)
            result = validator.verify_all_constraints()
        else:
            return
        
        # Check for issues
        if result.get('failed', 0) > 0:
            self.show_warning(obj, result)
        
        # Log to history
        self.history.append({
            'timestamp': datetime.now(),
            'object': obj.Name,
            'property': prop,
            'validation_result': result
        })
    
    def show_warning(self, obj, result):
        """
        Display warning for constraint violations
        """
        failed_constraints = [
            c for c in result['details'] 
            if not c.get('satisfied', True)
        ]
        
        message = f"Constraint violation in {obj.Name}:\n"
        for constraint in failed_constraints[:3]:  # Show first 3
            message += f"- {constraint['type']}: "
            if 'error' in constraint:
                message += f"Error = {constraint['error']:.4f}\n"
            else:
                message += "Failed\n"
        
        if len(failed_constraints) > 3:
            message += f"... and {len(failed_constraints) - 3} more"
        
        FreeCAD.Console.PrintWarning(message + "\n")
    
    def generate_validation_report(self):
        """
        Generate comprehensive validation report
        """
        report = {
            'document': self.doc.Name,
            'timestamp': datetime.now(),
            'validation_summary': {}
        }
        
        # Validate sketches
        sketch_results = []
        for obj in self.doc.Objects:
            if obj.TypeId == 'Sketcher::SketchObject':
                validator = self.validators['sketch'](obj)
                result = validator.verify_all_constraints()
                result['sketch'] = obj.Name
                sketch_results.append(result)
        
        report['validation_summary']['sketches'] = sketch_results
        
        # Validate assembly
        if hasattr(self.doc, 'Assembly'):
            validator = self.validators['assembly'](self.doc.Assembly)
            report['validation_summary']['assembly'] = validator.verify_all_constraints()
        
        # Validate parametric relationships
        param_validator = self.validators['parametric'](self.doc)
        report['validation_summary']['parametric'] = {
            'circular_dependencies': param_validator.verify_no_circular_dependencies(),
            'parameter_bounds': param_validator.verify_parameter_bounds()
        }
        
        # Overall status
        all_valid = all(
            all(s.get('satisfied', 0) == s.get('total_constraints', 1) 
                for s in sketch_results)
        )
        
        report['overall_status'] = 'VALID' if all_valid else 'ISSUES FOUND'
        
        return report
```