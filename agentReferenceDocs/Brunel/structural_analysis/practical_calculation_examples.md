## Practical Calculation Examples

### Example 1: Simple Beam
```
Given: L = 5m, w = 10 kN/m, Steel I-beam
Required: Select beam size

Solution:
M_max = wL²/8 = 10 × 5²/8 = 31.25 kN⋅m
Required S = M/σ_allow = 31250/165 = 189 cm³
Select: IPE 200 (S = 194 cm³)

Check deflection:
δ = 5wL⁴/(384EI) = 5×10×5000⁴/(384×200×10⁶×1943)
δ = 21mm < L/250 = 20mm (marginal - consider larger beam)
```

### Example 2: Column Buckling
```
Given: L = 3m, P = 500 kN, pinned ends
Required: Column size

Solution:
Try 200×200×10 HSS
A = 7600 mm², I = 23.4×10⁶ mm⁴
r = √(I/A) = 55.5 mm
λ = KL/r = 1.0×3000/55.5 = 54

From buckling curves: σ_cr = 180 MPa
P_capacity = 180 × 7600 = 1368 kN > 500 kN ✓
```
