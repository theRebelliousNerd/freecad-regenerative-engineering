## Stress Distribution Patterns

### Uniform Stress Distribution
Ideal case where stress is constant across a section.

```
σ = P/A (constant across area)

Example: Axially loaded rod
|←─ A ─→|
┌───────┐
│       │ P →
└───────┘
σ = P/A everywhere
```

### Non-Uniform Stress Distribution

#### Bending Stress
```
σ = My/I

Distribution:
  Compression
    ────
    ─┬─
     │  } Neutral axis (σ = 0)
    ─┴─
    ────
   Tension

Maximum at extreme fibers
```

#### Shear Stress in Beams
```
τ = VQ/(It)

Parabolic distribution:
│\     /│
│ \   / │  Maximum at neutral axis
│  \_/  │  Zero at top/bottom
│       │
```

### Stress Concentration

Stress multiplies at geometric discontinuities:

```
Circular Hole:
  ───┬───
     │    K_t = 3.0
  ───○───  σ_max = 3σ_nominal
     │
  ───┴───

Fillet:
  ──┐
    │╲    K_t = 1.5-2.5
  ──┴─    depending on r/d ratio
```
