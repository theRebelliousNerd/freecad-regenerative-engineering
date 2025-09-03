## Types of Load Paths

### Direct Load Path
Forces travel in straight lines through members in pure compression or tension.

```
Example: Column under vertical load
     P
     ↓
   [===]  (compression)
     ↓
   Base
```

**Advantages:**
- Most efficient use of material
- Minimal bending stresses
- Predictable behavior

### Indirect Load Path
Forces must change direction through connections and joints.

```
Example: Portal frame
    P
    ↓
  ┌─┴─┐   (moment connection)
  │   │   (combined bending + axial)
  └───┘
```

**Considerations:**
- Stress concentrations at direction changes
- Bending moments induced
- Requires stronger connections

### Redundant Load Paths
Multiple paths available for load transfer.

```
Example: Truss with redundant members
    P
    ↓
  /│\   Multiple paths:
 / │ \  - Direct through center
/  │  \ - Through diagonal members
───────
```

**Benefits:**
- Increased safety (alternate paths if one fails)
- Load sharing reduces individual member stress
- Progressive collapse prevention
