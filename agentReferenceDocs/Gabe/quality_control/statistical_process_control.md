# Statistical Process Control (SPC)

Statistical process control (SPC) is a method of quality control that uses statistical methods to monitor and control a process. The goal of SPC is to ensure that the process operates at its full potential to produce conforming products.

## Control Charts

### Implementation Guidelines
```
Chart Types:
- X̄-R charts: Dimensional measurements
- P-charts: Defect rates
- C-charts: Defects per unit
- CUSUM: Detecting small shifts
```

### Control Limits
- **Upper Control Limit (UCL)**: Mean + 3σ
- **Lower Control Limit (LCL)**: Mean - 3σ
- **Upper Warning Limit**: Mean + 2σ
- **Lower Warning Limit**: Mean - 2σ

## Process Capability Analysis

### Key Metrics
```
Cp = (USL - LSL) / 6σ
Cpk = min[(USL - μ) / 3σ, (μ - LSL) / 3σ]

Target Values:
- Cp > 1.33: Process capable
- Cpk > 1.33: Process centered and capable
- Cp > 2.0: Six Sigma capability
```

## Root Cause Analysis

### Fishbone Diagram Categories
```
3D Printing Defects
├── Machine
│   ├── Calibration
│   ├── Wear
│   └── Maintenance
├── Material
│   ├── Quality
│   ├── Moisture
│   └── Age
├── Method
│   ├── Settings
│   ├── Orientation
│   └── Support
├── Environment
│   ├── Temperature
│   ├── Humidity
│   └── Vibration
└── Measurement
    ├── Accuracy
    ├── Repeatability
    └── Calibration
```
