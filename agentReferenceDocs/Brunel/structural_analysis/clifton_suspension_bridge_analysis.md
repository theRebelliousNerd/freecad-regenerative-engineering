## Case Study: Clifton Suspension Bridge Analysis

### Given Parameters
- Span: 214m (702 ft)
- Width: 9.5m (31 ft)
- Design Load: Traffic + wind
- Material: Wrought iron chains

### Chain Analysis
```
Chain Tension Calculation:
T = wL²/(8h)

where:
  w = distributed load (kN/m)
  L = span (m)
  h = sag (m)

Maximum Tension (at tower):
T_max = T × √(1 + (4h/L)²)

Stress in Chain:
σ = T_max / A_chain

Brunel's Design: σ < 5.5 tons/in² (85 N/mm²)
Actual (with 3 chains): σ = 4.75 tons/in² (73 N/mm²)
```

### Tower Analysis
```
Vertical Load: V = 2T × sin(θ)
Horizontal Load: H = T × cos(θ)
Moment at Base: M = H × height

Check:
- Compression stress in masonry
- Overturning moment
- Sliding resistance
```
