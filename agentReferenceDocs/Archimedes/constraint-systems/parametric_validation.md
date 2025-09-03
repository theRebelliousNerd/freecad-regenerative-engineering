## Parametric Validation

### Parameter Dependency Verification
```python
class ParametricValidator:
    """
    Validate parametric relationships in FreeCAD models
    """
    
    def __init__(self, document):
        self.doc = document
        self.parameters = self.extract_parameters()
        self.expressions = self.extract_expressions()
    
    def build_dependency_graph(self):
        """
        Build graph of parameter dependencies
        """
        import networkx as nx
        
        graph = nx.DiGraph()
        
        for param_name, param_value in self.parameters.items():
            graph.add_node(param_name, value=param_value)
        
        for expr_obj, expr_prop, expression in self.expressions:
            # Parse expression to find dependencies
            dependencies = self.parse_expression_dependencies(expression)
            
            target = f"{expr_obj}.{expr_prop}"
            graph.add_node(target, expression=expression)
            
            for dep in dependencies:
                graph.add_edge(dep, target)
        
        return graph
    
    def verify_no_circular_dependencies(self):
        """
        Check for circular parameter dependencies
        """
        graph = self.build_dependency_graph()
        
        try:
            # Topological sort will fail if cycles exist
            nx.topological_sort(graph)
            return {
                'has_cycles': False,
                'status': 'Valid parametric model'
            }
        except nx.NetworkXError:
            # Find cycles
            cycles = list(nx.simple_cycles(graph))
            return {
                'has_cycles': True,
                'cycles': cycles,
                'status': 'Circular dependency detected'
            }
    
    def verify_parameter_bounds(self):
        """
        Verify all parameters stay within valid bounds
        """
        results = []
        
        for param_name, param_value in self.parameters.items():
            # Get bounds if defined
            bounds = self.get_parameter_bounds(param_name)
            
            if bounds:
                min_val, max_val = bounds
                
                if param_value < min_val or param_value > max_val:
                    results.append({
                        'parameter': param_name,
                        'value': param_value,
                        'bounds': bounds,
                        'valid': False,
                        'error': 'Out of bounds'
                    })
                else:
                    margin_low = param_value - min_val
                    margin_high = max_val - param_value
                    
                    results.append({
                        'parameter': param_name,
                        'value': param_value,
                        'bounds': bounds,
                        'valid': True,
                        'margin_low': margin_low,
                        'margin_high': margin_high
                    })
        
        return {
            'parameters_checked': len(results),
            'valid': all(r['valid'] for r in results),
            'details': results
        }
    
    def sensitivity_analysis(self, target_parameter):
        """
        Analyze sensitivity of target to input parameters
        """
        sensitivities = {}
        
        base_value = self.evaluate_parameter(target_parameter)
        
        for param_name in self.parameters:
            if param_name == target_parameter:
                continue
            
            # Perturb parameter
            original = self.parameters[param_name]
            delta = original * 0.01 if original != 0 else 0.01
            
            self.parameters[param_name] = original + delta
            perturbed_value = self.evaluate_parameter(target_parameter)
            
            # Calculate sensitivity
            sensitivity = (perturbed_value - base_value) / delta
            
            sensitivities[param_name] = {
                'sensitivity': sensitivity,
                'relative_sensitivity': sensitivity * original / base_value if base_value != 0 else 0
            }
            
            # Restore original value
            self.parameters[param_name] = original
        
        return sensitivities
```
