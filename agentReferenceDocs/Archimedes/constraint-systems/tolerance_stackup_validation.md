## Tolerance Stack-Up Validation

### Tolerance Chain Analysis
```python
class ToleranceValidator:
    """
    Validate tolerance stack-ups in FreeCAD assemblies
    """
    
    def __init__(self, assembly):
        self.assembly = assembly
        self.tolerance_chain = []
    
    def build_tolerance_chain(self, start_face, end_face):
        """
        Build tolerance chain between two faces
        """
        # Find path through assembly
        path = self.find_assembly_path(start_face, end_face)
        
        chain = []
        for i in range(len(path) - 1):
            part1 = path[i]
            part2 = path[i + 1]
            
            # Find connecting dimension
            dimension = self.find_connecting_dimension(part1, part2)
            
            chain.append({
                'from': part1,
                'to': part2,
                'nominal': dimension['nominal'],
                'tolerance_plus': dimension['tolerance_plus'],
                'tolerance_minus': dimension['tolerance_minus']
            })
        
        return chain
    
    def worst_case_analysis(self, chain):
        """
        Perform worst-case tolerance analysis
        """
        nominal_sum = sum(link['nominal'] for link in chain)
        
        # Worst case: all tolerances add up
        max_sum = sum(
            link['nominal'] + link['tolerance_plus'] 
            for link in chain
        )
        min_sum = sum(
            link['nominal'] - link['tolerance_minus'] 
            for link in chain
        )
        
        return {
            'method': 'Worst Case',
            'nominal': nominal_sum,
            'maximum': max_sum,
            'minimum': min_sum,
            'tolerance_plus': max_sum - nominal_sum,
            'tolerance_minus': nominal_sum - min_sum
        }
    
    def statistical_analysis(self, chain, confidence=0.9973):
        """
        Perform statistical tolerance analysis (RSS)
        """
        import numpy as np
        from scipy import stats
        
        nominal_sum = sum(link['nominal'] for link in chain)
        
        # Root Sum Squares method
        variance_sum = sum(
            ((link['tolerance_plus'] + link['tolerance_minus']) / 6) ** 2
            for link in chain
        )
        
        std_dev = np.sqrt(variance_sum)
        
        # Confidence interval
        z_score = stats.norm.ppf((1 + confidence) / 2)
        
        return {
            'method': 'Statistical (RSS)',
            'nominal': nominal_sum,
            'std_deviation': std_dev,
            'confidence': confidence,
            'confidence_interval': (
                nominal_sum - z_score * std_dev,
                nominal_sum + z_score * std_dev
            ),
            '3_sigma_range': (
                nominal_sum - 3 * std_dev,
                nominal_sum + 3 * std_dev
            )
        }
    
    def monte_carlo_analysis(self, chain, num_samples=10000):
        """
        Perform Monte Carlo tolerance analysis
        """
        import numpy as np
        
        results = []
        
        for _ in range(num_samples):
            sample_sum = 0
            
            for link in chain:
                # Assume normal distribution
                mean = link['nominal']
                # 3-sigma = tolerance
                sigma = (link['tolerance_plus'] + link['tolerance_minus']) / 6
                
                sample = np.random.normal(mean, sigma)
                sample_sum += sample
            
            results.append(sample_sum)
        
        results = np.array(results)
        
        return {
            'method': 'Monte Carlo',
            'num_samples': num_samples,
            'mean': np.mean(results),
            'std_deviation': np.std(results),
            'minimum': np.min(results),
            'maximum': np.max(results),
            'percentiles': {
                '1%': np.percentile(results, 1),
                '5%': np.percentile(results, 5),
                '50%': np.percentile(results, 50),
                '95%': np.percentile(results, 95),
                '99%': np.percentile(results, 99)
            }
        }
```
