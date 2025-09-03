## Connection Systems

### Riveted Assemblies (Historical)

```
Single Riveted Lap Joint:
══════════════
    ○ ○ ○ ○    Efficiency: 50-60%
══════════════

Double Riveted Lap Joint:
══════════════
  ○ ○ ○ ○ ○    Efficiency: 60-70%
   ○ ○ ○ ○
══════════════

Brunel's Innovation - Staggered Double:
══════════════
  ○   ○   ○    Efficiency: 70-75%
    ○   ○      Better stress distribution
══════════════
```

### Assembly Process
```python
def rivet_assembly_process():
    """
    Historical hot riveting process
    """
    steps = [
        "1. Heat rivet to 1000°C (cherry red)",
        "2. Insert through aligned holes",
        "3. Holder-on supports one side",
        "4. Riveter forms head on other side", 
        "5. Rivet contracts on cooling",
        "6. Creates pretension in joint"
    ]
    
    crew_roles = {
        'heater': 'Maintains forge, heats rivets',
        'catcher': 'Catches hot rivet, inserts',
        'holder_on': 'Backs up rivet with dolly',
        'riveter': 'Forms second head with hammer'
    }
    
    production_rate = "200 rivets/day per gang"
    return steps, crew_roles, production_rate
```
