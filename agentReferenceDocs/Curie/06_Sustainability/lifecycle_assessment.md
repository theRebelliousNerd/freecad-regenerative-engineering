# Lifecycle Assessment Methods for Materials Selection
## Quantitative Environmental Impact Analysis for Engineering Design

*"In science, we must be interested in things, not in persons."* - Marie Curie's approach to objective sustainability analysis

## Fundamentals of Lifecycle Assessment (LCA)

### LCA Framework Structure (ISO 14040/14044)

#### Phase 1: Goal and Scope Definition
**Functional Unit Definition**:
- Mass-based: per kg of material
- Function-based: per unit strength (MPa·kg⁻¹)
- Service-based: per year of service life
- Component-based: per functional component

**System Boundaries**:
- **Cradle-to-Gate**: Raw materials → Manufacturing
- **Cradle-to-Grave**: Full lifecycle including disposal
- **Cradle-to-Cradle**: Including recycling/reuse scenarios
- **Gate-to-Gate**: Specific process segments only

#### Phase 2: Life Cycle Inventory (LCI)
**Material Flow Categories**:
```
Inputs:                    Outputs:
- Raw materials           - Products  
- Energy (electricity)    - Co-products
- Energy (thermal)        - Emissions to air
- Water                   - Emissions to water
- Land use                - Emissions to soil
- Transportation          - Waste materials
```

#### Phase 3: Life Cycle Impact Assessment (LCIA)
**Mandatory Impact Categories**:
- Climate Change (kg CO₂ equivalent)
- Ozone Depletion (kg CFC-11 equivalent)
- Acidification (kg SO₂ equivalent)
- Eutrophication (kg PO₄³⁻ equivalent)
- Human Toxicity (CTUh - Comparative Toxic Units for humans)
- Ecotoxicity (CTUe - Comparative Toxic Units for ecosystems)

**Resource Depletion Categories**:
- Abiotic Depletion Potential (kg Sb equivalent)
- Fossil Fuel Depletion (MJ surplus)
- Water Scarcity (m³ water equivalent)

### Material Carbon Footprint Database

#### Primary Materials (kg CO₂ equivalent per kg material)

**Metals and Alloys**:
| Material | Primary Production | Recycled Content | Recycling Benefit |
|----------|-------------------|------------------|-------------------|
| **Steel (mild)** | 2.3-2.8 | 1.2-1.6 | -0.8 to -1.2 |
| **Stainless Steel** | 6.2-7.5 | 3.1-4.2 | -1.8 to -2.4 |
| **Aluminum (primary)** | 8.2-12.8 | 0.6-1.2 | -7.6 to -11.6 |
| **Copper** | 3.2-4.6 | 1.8-2.4 | -1.4 to -2.2 |
| **Titanium** | 35-45 | 15-22 | -20 to -23 |

**Engineering Polymers**:
| Material | Production | End-of-Life | Net Impact |
|----------|------------|-------------|------------|
| **PE (Polyethylene)** | 1.8-2.1 | +0.2 (landfill) | 2.0-2.3 |
| **PP (Polypropylene)** | 1.9-2.3 | -1.5 (energy recovery) | 0.4-0.8 |
| **PET** | 2.2-2.8 | -1.2 (recycling) | 1.0-1.6 |
| **PA6 (Nylon)** | 7.2-9.8 | +0.3 (landfill) | 7.5-10.1 |
| **PEEK** | 18-25 | +0.4 (landfill) | 18.4-25.4 |
| **PLA (Bioplastic)** | 2.0-2.8 | -1.8 (composting) | 0.2-1.0 |

**Composites**:
| Material | Production | Recycling Challenges | Net Impact |
|----------|------------|---------------------|------------|
| **Carbon Fiber/Epoxy** | 24-32 | Limited options | 24-32 |
| **Glass Fiber/Epoxy** | 2.8-4.2 | Energy recovery only | 1.3-2.7 |
| **Natural Fiber/PP** | 1.2-1.8 | Good recyclability | 0.4-1.0 |

### Energy Consumption Analysis

#### Manufacturing Energy Requirements (MJ/kg)

**Primary Processing**:
- Steel from ore: 25-35 MJ/kg
- Aluminum from ore: 45-60 MJ/kg  
- Plastic polymerization: 60-90 MJ/kg
- Carbon fiber production: 180-300 MJ/kg

**Secondary Processing (Shaping)**:
- Casting: 2-8 MJ/kg
- Forging: 8-15 MJ/kg
- Machining: 15-40 MJ/kg
- 3D printing: 20-100 MJ/kg (material dependent)
- Injection molding: 8-20 MJ/kg

**Joining and Assembly**:
- Welding: 0.5-2 MJ/joint
- Mechanical fastening: 0.1-0.5 MJ/joint
- Adhesive bonding: 2-8 MJ/m²
- Composite cure: 15-30 MJ/kg

### Water Footprint Analysis

#### Water Consumption by Material (liters/kg)

**Direct Water Use**:
- Steel production: 20-40 L/kg
- Aluminum production: 1000-2000 L/kg
- Plastic production: 180-300 L/kg
- Paper/cardboard: 10-50 L/kg

**Indirect Water Use (Supply Chain)**:
- Natural fiber composites: 500-2000 L/kg
- Cotton-based materials: 2000-8000 L/kg
- Wool-based materials: 3000-15000 L/kg

### Sustainability Assessment Methodology

#### Multi-Criteria Impact Assessment

**Weighting Factors for Impact Categories**:
```python
impact_weights = {
    'climate_change': 0.30,        # Global priority
    'resource_depletion': 0.25,    # Scarcity concerns
    'toxicity_human': 0.20,        # Health implications
    'toxicity_eco': 0.15,          # Environmental protection
    'acidification': 0.05,         # Regional effects
    'eutrophication': 0.05          # Local water quality
}
```

**Sustainability Index Calculation**:
```
SI = Σ(Impact_i × Weight_i × Normalization_factor_i)
```

Where lower SI values indicate better sustainability performance.

#### Material Selection Decision Matrix

**Sustainability-Weighted Selection**:

| Material | Climate | Resource | Toxicity | Recyclability | Total Score | Rank |
|----------|---------|----------|----------|---------------|-------------|------|
| **Aluminum 6061** | 0.15 | 0.20 | 0.05 | 0.30 | 0.18 | 2 |
| **Steel 1045** | 0.08 | 0.10 | 0.02 | 0.35 | 0.12 | 1 |
| **PEEK** | 0.40 | 0.45 | 0.15 | 0.05 | 0.35 | 5 |
| **Carbon/Epoxy** | 0.50 | 0.60 | 0.25 | 0.02 | 0.48 | 6 |
| **PLA** | 0.05 | 0.08 | 0.03 | 0.40 | 0.11 | 3 |

### Circular Economy Principles

#### Material Circularity Indicators

**Circular Material Use Rate**:
```
CMU = Recycled_Material_Input / (Recycled_Material_Input + Virgin_Material_Input)
```

**End-of-Life Recycling Rate**:
```
EoL_RR = Recycled_Output / (Recycled_Output + Disposed_Output)
```

**Material Circularity Index**:
```
MCI = 1 - (Linear_Index × (1 - Utility_Factor) × (1 - Recovery_Factor))
```

#### Design for Circularity Guidelines

**Material Selection Hierarchy**:
1. **Renewable/Bio-based**: PLA, natural fibers, bio-composites
2. **High Recycled Content**: Secondary aluminum, recycled steel
3. **High Recyclability**: Pure metals, thermoplastics
4. **Biodegradable**: Natural materials, specific bioplastics
5. **Long Service Life**: Durable materials for lasting applications

**Design Strategies**:
- **Material Reduction**: Topology optimization, hollow structures
- **Single Material Design**: Avoid dissimilar material combinations  
- **Mechanical Joining**: Prefer bolts/clips over adhesives
- **Material Identification**: Clear marking for sorting
- **Disassembly Planning**: Accessible fasteners, separation guidelines

### Regional Environmental Factors

#### Electricity Grid Carbon Intensity (kg CO₂/kWh)

**Global Variations**:
- Norway (hydro): 0.02
- France (nuclear): 0.06
- Germany (mixed): 0.35
- China (coal): 0.68
- India (coal): 0.82
- Global average: 0.45

**Impact on Manufacturing**:
Manufacturing location significantly affects carbon footprint:
- Aluminum smelting in Norway vs. China: 7× difference
- 3D printing energy use: Location-dependent factor
- Data center processing: Consider grid mix for AI/computation

#### Transportation Impact Modeling

**Mode-Specific Emissions (kg CO₂/tonne-km)**:
- Ocean freight: 0.01-0.02
- Rail freight: 0.03-0.05
- Road freight: 0.08-0.12
- Air freight: 0.5-1.5

**Distance Sensitivity Analysis**:
```python
def transport_impact(mass_kg, distance_km, mode='road'):
    emission_factors = {
        'ocean': 0.015, 'rail': 0.04, 
        'road': 0.10, 'air': 1.0
    }
    return mass_kg * distance_km * emission_factors[mode] / 1000
```

### Sustainability Reporting Framework

#### Key Performance Indicators (KPIs)

**Material Efficiency**:
- Material Utilization Rate = (Product mass) / (Input material mass)
- Waste Generation Rate = (Waste mass) / (Product mass)
- Recycled Content Percentage = (Recycled input) / (Total input) × 100%

**Environmental Performance**:
- Carbon Intensity = kg CO₂ equivalent per functional unit
- Water Intensity = L H₂O per functional unit
- Energy Intensity = MJ per functional unit

**Circularity Performance**:
- End-of-Life Recovery Rate = Percentage by mass recovered
- Material Health Assessment = Score (0-100) for toxicity
- Renewable Content = Percentage by mass from renewable sources

#### Integration with Design Process

**LCA-Informed Material Selection Workflow**:
```python
def sustainable_material_selection(requirements, candidates):
    # Filter by technical requirements
    technical_fit = filter_technical_performance(candidates, requirements)
    
    # Calculate sustainability metrics
    for material in technical_fit:
        material.lca_score = calculate_lca_impact(material)
        material.eol_options = assess_end_of_life(material)
        material.supply_risk = evaluate_supply_chain(material)
    
    # Multi-objective optimization
    pareto_optimal = optimize_performance_sustainability(technical_fit)
    
    return rank_by_weighted_criteria(pareto_optimal, weights)
```

**Continuous Improvement Metrics**:
- Year-over-year carbon footprint reduction
- Recycled content increase targets
- Waste reduction achievements
- Supplier sustainability scorecard improvements

This comprehensive LCA framework enables quantitative sustainability assessment within the Curie materials selection process, ensuring environmental considerations are systematically integrated with technical and economic factors in engineering design decisions.