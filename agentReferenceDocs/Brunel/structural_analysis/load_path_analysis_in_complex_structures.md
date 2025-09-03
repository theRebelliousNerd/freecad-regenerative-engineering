## Load Path Analysis in Complex Structures

### Brunel's Royal Albert Bridge

```
Load Path Diagram:
                Train Load (W)
                     ↓
              [Deck Girder]
                  ↓    ↓
           [Hangers - Tension]
              ↓          ↓
    [Chains - Tension]  [Verticals]
         ↓                   ↓
    [Arch Tube - Compression]
              ↓     ↓
         [Pier]   [Pier]
           ↓         ↓
      [Foundation] [Foundation]
```

**Force Distribution:**
- Deck load: W
- Hanger tension: W/n (n = number of hangers)
- Chain tension: T = WL/(8h)
- Arch compression: C = T/cos(θ)
- Pier vertical: W/2
- Pier horizontal: H = T×cos(θ)

### Great Eastern Hull

```
Wave Load Distribution:

Hogging (wave crest amidships):
     ╱╲
    ╱  ╲     Compression in deck
   ╱    ╲    Tension in keel
  ────────

Sagging (wave trough amidships):
  ────────
   \    /    Tension in deck
    \  /     Compression in keel
     \/
```

**Double Hull Load Sharing:**
- Outer hull: 60% of bending moment
- Inner hull: 30% of bending moment
- Connecting structure: 10% + shear transfer
