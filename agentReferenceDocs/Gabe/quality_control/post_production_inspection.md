# Post-Production Inspection

Post-production inspection is focused on verifying the quality of the finished part. This is achieved through a combination of automated optical inspection, dimensional verification, surface quality assessment, and mechanical testing.

## Automated Optical Inspection (AOI)

### 3D Scanning Systems
**Hexagon PRESTO (2025)**:
- 8.3 million points/second
- 610 x 640mm scan area
- WiFi connectivity
- 7-meter tracking range
- ±0.05mm accuracy

### Inspection Workflow
1. **Part placement** on an inspection station
2. **Automated scanning** (30-60 seconds)
3. **Comparison to CAD** model
4. **Deviation mapping** and analysis
5. **Pass/fail determination**
6. **Report generation**

## Dimensional Verification

### Measurement Strategy
```
Sampling Plan (ANSI/ASQ Z1.4):
- Lot size: 100-500 parts
- Sample size: 8-13 parts
- AQL: 1.0-2.5%
- Critical dimensions: 100% inspection
- Non-critical: Sampling inspection
```

### Go/No-Go Gauge Design
- Design gauges for critical features
- 3D print checking fixtures
- Implement at the production station
- Enable operator self-inspection
- Document pass/fail rates

## Surface Quality Assessment

### Visual Inspection Standards
```
Defect Classification:
Class A (Critical): Affects function
- Missing features
- Cracks or delamination
- Severe warping

Class B (Major): Affects appearance
- Visible layer shifts
- Stringing/oozing
- Support marks on visible surfaces

Class C (Minor): Cosmetic only
- Slight layer lines
- Minor surface roughness
- Color variations
```

### Surface Roughness Measurement
**Keyence VR-6000 Specifications**:
- Sub-micron measurement capability
- ±0.1μm repeatability
- Non-contact measurement
- 3D surface mapping

## Mechanical Testing

### Test Methods
| Test Type | Standard | Equipment | Frequency |
|---|---|---|---|
| Tensile | ASTM D638 | Universal tester | Weekly |
| Compression | ASTM D695 | Universal tester | Weekly |
| Impact | ASTM D256 | Izod tester | Monthly |
| Fatigue | ASTM D7791 | Fatigue tester | Quarterly |
| Creep | ASTM D2990 | Creep tester | As needed |

### Batch Testing Protocol
```
Sampling Strategy:
- First article: Comprehensive testing
- Production: 1 per 100 parts
- Material change: Full revalidation
- Process change: Abbreviated testing
- Customer requirement: As specified
```
