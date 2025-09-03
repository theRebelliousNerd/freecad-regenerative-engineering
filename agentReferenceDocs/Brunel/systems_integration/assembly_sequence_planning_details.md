## Assembly Sequence Planning

### Critical Operations Identification

```python
def identify_critical_assembly_ops(assembly_graph):
    """
    Find operations that cannot be parallelized
    """
    critical_path = []
    
    # Topological sort of assembly operations
    for operation in topological_sort(assembly_graph):
        predecessors = assembly_graph.predecessors(operation)
        
        earliest_start = max(
            pred.finish_time for pred in predecessors
        ) if predecessors else 0
        
        operation.start_time = earliest_start
        operation.finish_time = earliest_start + operation.duration
        
        if operation.is_critical():
            critical_path.append(operation)
    
    return critical_path
```

### Resource Allocation

```
Assembly Resource Matrix:

Operation    | Workers | Equipment | Duration | Precedence
-------------|---------|-----------|----------|------------
Foundation   | 20      | Excavator | 10 days  | -
Pier Erect   | 15      | Crane     | 15 days  | Foundation
Deck Install | 25      | 2×Crane   | 20 days  | Pier
Chain Hang   | 30      | Winches   | 25 days  | Deck
Finishing    | 10      | Hand tools| 30 days  | Chain
```
