# Material Comparison Matrix
*Quantitative Performance Data for FDM Material Selection*

## Comprehensive Material Performance Database

### Mechanical Properties (As-Printed FDM Parts)
```
COMPRESSIVE STRENGTH TEST RESULTS:
                    Max Load    Max Load    Failure Mode         Density    Cost
Material            (lbf)       (N)                             (g/cm³)    ($/kg)
PLA                 530         2362        Brittle fracture     1.24       $25
PETG                485         2160        Ductile deform       1.27       $35  
ABS                 472         2100        Ductile deform       1.04       $30
PA6 Nylon           189         844         Buckling/deform      1.14       $60
TPU                 N/A         N/A         Elastic deform       1.20       $80
ASA                 465         2070        Ductile deform       1.07       $45
PC (Polycarbonate)  580         2580        Ductile deform       1.20       $120
PEEK                850         3780        Ductile deform       1.30       $400+
```

### Thermal Properties
```
TEMPERATURE RESISTANCE:
Material      Glass Trans.  Deflection   Max Service   Print Temp   Bed Temp
              Temp (°C)     Temp (°C)    Temp (°C)     (°C)         (°C)
PLA           60            55           50-60         190-220      60
PETG          80            70           70-80         220-250      70-80
ABS           105           95           80-100        220-250      90-110
PA6 Nylon     60            180          120-150       240-270      70-90
TPU           Variable      Variable     60-80         210-230      60
ASA           110           100          85-105        240-260      90-110
PC            150           138          110-130       270-300      110-130
PEEK          143           152          200-250       360-400      150-200
```

### Print Quality Characteristics
```
PRINTING PERFORMANCE MATRIX:
                   Ease of    Overhang    Support      Warping    Surface
Material           Printing   Quality     Removal      Tendency   Finish
PLA                ★★★★★     ★★★★★      ★★★★☆     ★★★★★     ★★★★☆
PETG               ★★★★☆     ★★★★☆      ★★★★★     ★★★★☆     ★★★★☆
ABS                ★★★☆☆     ★★★☆☆      ★★★★☆     ★★☆☆☆     ★★★☆☆
PA6 Nylon          ★★☆☆☆     ★★★☆☆      ★★☆☆☆     ★★☆☆☆     ★★★★☆
TPU                ★★☆☆☆     ★★☆☆☆      ★★★☆☆     ★★★★★     ★★★☆☆
ASA                ★★★☆☆     ★★★☆☆      ★★★★☆     ★★☆☆☆     ★★★☆☆
PC                 ★★☆☆☆     ★★☆☆☆      ★★☆☆☆     ★☆☆☆☆     ★★★☆☆
PEEK               ★☆☆☆☆     ★★☆☆☆      ★★☆☆☆     ★☆☆☆☆     ★★★★☆
```

## Material Selection Decision Matrix

### Application-Based Selection
```python
def select_optimal_material(application_requirements):
    """Material selection algorithm based on requirements"""
    
    if application_requirements.temperature_max < 60:
        if application_requirements.strength_priority == "HIGH":
            return "PLA"  # Best strength, easiest printing
        elif application_requirements.flexibility_needed:
            return "PETG"  # Good strength, some flexibility
        else:
            return "PLA"  # Default for low-temp applications
    
    elif application_requirements.temperature_max < 100:
        if application_requirements.chemical_resistance:
            return "PETG"  # Better chemical resistance than PLA
        elif application_requirements.impact_resistance:
            return "ABS"   # Best impact resistance in this range
        else:
            return "PETG"  # Good all-around performer
    
    elif application_requirements.temperature_max < 150:
        if application_requirements.wear_resistance:
            return "PA6_NYLON"  # Excellent wear resistance
        elif application_requirements.dimensional_stability:
            return "ASA"    # Better than ABS for outdoor use
        else:
            return "ABS"    # Standard high-temp material
    
    else:  # High-temperature applications
        if application_requirements.budget == "HIGH":
            return "PEEK"   # Ultimate performance
        else:
            return "PC"     # High performance, moderate cost
```

### Strength-to-Weight Optimization
```
STRENGTH-TO-WEIGHT RATIOS (Compressive):
Material        Strength/Weight    Relative Score    Best Use Case
PEEK            2908 N/g·cm³       100%             Aerospace, medical
PLA             1905 N/g·cm³       66%              General structural
PETG            1701 N/g·cm³       58%              Transparent parts
ABS             2019 N/g·cm³       69%              Impact resistance
PA6 Nylon       740 N/g·cm³        25%              Flexible mechanisms
PC              2150 N/g·cm³       74%              High-temp structural
ASA             1935 N/g·cm³       67%              Outdoor applications
```

## Specialized Material Properties

### Chemical Resistance Matrix
```
CHEMICAL RESISTANCE RATINGS:
             Alcohols  Acids   Bases   Oils    Solvents  UV
PLA          Good      Poor    Poor    Fair    Poor      Poor
PETG         Excellent Good    Good    Good    Fair      Fair  
ABS          Good      Fair    Fair    Good    Poor      Poor
Nylon        Good      Poor    Fair    Excellent Good    Good
TPU          Good      Good    Good    Excellent Fair    Fair
ASA          Good      Good    Fair    Good    Fair      Excellent
PC           Excellent Excellent Good  Good    Fair      Good
PEEK         Excellent Excellent Excellent Excellent Good Excellent
```

### Electrical Properties
```
ELECTRICAL CHARACTERISTICS:
Material      Dielectric   Volume        Surface       Conductivity
              Strength     Resistivity   Resistivity   Modification
              (kV/mm)      (Ω·cm)        (Ω)           Possible
PLA           40-50        10¹⁶          10¹⁴          Carbon fill
PETG          45-55        10¹⁶          10¹⁴          Conductive variants
ABS           35-45        10¹⁶          10¹⁴          Carbon/metal fill
Nylon         25-35        10¹³          10¹²          Conductive grades
TPU           30-40        10¹⁴          10¹³          Conductive available
PC            65-75        10¹⁶          10¹⁴          Static dissipative
PEEK          50-60        10¹⁸          10¹⁶          Carbon fiber filled
```

## Manufacturing Considerations by Material

### PLA Manufacturing Profile
```json
{
  "pla_manufacturing": {
    "ease_of_printing": 95,
    "support_requirements": "Minimal - excellent overhangs",
    "post_processing": "Easy machining, gluing, painting",
    "dimensional_accuracy": "±0.1-0.15mm typical",
    "production_speed": "Fast - high print speeds possible",
    "warping_management": "Minimal bed heating required",
    "environmental_sensitivity": "Low humidity requirements"
  }
}
```

### PETG Manufacturing Profile  
```json
{
  "petg_manufacturing": {
    "ease_of_printing": 80,
    "support_requirements": "Easy removal, sometimes too strong",
    "post_processing": "Chemical welding, limited machining",
    "dimensional_accuracy": "±0.15-0.2mm typical", 
    "production_speed": "Moderate - temperature sensitive",
    "warping_management": "Moderate bed heating",
    "environmental_sensitivity": "Moderate humidity tolerance"
  }
}
```

### ABS Manufacturing Profile
```json
{
  "abs_manufacturing": {
    "ease_of_printing": 60,
    "support_requirements": "Good removal, soluble supports available",
    "post_processing": "Excellent - vapor smoothing, welding",
    "dimensional_accuracy": "±0.2-0.3mm due to warping",
    "production_speed": "Moderate - requires chamber heating",
    "warping_management": "Enclosed chamber strongly recommended", 
    "environmental_sensitivity": "Requires stable thermal environment"
  }
}
```

## Cost-Performance Analysis

### Material Cost vs Performance
```
COST-BENEFIT ANALYSIS (Relative to PLA):
Material    Cost     Strength   Temp      Ease     Overall
            Ratio    Ratio      Ratio     Ratio    Value
PLA         1.0x     1.0x       1.0x      1.0x     1.0x (baseline)
PETG        1.4x     0.91x      1.33x     0.85x    0.89x
ABS         1.2x     0.89x      1.67x     0.65x    0.91x
Nylon       2.4x     0.36x      2.5x      0.40x    0.44x
TPU         3.2x     N/A        1.33x     0.45x    Special case
ASA         1.8x     0.88x      1.75x     0.60x    0.71x
PC          4.8x     1.09x      2.17x     0.40x    0.59x
PEEK        16x      1.60x      4.17x     0.20x    0.47x
```

### Production Volume Considerations
```
VOLUME-BASED MATERIAL SELECTION:
Low Volume (1-100 parts):
- Prioritize ease of printing and material availability
- PLA or PETG recommended for most applications
- Prototype with cheap materials, production with optimal

Medium Volume (100-10,000 parts):
- Balance material cost with printing efficiency
- Consider setup time for difficult materials
- ABS worth the complexity for suitable applications

High Volume (10,000+ parts):
- Optimize total cost including labor and failures
- Invest in proper equipment for difficult materials
- Material cost becomes secondary to production efficiency
```

## Quality Control by Material

### Dimensional Stability Factors
```
DIMENSIONAL VARIATION SOURCES:
PLA: Minimal shrinkage, excellent stability
- Typical variation: ±0.05-0.1mm
- Factors: Print temperature consistency

PETG: Moderate shrinkage, good stability  
- Typical variation: ±0.1-0.15mm
- Factors: Cooling rate, bed adhesion

ABS: High shrinkage, warping sensitivity
- Typical variation: ±0.15-0.3mm  
- Factors: Thermal gradients, part geometry

Nylon: High shrinkage, moisture sensitive
- Typical variation: ±0.2-0.4mm
- Factors: Moisture content, thermal history
```

### Production Testing Requirements
```json
{
  "material_testing_protocol": {
    "incoming_inspection": {
      "diameter_consistency": "±0.02mm tolerance",
      "moisture_content": "<0.1% for hygroscopic materials",
      "color_consistency": "ΔE <2.0 for critical applications"
    },
    "print_quality_testing": {
      "dimensional_accuracy": "First article inspection per batch",
      "mechanical_properties": "Tensile testing per material change", 
      "surface_finish": "Visual inspection to standard"
    }
  }
}
```

## Selection Flowchart

### Quick Material Selection Guide
```
START: Application Requirements
│
├─ Temperature <60°C?
│  ├─ YES: Need flexibility? → PETG : PLA
│  └─ NO: Continue to next question
│
├─ Temperature <100°C?
│  ├─ YES: Chemical exposure? → PETG : ABS/ASA
│  └─ NO: Continue to next question
│
├─ Temperature <150°C?  
│  ├─ YES: Wear resistance needed? → Nylon : PC
│  └─ NO: PEEK (if budget allows) or PC
│
└─ Special requirements?
   ├─ Flexible: TPU
   ├─ Outdoor: ASA  
   ├─ Clear: PETG or PC
   └─ Conductive: Carbon-filled variants
```

**Remember**: Material selection is not about finding the "best" material—it's about finding the optimal balance of performance, manufacturability, and cost for your specific application and production volume.