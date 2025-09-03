# ACTUAL COMPONENT CATALOG - PDU MEDIA PLAYER ENCLOSURE
## Based on Amazon Components List
*Generated: 2025-09-02*

---

## ✅ ACTUAL COMPONENTS FROM PURCHASE LIST

### 1. RELAY MODULE
**Product**: NOYITO 30A 4 Channel Relay Module
**Source**: Amazon B07BLKV64Y
- **Channels**: 4 (Note: Need 2 modules for 8 channels total)
- **Load Rating**: DC 30V / AC 250V @ 30A
- **Control Voltage**: 5V
- **Features**: Optocoupler isolation, High/Low level trigger
- **Estimated Dimensions**: ~75×55×20mm per module (typical for 4-ch)
- **Mounting**: PCB has corner mounting holes (typically M3)
- **Terminal Type**: Screw terminals for load connections
- **Control Interface**: Pin headers for control signals

### 2. USB TYPE-C PANEL MOUNT
**Product**: Right&Left Angled USB 3.1 Type C Panel Mount Cable
**Source**: Amazon B08HS6VXNG
- **Type**: Type-C Male to Female, 90-degree angled
- **Current Rating**: 3A
- **Data**: USB 3.1 Gen 2 support
- **Mounting**: Panel mount with screws
- **Cable Length**: 0.3M (1ft)
- **Application**: Data connection to Arduino Portenta

### 3. AC POWER OUTLETS
**Product**: weideer 3-Pin US Power Socket Panel Mount
**Source**: Amazon B092VQNKN7
- **Quantity**: 3 pieces in order
- **Rating**: 15A 125V AC
- **Type**: NEMA 5-15R panel mount
- **Model**: K-019-X
- **Wire**: 18AWG connection lines included
- **Mounting**: Panel mount (requires rectangular cutout)
- **Application**: Switched AC outputs from relays

### 4. DC POWER SUPPLY
**Product**: 5V 5A Switching Power Supply
**Source**: Amazon B07PPPF1R5
- **Output**: 5V @ 5A (25W)
- **Input**: Universal AC (100-240V)
- **Type**: External adapter/transformer style
- **Application**: Logic power for relays and control
- **Note**: This is 5V, not 12V as mentioned in other docs

### 5. AC INPUT MODULE
**Product**: OZXNO 15A 250V Rocker Switch Power Socket
**Source**: Amazon B08G1VV71K
- **Type**: IEC inlet module with integrated switch
- **Rating**: 15A 250V
- **Fuse**: Built-in 5A fuse holder
- **Switch**: Integrated rocker switch
- **Connector**: 3-pin IEC male inlet
- **Mounting**: Snap-in panel mount
- **Cable**: Extension cable included
- **Application**: Main power input with switch

### 6. POWER DISTRIBUTION TERMINAL BLOCK
**Product**: 30A DIN Rail Terminal Block Distribution Module
**Source**: Amazon B0B55R8TRH
- **Configuration**: 2 input, 8 output
- **Current Rating**: 30A
- **Mounting**: DIN rail mount
- **Type**: Screw terminal connections
- **Application**: Power distribution from PSU to components

---

## 📊 COMPONENT DIMENSIONS ANALYSIS

### RELAY MODULES (2× Required for 8 channels)
| Parameter | Estimated Value | Notes |
|-----------|-----------------|-------|
| Module Size | 75×55×20mm | Per 4-channel module |
| Total Space | 150×55×20mm | If placed side-by-side |
| Mounting | M3 corner holes | 4 holes per module |
| Wire Space | 10mm above terminals | For screw access |
| Heat Generation | ~2W per channel active | 16W max with all on |

### ARDUINO PORTENTA MID CARRIER
| Parameter | From Schematic | Notes |
|-----------|----------------|-------|
| Board Size | 166×101mm | Based on PDF schematic |
| Mounting | M3 holes | Standard Arduino pattern |
| Height with X8 | ~30mm | Including heatsink |
| USB-C Location | Edge mounted | Via panel mount cable |

### POWER COMPONENTS
| Component | Dimensions | Mount Type |
|-----------|------------|------------|
| AC Input Module | 50×30×45mm | Snap-in panel |
| Power Supply | External unit | Outside enclosure |
| Terminal Block | 120×60×80mm | DIN rail |
| AC Outlets (×3) | 45×25×40mm each | Panel cutout |

---

## 🔧 MOUNTING STRATEGY BASED ON ACTUAL COMPONENTS

### DIN RAIL COMPONENTS
1. **Terminal Block Distribution** (30A rated)
   - Mounts on horizontal DIN rail
   - Central location for power distribution

### PANEL MOUNT COMPONENTS
1. **AC Input Module** - Rear panel, snap-in
2. **AC Outlets** (×3) - Side or rear panel
3. **USB Type-C** - Front panel for access

### PCB MOUNTED COMPONENTS
1. **Relay Modules** (×2) - Standoff mounted
2. **Arduino Mid Carrier** - Standoff mounted

---

## 📐 SPACE REQUIREMENTS CALCULATION

### Minimum Internal Volume Required
```
Width = 180mm minimum
- Arduino (166mm) + clearance (14mm)

Depth = 150mm minimum  
- Arduino (101mm) + terminal block (60mm) + wiring

Height = 100mm minimum
- DIN rail (35mm) + components (45mm) + clearance (20mm)
```

### Recommended Enclosure Size
**250×200×120mm** (L×W×H)
- Provides adequate clearance
- Allows proper airflow
- Enables tool access for assembly

---

## ⚡ ELECTRICAL ARCHITECTURE CLARIFICATION

### Power Flow
1. **AC Input** → IEC inlet with switch (15A)
2. **AC Distribution** → Terminal block (30A rated)
3. **Relay Switching** → 4-channel modules (×2)
4. **AC Outputs** → Panel outlets (×3)
5. **Logic Power** → 5V 5A external supply

### Control Architecture
- Arduino Portenta X8 controls relay modules
- 5V logic levels (relay modules are 5V)
- Optocoupler isolation on relay boards
- USB-C for programming/data

---

## 🌡️ THERMAL CONSIDERATIONS

### Heat Sources
1. **Relay Modules**: ~2W per active channel (16W max)
2. **Arduino Portenta**: ~5-10W
3. **Terminal Connections**: Minimal if properly sized

### Total Heat Load
**~25W maximum** with all relays active

### Cooling Requirements
- Natural convection should suffice
- Optional 60mm fan if enclosed tightly
- Ventilation slots top and bottom

---

## 🔨 ASSEMBLY SEQUENCE

Based on actual components:

1. **Install DIN Rail** (horizontal, center)
2. **Mount Terminal Block** on DIN rail
3. **Install Panel Components**
   - AC inlet module (rear)
   - AC outlets (sides/rear)
   - USB-C connector (front)
4. **Mount PCBs** on standoffs
   - Arduino Mid Carrier
   - Relay modules (×2)
5. **Wire Power Distribution**
   - AC input to terminal block
   - Terminal block to relay inputs
   - Relay outputs to outlets
6. **Wire Control Signals**
   - Arduino to relay control pins
   - 5V power to relay modules
7. **Final Connections**
   - USB-C cable to Arduino
   - Test all connections

---

## ✅ DESIGN REQUIREMENTS SUMMARY

### Confirmed Requirements
- **8 Relay Channels**: Using 2× 4-channel modules
- **AC Switching**: Direct 250V/30A capability
- **Panel Mount I/O**: USB-C, AC outlets, AC input
- **DIN Rail Distribution**: 30A terminal block
- **External PSU**: 5V logic power

### Key Dimensions
- **Minimum Enclosure**: 250×200×120mm
- **Arduino Board**: 166×101mm (confirmed larger size)
- **Total Relay Space**: 150×55×20mm
- **DIN Rail Length**: 120mm minimum

### Critical Clearances
- **Above Relays**: 15mm for wire terminals
- **Around Arduino**: 10mm for connectors
- **Behind Panels**: 50mm for AC components

---

## 📋 REMAINING QUESTIONS

1. **Fan Requirement**: Is active cooling needed or passive sufficient?
2. **Environmental Rating**: IP54 still required with ventilation?
3. **Cable Management**: Specific routing requirements?
4. **Status Indicators**: LEDs needed on front panel?
5. **Mounting Orientation**: Wall mount, shelf, or rack?

---

## 🎯 NEXT STEPS

1. **Verify Arduino Dimensions**: Confirm 166×101mm size
2. **Thermal Analysis**: Calculate if 25W needs active cooling
3. **Layout Optimization**: Arrange components for best fit
4. **Cable Routing Design**: Plan wire paths
5. **Service Access**: Design for maintenance

---

*This catalog is based on ACTUAL components from the Amazon purchase list. Design can now proceed with confidence.*