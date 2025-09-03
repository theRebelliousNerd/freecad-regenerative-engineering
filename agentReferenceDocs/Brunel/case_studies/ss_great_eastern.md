## 3. SS Great Eastern (1854-1858)

### Project Specifications
- **Length**: 211m (692 ft)
- **Beam**: 25m (82 ft)
- **Displacement**: 32,160 tons loaded
- **Propulsion**: Paddle wheels + screw propeller + sails
- **Capacity**: 4,000 passengers or 10,000 troops
- **Innovation**: First double-hull iron ship

### Structural Design

#### Double Hull System
```
Cross-Section:
Water ~~~~~~~~~~~~~~~~~~~
      ╔═══════════════╗  Outer hull (19mm plates)
      ║               ║
      ║  ┌─────────┐  ║  Inner hull
      ║  │         │  ║  
      ║  │  CARGO  │  ║  860mm gap
      ║  │         │  ║  (cellular construction)
      ║  └─────────┘  ║
      ╚═══════════════╝
      
Advantages:
- Damage tolerance (grounding protection)
- Increased longitudinal strength
- Buoyancy reserve
- Coal bunker space
```

#### Stress Analysis
```python
def hull_stress_calculation():
    """
    Longitudinal bending stress in waves
    """
    # Ship parameters
    L = 211  # m
    B = 25   # m
    D = 18   # m (depth)
    displacement = 32160  # tons
    
    # Wave bending moment (hogging)
    M_wave = 0.11 * displacement * L  # ton⋅m
    M_wave = 0.11 * 32160 * 211
    M_wave = 746_476  # ton⋅m
    
    # Section modulus (double hull)
    I = calculate_moment_of_inertia()  # m⁴
    y = D/2  # distance to extreme fiber
    S = I/y  # section modulus
    
    # Stress
    stress = M_wave / S  # MPa
    allowable = 77  # MPa (wrought iron)
    
    FOS = allowable / stress
    return FOS  # Should be > 2.5
```

#### Standardization Achievement
```
Component Standardization:
- 30,000 iron plates (only 2 sizes)
- 3 million rivets (1 diameter)
- Angle bars (2 sizes only)
- Frame spacing (uniform 1.8m)

Result: Weight/displacement ratio = 0.24
(Compare modern ships: 0.30-0.35)
```

### Propulsion System Integration

#### Triple Redundancy Design
```
System Layout:
         Paddle Engines
              ↓
    ┌─────────────────────┐
    │  4 cylinders        │
    │  2.13m bore         │ Port paddle (17m dia)
    │  4.3m stroke        ├→
    │  1000 HP nominal    │
    └─────────────────────┘
    
         Screw Engine
              ↓
    ┌─────────────────────┐
    │  4 cylinders        │
    │  2.13m bore         │ Propeller (7.3m dia)
    │  4.3m stroke        ├→
    │  1600 HP nominal    │
    └─────────────────────┘
    
         6 Masts
           ├─├─├
         5400 m² sail area
```

### Launch Disaster Analysis

#### Failed Perpendicular Launch
```
Original Plan:
    HULL
    ════════
    ╱╱╱╱╱╱╱╱  Slipway (gradient 1:12)
~~~~~~~~~~~~  River

Problem: Ship stuck after 1m movement
Cause: Inadequate launching force
```

#### Sideways Launch Solution
```
Revised Plan:
    ┌──────────────┐
    │     HULL     │ → Sideways movement
    └──────────────┘
    ================  Cradles on ways
    
Forces Required:
- Weight: 12,000 tons
- Friction coefficient: 0.15
- Required force: 1,800 tons
- Applied: 2× 80-ton rams + winches
```

### Lessons Learned
1. **Scale limits** - Some things don't scale linearly
2. **Market timing** - Built before market ready
3. **Project management** - Cost overrun 6×
4. **Technical success ≠ Commercial success**
5. **Innovation adoption** - Too far ahead can fail
