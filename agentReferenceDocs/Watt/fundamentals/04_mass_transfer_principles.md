# Mass Transfer Principles for Thermal Systems

*"Understanding mass transfer is essential for complete thermal system analysis."* - Multi-physics coupling principles

## Executive Summary

Mass transfer is the transport of mass from one location to another within a system or between systems. In thermal applications, mass transfer often occurs simultaneously with heat transfer, creating coupled phenomena that significantly affect system performance. Mass transfer is driven by concentration gradients, pressure differences, temperature gradients, or chemical potential differences.

## Fundamental Principles of Mass Transfer

### Modes of Mass Transfer

**Molecular Diffusion:** Random molecular motion causes mass transfer from regions of high concentration to low concentration, similar to heat conduction.

**Convective Mass Transfer:** Bulk fluid motion combined with molecular diffusion transports mass, analogous to convective heat transfer.

**Advection:** Mass transport by bulk fluid motion, where the fluid carries dissolved or suspended species.

### Fick's Laws of Diffusion

**Fick's First Law** (steady-state molecular diffusion):
```
J_A = -D_AB · (dC_A/dx)
```

Where:
- J_A = molar flux of species A [mol/m²·s]
- D_AB = binary diffusion coefficient [m²/s]
- C_A = molar concentration of species A [mol/m³]
- dC_A/dx = concentration gradient [mol/m⁴]

**Fick's Second Law** (unsteady-state diffusion):
```
∂C_A/∂t = D_AB · ∇²C_A
```

This is analogous to the heat equation, with concentration replacing temperature and diffusivity replacing thermal diffusivity.

### Mass Transfer by Convection

**Convective Mass Transfer Equation:**
```
N_A = k_c · (C_As - C_A∞)
```

Where:
- N_A = molar flux [mol/m²·s]
- k_c = mass transfer coefficient [m/s]
- C_As = concentration at surface [mol/m³]
- C_A∞ = bulk concentration [mol/m³]

## Dimensionless Numbers in Mass Transfer

### Schmidt Number
```
Sc = μ/(ρ·D_AB) = ν/D_AB
```
Represents the ratio of momentum diffusivity to mass diffusivity (analogous to Prandtl number in heat transfer).

### Sherwood Number
```
Sh = k_c·L/D_AB
```
Dimensionless mass transfer coefficient (analogous to Nusselt number).

### Lewis Number
```
Le = α/D_AB = Sc/Pr
```
Relates thermal and mass diffusivities. When Le = 1, heat and mass transfer boundary layers have similar thickness.

### Péclet Number for Mass Transfer
```
Pe_m = V·L/D_AB = Re·Sc
```
Ratio of convective to diffusive mass transport.

## Heat and Mass Transfer Analogy

### Reynolds Analogy Extension

The analogy between heat and mass transfer allows us to relate their coefficients:

**For gases (Pr ≈ Sc ≈ 0.7):**
```
St = St_m = Cf/2
```

Where:
- St = h/(ρ·cp·V) (Stanton number for heat)
- St_m = k_c/V (Stanton number for mass)
- Cf = friction factor

**General Chilton-Colburn Analogy:**
```
St·Pr^(2/3) = St_m·Sc^(2/3) = Cf/2
```

This allows estimation of mass transfer coefficients from known heat transfer correlations:
```
Sh = Nu·(Sc/Pr)^(1/3)
```

## Mass Transfer Correlations

### Internal Flow (Pipes and Ducts)

**Laminar Flow (Re < 2300):**
```
Sh = 3.66 (constant wall concentration)
Sh = 4.36 (constant mass flux)
```

**Turbulent Flow (Re > 10,000):**
```
Sh = 0.023·Re^0.8·Sc^0.33  (Dittus-Boelter analogy)
```

### External Flow

**Flat Plate:**
```
Sh_L = 0.664·Re_L^0.5·Sc^(1/3)  (Laminar, Re_L < 5×10⁵)
Sh_L = 0.037·Re_L^0.8·Sc^(1/3)  (Turbulent, Re_L > 5×10⁵)
```

**Sphere in Cross-flow:**
```
Sh = 2 + 0.6·Re^0.5·Sc^(1/3)  (Re < 7×10⁴)
```

**Cylinder in Cross-flow:**
```
Sh = 0.62·Re^0.5·Sc^(1/3)  (Re: 40-4000)
```

## Simultaneous Heat and Mass Transfer

### Evaporation and Condensation

When evaporation or condensation occurs at an interface, both heat and mass transfer are coupled:

**Mass Transfer Rate:**
```
ṁ = k_c·A·(ρ_s - ρ_∞)
```

**Sensible Heat Transfer:**
```
q_sensible = h·A·(T_s - T_∞)
```

**Latent Heat Transfer:**
```
q_latent = ṁ·h_fg
```

**Total Heat Transfer:**
```
q_total = q_sensible + q_latent
```

### Wet Surface Heat Transfer

For a wet surface in air (cooling towers, evaporative coolers):

```
q/A = h_c·(T_s - T_∞) + k_c·h_fg·(ρ_v,s - ρ_v,∞)
```

Where:
- ρ_v,s = water vapor density at surface temperature
- ρ_v,∞ = water vapor density in bulk air
- h_fg = latent heat of vaporization

### Psychrometric Applications

**Humidity Ratio:**
```
W = 0.622·(P_v/(P - P_v))
```

**Enthalpy of Moist Air:**
```
h = cp_a·T + W·(h_fg + cp_v·T)
```

**Wet Bulb Temperature:** Temperature at which water evaporation balances heat transfer from air.

## Mass Transfer in Porous Media

### Diffusion Through Porous Structures

**Effective Diffusivity:**
```
D_eff = D_AB · (ε/τ)
```

Where:
- ε = porosity
- τ = tortuosity factor (typically 1.5-5)

**Knudsen Diffusion** (when pore size << mean free path):
```
D_K = (d_pore/3)·√(8RT/(πM))
```

### Capillary Action and Wicking

**Lucas-Washburn Equation** for capillary rise:
```
h² = (r·σ·cos(θ)·t)/(2μ)
```

Where:
- r = capillary radius
- σ = surface tension
- θ = contact angle
- μ = dynamic viscosity

## Applications in Thermal Systems

### Cooling Tower Design

**Mass Transfer Coefficient:**
```
k_G = (h_G/cp)·Le^(2/3)
```

**Cooling Tower Performance:**
```
L/G = (h₁ - h₂)/(H₁ - H₂)
```

Where L/G is liquid-to-gas mass ratio, h is air enthalpy, H is water enthalpy.

### Humidification and Dehumidification

**Humidifier Effectiveness:**
```
ε_h = (W₂ - W₁)/(W_sat(T₁) - W₁)
```

**Dehumidifier Performance:**
```
Moisture Removal Rate = ṁ_air·(W₁ - W₂)
```

### Membrane Systems

**Permeation Rate:**
```
J = P·(p₁ - p₂)/δ
```

Where:
- P = permeability coefficient
- p₁, p₂ = partial pressures on either side
- δ = membrane thickness

### Absorption/Adsorption Systems

**Equilibrium Relationships:**
- **Henry's Law:** C = H·P (dilute solutions)
- **Langmuir Isotherm:** q = q_max·b·C/(1 + b·C)
- **BET Isotherm:** For multilayer adsorption

## Diffusion Coefficients

### Typical Values in Air at 25°C

- **Water vapor:** 2.6×10⁻⁵ m²/s
- **Oxygen:** 2.1×10⁻⁵ m²/s
- **Carbon dioxide:** 1.6×10⁻⁵ m²/s
- **Ammonia:** 2.4×10⁻⁵ m²/s

### Temperature Dependence

**Fuller-Schettler-Giddings Correlation:**
```
D_AB = (0.00143·T^1.75)/(P·M_AB^0.5·(Σv_A^(1/3) + Σv_B^(1/3))²)
```

Where:
- T = temperature [K]
- P = pressure [atm]
- M_AB = reduced molecular weight
- Σv = sum of atomic diffusion volumes

## Practical Design Considerations

### Mass Transfer Equipment Design

**Packed Columns:**
- Calculate height of transfer unit (HTU)
- Determine number of transfer units (NTU)
- Account for flooding and pressure drop limitations

**Spray Systems:**
- Droplet size distribution affects mass transfer area
- Residence time determines approach to equilibrium
- Drift losses and entrainment considerations

### Boundary Layer Interactions

**Concentration Boundary Layer Thickness:**
```
δ_c/δ = Sc^(-1/3)
```

For Sc > 1: δ_c < δ (concentration BL thinner than velocity BL)
For Sc < 1: δ_c > δ (concentration BL thicker than velocity BL)

### Enhancement Techniques

**Surface Modifications:**
- Increased surface roughness
- Catalytic surfaces
- Selective membranes

**Flow Modifications:**
- Mixing enhancement
- Swirl generation
- Pulsating flow

## Quality Assurance for Mass Transfer Analysis

### Design Verification Checklist

1. **Mass Balance Verification**
   - [ ] Species conservation satisfied
   - [ ] Generation/consumption terms included
   - [ ] Boundary conditions consistent

2. **Transport Coefficient Selection**
   - [ ] Appropriate correlations for geometry and flow regime
   - [ ] Schmidt number calculated correctly
   - [ ] Diffusion coefficients at correct temperature

3. **Coupled Heat-Mass Transfer**
   - [ ] Latent heat effects included
   - [ ] Temperature-concentration coupling addressed
   - [ ] Equilibrium relationships accurate

4. **System Integration**
   - [ ] Mass transfer rates consistent with heat transfer
   - [ ] Pressure drop effects on driving forces
   - [ ] Thermodynamic equilibrium limitations

### Common Design Errors

1. **Neglecting temperature effects** on diffusion coefficients
2. **Assuming constant properties** in varying temperature fields  
3. **Ignoring bulk flow effects** in high mass transfer rate systems
4. **Overlooking equilibrium limitations** in absorption/desorption
5. **Incorrect analogy application** between heat and mass transfer

## Engineering Applications Summary

Mass transfer is critical in:
- **Cooling towers and evaporative coolers**
- **Absorption chillers and heat pumps**
- **Humidification and dehumidification systems**
- **Membrane separations and heat recovery**
- **Catalytic reactors with heat generation**
- **Drying processes and thermal treatment**

Understanding mass transfer principles enables accurate prediction of system performance where simultaneous heat and mass transport occur, leading to optimized thermal system designs with enhanced effectiveness and efficiency.

Remember: "Mass transfer and heat transfer are often inseparable partners in thermal systems." Recognizing their coupling enables more accurate analysis and superior design optimization.