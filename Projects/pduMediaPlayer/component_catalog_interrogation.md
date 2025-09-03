# CRITICAL COMPONENT CATALOG INTERROGATION
## PDU Media Player Enclosure - COMPLETE SPECIFICATION REQUIRED
*WARNING: No design work proceeds until EVERY field is completed*

---

## ⚠️ CRITICAL DESIGN BLOCKER ⚠️

**The following information MUST be provided with EXACT specifications before any CAD work begins. Approximations will lead to expensive failures.**

Based on analysis of existing documentation, we have CONFLICTING and INCOMPLETE component specifications:
- Requirements Blueprint mentions different dimensions than Gabe's specifications
- Arduino Mid Carrier mentioned as 114×86.5mm in Gabe's doc, but 166×101mm elsewhere
- No actual component datasheets or verified dimensions
- Missing critical mounting information

---

## A. POWER COMPONENTS - EXACT SPECIFICATIONS REQUIRED

### 1. AC POWER SUPPLY UNIT (PSU)
| Parameter | Requirements Doc | Gabe's Doc | ACTUAL (REQUIRED) |
|-----------|------------------|------------|-------------------|
| **Manufacturer/Model** | MeanWell-style | Not specified | ? |
| **Dimensions (L×W×H)** | 110×70×40mm | Not specified | ? |
| **Weight** | Not specified | Not specified | ? |
| **Input Voltage** | 240V AC | Not specified | ? |
| **Output** | 12V@10A | Not specified | ? |
| **Mounting Method** | Not specified | Not specified | □ DIN Rail □ Screw Mount □ Other: |
| **Mounting Hardware** | Not specified | Not specified | ? |
| **Terminal Locations** | Not specified | Not specified | ? |
| **Cooling Requirements** | 15W dissipation | Not specified | ? |
| **Safety Certifications** | Not specified | Not specified | ? |

### 2. AC INPUT CONNECTOR
| Parameter | Specification Required |
|-----------|------------------------|
| **Type** | □ IEC C14 □ Terminal Block □ Hardwired □ Other: |
| **Dimensions** | ? |
| **Mounting** | □ Snap-in □ Screw flange □ Other: |
| **Cutout Required** | ? |
| **Depth Behind Panel** | ? |

### 3. CIRCUIT BREAKER/SWITCH
| Parameter | Specification Required |
|-----------|------------------------|
| **Type** | □ Circuit Breaker □ Rocker Switch □ Both □ Other: |
| **Current Rating** | ? |
| **Voltage Rating** | ? |
| **Panel Cutout** | ? |
| **Mounting Depth** | ? |
| **Illuminated?** | □ Yes □ No |

### 4. TERMINAL BLOCKS
| Parameter | Requirements Doc | ACTUAL (REQUIRED) |
|-----------|------------------|-------------------|
| **Manufacturer/Series** | Not specified | ? |
| **Number of Positions** | 20 minimum | ? |
| **Pitch (spacing)** | Not specified | ? |
| **Current Rating** | 10A per position | ? |
| **Voltage Rating** | 240V | ? |
| **Wire Size Range** | Not specified | ? |
| **Mounting** | Not specified | □ DIN Rail □ Screw Mount □ Other: |
| **Connection Type** | Tool-free preferred | □ Screw □ Spring □ Push-in |
| **Total Length** | Not specified | ? |

---

## B. CONTROL & RELAY COMPONENTS

### 5. 8-CHANNEL RELAY BOARD
| Parameter | Requirements Doc | Gabe's Doc | ACTUAL (REQUIRED) |
|-----------|------------------|------------|-------------------|
| **Manufacturer/Model** | Not specified | Not specified | ? |
| **PCB Dimensions** | 170×80×35mm | Not specified | ? |
| **Mounting Holes** | Not specified | Not specified | Position: ? Size: ? |
| **Component Height Top** | Part of 35mm? | Not specified | ? |
| **Component Height Bottom** | Not specified | Not specified | ? |
| **Power Requirements** | 12V@0.5A/relay | Not specified | ? |
| **Input Connector** | Not specified | Not specified | Type: ? Location: ? |
| **Output Terminals** | Not specified | Not specified | Type: ? Location: ? |
| **Heat Dissipation** | 8W maximum | Not specified | ? |
| **Relay Contact Rating** | Not specified | Not specified | ? |

### 6. ARDUINO PORTENTA MID CARRIER
| Parameter | Requirements Doc | Gabe's Doc | ACTUAL (REQUIRED) |
|-----------|------------------|------------|-------------------|
| **Board Dimensions** | Not specified | 114×86.5mm | ? (CONFLICT: 166×101mm mentioned) |
| **Mounting Holes** | Not specified | 4×3mm (M3) | Pattern: ? |
| **With Portenta X8 Height** | Not specified | Not specified | ? |
| **Standoff Height Required** | Not specified | 5mm | ? |
| **Power Connector** | Not specified | Not specified | Type: ? Location: ? |
| **USB Connectors** | Not specified | Not specified | Type: ? Qty: ? Location: ? |
| **Network Connector** | Not specified | Not specified | □ RJ45 onboard □ External |
| **Antenna Connectors** | Not specified | Not specified | Type: ? Qty: ? |
| **Heat Sink** | Not specified | Not specified | Size: ? Height: ? |

### 7. CONTROL LOGIC BOARD (Additional?)
| Parameter | Requirements Doc | ACTUAL (REQUIRED) |
|-----------|------------------|-------------------|
| **Purpose** | Listed separately | ? (Same as Arduino or different?) |
| **Dimensions** | 150×100×20mm | ? |
| **Power** | 12V@1A | ? |
| **Heat Dissipation** | 5W | ? |
| **Mounting** | Not specified | ? |

---

## C. THERMAL MANAGEMENT

### 8. COOLING FAN
| Parameter | Requirements Doc | ACTUAL (REQUIRED) |
|-----------|------------------|-------------------|
| **Size** | 60mm | ? |
| **Thickness** | Not specified | ? |
| **Voltage** | Not specified | □ 12V □ 24V □ Other: |
| **CFM Rating** | Not specified | ? |
| **Noise Level** | <35dB target | ? |
| **Mounting** | Not specified | □ 4 screws (pattern?) □ Other: |
| **Connector Type** | Not specified | □ 2-pin □ 3-pin □ 4-pin PWM |
| **Direction** | Exhaust implied | □ Intake □ Exhaust |

### 9. TEMPERATURE SENSORS (If Any)
| Parameter | Specification Required |
|-----------|------------------------|
| **Type** | ? |
| **Quantity** | ? |
| **Mounting** | ? |
| **Interface** | ? |

---

## D. EXTERNAL CONNECTORS & INTERFACES

### 10. AC OUTPUT OUTLETS (If Any)
| Parameter | Specification Required |
|-----------|------------------------|
| **Type** | □ NEMA 5-15R □ IEC C13 □ Terminal □ Other: |
| **Quantity** | ? |
| **Mounting** | □ Panel mount □ Through-wall □ Other: |
| **Dimensions** | ? |

### 11. DATA CONNECTORS
| Parameter | Specification Required |
|-----------|------------------------|
| **Ethernet** | □ Panel mount RJ45 □ Cable gland □ None |
| **USB Type-A** | Quantity: ? Purpose: ? |
| **USB Type-C** | Quantity: ? Purpose: ? |
| **Serial (DB9)** | □ Yes □ No |
| **Other** | ? |

### 12. ANTENNA CONNECTIONS
| Parameter | Specification Required |
|-----------|------------------------|
| **Cellular** | □ SMA □ RP-SMA □ U.FL to external □ None |
| **WiFi** | □ SMA □ RP-SMA □ U.FL to external □ Internal |
| **GPS** | □ SMA □ Active antenna □ None |
| **Mounting** | □ Bulkhead □ Flying lead □ Other: |

### 13. STATUS INDICATORS
| Parameter | Specification Required |
|-----------|------------------------|
| **Power LED** | □ Yes □ No - Color: ? Size: ? |
| **Status LEDs** | Quantity: ? Purpose: ? |
| **Display** | □ LCD □ OLED □ None - Size: ? |
| **Mounting** | ? |

---

## E. MOUNTING & STRUCTURAL

### 14. DIN RAIL (If Used)
| Parameter | Specification Required |
|-----------|------------------------|
| **Rail Type** | □ 35mm standard □ Other: |
| **Orientation** | □ Horizontal □ Vertical |
| **Length Required** | ? |
| **Components on Rail** | List: |

### 15. CABLE SPECIFICATIONS
| Parameter | Specification Required |
|-----------|------------------------|
| **AC Power Cable** | Gauge: ? Length: ? |
| **DC Power Distribution** | Gauge: ? Qty: ? |
| **Inter-board Cables** | Types: ? Lengths: ? |
| **Antenna Cables** | Type: ? Length: ? |

---

## F. CRITICAL ASSEMBLY QUESTIONS

### SPATIAL RELATIONSHIPS - MUST ANSWER ALL
1. **Which component mounts FIRST?** 
2. **Can relay board be installed AFTER terminal blocks?**
3. **Does PSU block access to anything when installed?**
4. **Can all screws be accessed with components in place?**
5. **What is the MINIMUM spacing between PSU and relay board?**
6. **Do any connectors face the enclosure walls?**
7. **Are there any components on the BOTTOM of PCBs?**
8. **What clearance is needed for cable bend radius?**

### THERMAL RELATIONSHIPS
1. **What is the hottest component?**
2. **Can PSU and relay board touch?**
3. **Does Arduino need direct airflow?**
4. **Are there any temperature-sensitive components?**

### SERVICE ACCESS
1. **Which component fails most often?**
2. **Which connections need frequent access?**
3. **Can components be hot-swapped?**
4. **What test points need access?**

---

## G. MISSING CRITICAL INFORMATION

### URGENT CLARIFICATIONS NEEDED
1. **MID CARRIER CONFUSION**: Documentation shows 114×86.5mm AND 166×101mm - WHICH IS CORRECT?
2. **"CONTROL LOGIC BOARD"**: Is this the Arduino or a SEPARATE board?
3. **AC SWITCHING**: Do relays switch AC directly or through separate contactors?
4. **CERTIFICATION**: Exact standards? (UL 508A? CE? CSA?)
5. **ENVIRONMENTAL**: IP54 mentioned - dust/water from which directions?

### DOCUMENTATION REQUIRED
- [ ] **Component datasheets** (ALL components)
- [ ] **Electrical schematic** (Readable version of ASX00055.PDF)
- [ ] **Wiring diagram** (Showing all connections)
- [ ] **3D models or STEP files** of major components
- [ ] **Assembly sequence** from existing prototype
- [ ] **Photos** of current prototype/layout

---

## H. COMPLETE COMPONENT TABLE - FILL ALL FIELDS

| Component | Qty | Exact Dimensions | Mount Type | Mount Hardware | Wire Space | Critical Notes |
|-----------|-----|------------------|------------|----------------|------------|----------------|
| PSU | 1 | ?×?×? | ? | ? | ? | REQUIRED |
| Relay Board | 1 | ?×?×? | ? | ? | ? | REQUIRED |
| Mid Carrier | 1 | ?×?×? | ? | ? | ? | REQUIRED |
| Control Board | ? | ?×?×? | ? | ? | ? | REQUIRED |
| Terminal Blocks | ? | ?×?×? | ? | ? | ? | REQUIRED |
| Circuit Breaker | ? | ?×?×? | ? | ? | ? | REQUIRED |
| AC Input | 1 | ?×?×? | ? | ? | ? | REQUIRED |
| Fan | 1 | ?×?×? | ? | ? | ? | REQUIRED |
| DIN Rail | ? | ?×?×? | ? | ? | ? | IF USED |
| Indicators | ? | ?×?×? | ? | ? | ? | IF USED |

---

## ❌ DESIGN BLOCKERS - CANNOT PROCEED WITHOUT:

1. **EXACT component dimensions with manufacturer part numbers**
2. **CLEAR understanding of Arduino board size (114mm or 166mm?)**
3. **MOUNTING method for each component**
4. **SPATIAL arrangement confirmation**
5. **CABLE routing requirements**
6. **THERMAL dissipation per component**
7. **ACCESS requirements for service**

## 🛑 STOP REQUIREMENTS

**DO NOT BEGIN CAD DESIGN UNTIL:**
- [ ] Every "?" in this document is replaced with actual values
- [ ] All dimension conflicts are resolved
- [ ] Mounting strategies are confirmed
- [ ] Assembly sequence is validated
- [ ] Component datasheets are provided

---

## NEXT ACTIONS REQUIRED FROM CLIENT:

1. **PROVIDE** complete component list with manufacturer part numbers
2. **CLARIFY** the Arduino board actual dimensions
3. **CONFIRM** if "Control Logic Board" is separate from Arduino
4. **SUPPLY** datasheets or 3D models for all components
5. **DESCRIBE** current working prototype if it exists
6. **DEFINE** exact assembly sequence preferred

**COST OF AMBIGUITY**: Every assumption that proves wrong in production will cost:
- Design rework: 20-40 hours
- Prototype iterations: $2,000-5,000
- Production delays: 2-4 weeks
- Potential unit failures: $2,000 per unit in electronics damage

**THIS DOCUMENT MUST BE 100% COMPLETE BEFORE DESIGN PHASE**

---

*Document Generated: 2025-09-02*
*Status: AWAITING CRITICAL INFORMATION*
*Risk Level: EXTREME - Cannot proceed without specifications*