## 2. Great Western Railway (1833-1841)

### Project Specifications
- **Length**: 189 km (118 miles)
- **Gauge**: 2140mm (7 ft 1⁄4 in) broad gauge
- **Gradient**: Maximum 1:1000 (except Box Tunnel 1:100)
- **Speed**: Design for 60 mph average
- **Cost**: £6.5 million

### System Design Philosophy

#### Route Selection Analysis
```
Route Comparison:
Direct Route:          Brunel's Route:
London                 London
  ↓ (steep)             ↓ (gradual)
High Wycombe           Slough
  ↓ (valleys)           ↓ (flat)
Oxford                 Reading
  ↓ (hills)             ↓ (Thames valley)
Bath                   Swindon
  ↓                     ↓ (gentle)
Bristol                Bath
                        ↓
                       Bristol

Distance: 116 miles    Distance: 118 miles
Max gradient: 1:75     Max gradient: 1:100
Earthworks: Massive    Earthworks: Minimal
```

#### Broad Gauge Advantages
```python
def gauge_comparison():
    standard_gauge = {
        'width': 1435,  # mm
        'stability': 'moderate',
        'speed_limit': 45,  # mph in 1840s
        'capacity': 'limited',
        'ride_quality': 'rough'
    }
    
    brunel_broad = {
        'width': 2140,  # mm
        'stability': 'excellent',
        'speed_limit': 60,  # mph achieved
        'capacity': 'high',
        'ride_quality': 'smooth'
    }
    
    # Lower center of gravity
    cg_ratio = 1435/2140  # 0.67
    stability_improvement = 1/cg_ratio  # 1.49× better
    
    return stability_improvement
```

### Major Structures

#### Maidenhead Bridge
```
Two brick arches, each 39m span
World's flattest brick arches (1:3.5 rise:span)

Arch Analysis:
Horizontal thrust: H = wL²/(8h)
where:
  w = 150 kN/m (load)
  L = 39m (span)
  h = 11m (rise)

H = 150 × 39²/(8 × 11) = 2,592 kN

Abutment design:
- Must resist 2,592 kN horizontal
- Founding depth: 8m to solid chalk
- Safety factor: 2.0
```

#### Box Tunnel Engineering
Detailed in Load Paths document, key points:
- 2,937m length
- 1:100 gradient
- 6 construction shafts
- 2-inch alignment error
- 30 months construction

### Track System Innovation

#### Baulk Road Design
```
Cross-Section:
    Rails
    ═════════════
    ║         ║    Longitudinal timbers
    ═══════════    (baulks)
    //////////     Ballast
    
Advantages:
- Continuous support (vs point support)
- Smooth ride
- Load distribution
- Reduced ballast pressure

Disadvantages:
- Timber decay
- Maintenance difficulty
- Higher initial cost
```

### Performance Metrics
```python
def gwr_performance():
    metrics = {
        'construction_time': '8 years',
        'peak_workforce': 20000,
        'earthworks': '10 million cubic yards',
        'bridges': 129,
        'tunnels': 2,
        'stations': 35,
        'initial_revenue': '£1.3M/year',
        'passenger_growth': '500% in 10 years'
    }
    
    return metrics
```
