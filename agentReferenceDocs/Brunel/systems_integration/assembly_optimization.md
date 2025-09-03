## Assembly Optimization

### Design for Assembly (DFA) Principles

```
Brunel's DFA Rules (Implicit):
1. Minimize part count
2. Use standard components
3. Design for top-down assembly
4. Eliminate adjustments
5. Use self-locating features

Modern DFA Metrics:
Assembly Time = Σ(handling_time + insertion_time)
Assembly Efficiency = (3 × Nmin) / Total_Assembly_Time
```

### Modular Interface Design

```
Standard Interface Specification:
┌─────────────────┐
│  Bolt Pattern   │  4 × M12 on 100mm PCD
│  Alignment      │  2 × φ10 dowel pins
│  Sealing        │  O-ring groove 2mm × 3mm
│  Electrical     │  24-pin connector
│  Load Rating    │  5000N axial, 2000N lateral
└─────────────────┘
```
