## Optimizing Load Paths

### Design Strategies

#### 1. Minimize Path Length
Shorter paths = less material, lower deflection

```
Poor:          Better:
  P              P
  │              │
  └──┐          ╱│
     │         ╱ │
     └──┐     ╱  │
        │    ╱   │
        ▼   ▼    ▼
```

#### 2. Align with Principal Stresses
Orient members along stress trajectories

```
Stress Trajectories:
┌─────────────┐
│ ╱ ╱ ╱ ╱ ╱ ╱ │ ← Compression
│╱ ╱ ╱ ╱ ╱ ╱  │
│ ╱ ╱ ╱ ╱ ╱ ╱ │
└─────────────┘
    Optimal member orientation
```

#### 3. Gradual Load Transfer
Avoid sudden changes in stiffness

```
Abrupt:         Gradual:
████│           ████╲
████│           ████ ╲
    │                 ╲
    │                  ╲
Stress spike     Smooth transition
```
