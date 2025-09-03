# Component Database - Edison Reference Data 2024-2025

## Power Semiconductors Database

### Power MOSFETs (N-Channel)

#### Low Voltage (<100V)
```json
{
  "BSC016N06NS": {
    "manufacturer": "Infineon",
    "package": "SuperSO8",
    "specifications": {
      "vds_max": {"value": 60, "unit": "V"},
      "id_continuous": {"value": 100, "unit": "A"},
      "rds_on_typ": {"value": 1.6, "unit": "mOhm", "conditions": "Vgs=10V"},
      "qg_typ": {"value": 38, "unit": "nC"},
      "ciss": {"value": 3900, "unit": "pF"}
    },
    "thermal": {
      "rth_jc": {"value": 0.45, "unit": "C/W"},
      "tj_max": {"value": 175, "unit": "C"}
    },
    "applications": ["synchronous_rectification", "motor_drives", "battery_management"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 16,
      "second_sources": ["IRFB4115PBF", "STP75NF75"]
    }
  },
  "IRFB4115PBF": {
    "manufacturer": "Vishay",
    "package": "TO-220AB",
    "specifications": {
      "vds_max": {"value": 150, "unit": "V"},
      "id_continuous": {"value": 104, "unit": "A"},
      "rds_on_typ": {"value": 8.7, "unit": "mOhm", "conditions": "Vgs=10V"},
      "qg_typ": {"value": 180, "unit": "nC"},
      "ciss": {"value": 6400, "unit": "pF"}
    },
    "thermal": {
      "rth_jc": {"value": 0.36, "unit": "C/W"},
      "tj_max": {"value": 175, "unit": "C"}
    },
    "applications": ["switching_power_supplies", "motor_drives", "lighting"],
    "availability": {
      "status": "Active", 
      "lead_time_weeks": 12,
      "second_sources": ["STP140NF75", "IXFN140N75X2"]
    }
  }
}
```

#### High Voltage (>600V)
```json
{
  "IPW60R125CP": {
    "manufacturer": "Infineon",
    "package": "TO-247",
    "technology": "CoolMOS_C6",
    "specifications": {
      "vds_max": {"value": 650, "unit": "V"},
      "id_continuous": {"value": 23, "unit": "A"},
      "rds_on_typ": {"value": 125, "unit": "mOhm", "conditions": "Vgs=10V"},
      "qg_typ": {"value": 46, "unit": "nC"},
      "eoss": {"value": 45, "unit": "uJ"}
    },
    "thermal": {
      "rth_jc": {"value": 0.83, "unit": "C/W"},
      "tj_max": {"value": 150, "unit": "C"}
    },
    "applications": ["pfc_circuits", "llc_resonant", "hard_switching"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 20,
      "second_sources": ["STP23NM60N", "FCH041N60E"]
    }
  }
}
```

### IGBTs (Insulated Gate Bipolar Transistors)

```json
{
  "IRGB4062D": {
    "manufacturer": "Infineon",
    "package": "TO-263",
    "specifications": {
      "vces": {"value": 600, "unit": "V"},
      "ic_continuous": {"value": 24, "unit": "A"},
      "vce_sat_typ": {"value": 1.65, "unit": "V", "conditions": "Vge=15V, Ic=12A"},
      "switching_times": {
        "turn_on": {"value": 19, "unit": "ns"},
        "turn_off": {"value": 39, "unit": "ns"}
      }
    },
    "thermal": {
      "rth_jc": {"value": 1.45, "unit": "C/W"},
      "tj_max": {"value": 150, "unit": "C"}
    },
    "applications": ["motor_drives", "ups", "welding"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 24,
      "second_sources": ["FGH40N60SFD", "GT40Q321"]
    }
  }
}
```

## Microcontrollers Database

### ARM Cortex-M Series

```json
{
  "STM32F407VGT6": {
    "manufacturer": "STMicroelectronics",
    "core": "ARM_Cortex_M4F",
    "package": "LQFP100",
    "specifications": {
      "clock_frequency": {"max": 168, "unit": "MHz"},
      "flash_memory": {"value": 1024, "unit": "kB"},
      "sram": {"value": 192, "unit": "kB"},
      "gpio_pins": 82,
      "operating_voltage": {"min": 1.8, "max": 3.6, "unit": "V"}
    },
    "peripherals": {
      "timers": {
        "advanced": 2,
        "general_purpose": 10,
        "basic": 2
      },
      "communication": {
        "usart": 4,
        "uart": 2,
        "spi": 3,
        "i2c": 3,
        "can": 2,
        "usb_otg": 2
      },
      "analog": {
        "adc_12bit": 3,
        "dac_12bit": 2,
        "comparators": 0
      }
    },
    "applications": ["motor_control", "industrial_automation", "consumer_electronics"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 26,
      "second_sources": ["TM4C1294NCPDT", "MK66FN2M0VLQ18"]
    }
  },
  "ESP32-WROOM-32E": {
    "manufacturer": "Espressif",
    "core": "Dual_Xtensa_LX6",
    "package": "Module",
    "specifications": {
      "clock_frequency": {"max": 240, "unit": "MHz"},
      "flash_memory": {"value": 4, "unit": "MB"},
      "sram": {"value": 520, "unit": "kB"},
      "gpio_pins": 26,
      "operating_voltage": {"min": 3.0, "max": 3.6, "unit": "V"}
    },
    "wireless": {
      "wifi": "802.11_b/g/n",
      "bluetooth": "v4.2_BR/EDR_and_BLE",
      "antenna": "pcb_trace_antenna"
    },
    "peripherals": {
      "adc": {"resolution": 12, "channels": 18},
      "dac": {"resolution": 8, "channels": 2},
      "touch_sensors": 10,
      "pwm_channels": 16
    },
    "applications": ["iot_devices", "smart_home", "wearables"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 8,
      "second_sources": ["ESP32-S3-WROOM-1"]
    }
  }
}
```

## Power Management ICs

### DC-DC Controllers

```json
{
  "LTC3891": {
    "manufacturer": "Analog_Devices",
    "topology": "synchronous_buck",
    "package": "QFN20",
    "specifications": {
      "input_voltage": {"min": 4, "max": 60, "unit": "V"},
      "output_voltage": {"min": 0.8, "max": 24, "unit": "V"},
      "switching_frequency": {"min": 50, "max": 900, "unit": "kHz"},
      "output_current": {"max": 20, "unit": "A"}
    },
    "features": [
      "current_mode_control",
      "programmable_soft_start",
      "overcurrent_protection",
      "thermal_shutdown"
    ],
    "applications": ["automotive", "industrial", "telecom"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 18,
      "second_sources": ["TPS54560", "MP2145"]
    }
  },
  "TPS54560": {
    "manufacturer": "Texas_Instruments",
    "topology": "synchronous_buck",
    "package": "HTSSOP20",
    "specifications": {
      "input_voltage": {"min": 4.5, "max": 60, "unit": "V"},
      "output_voltage": {"min": 0.76, "max": 52, "unit": "V"},
      "switching_frequency": {"typ": 570, "unit": "kHz"},
      "output_current": {"max": 5, "unit": "A"}
    },
    "features": [
      "eco_mode_operation",
      "adjustable_switching_frequency",
      "enable_and_tracking",
      "power_good_output"
    ],
    "applications": ["industrial", "automotive", "communications"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 12,
      "second_sources": ["LTC3891", "LT8645S"]
    }
  }
}
```

### Linear Regulators

```json
{
  "AMS1117-3.3": {
    "manufacturer": "Advanced_Monolithic_Systems",
    "type": "low_dropout_regulator",
    "package": "SOT223",
    "specifications": {
      "input_voltage": {"min": 4.75, "max": 15, "unit": "V"},
      "output_voltage": {"value": 3.3, "tolerance": 1, "unit": "V_%"},
      "output_current": {"max": 1, "unit": "A"},
      "dropout_voltage": {"typ": 1.3, "unit": "V"},
      "line_regulation": {"typ": 0.2, "unit": "%"},
      "load_regulation": {"typ": 0.4, "unit": "%"}
    },
    "applications": ["general_purpose", "microcontroller_supply", "sensor_power"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 4,
      "second_sources": ["LD1117V33", "LP2950-3.3"]
    }
  }
}
```

## Passive Components Database

### Resistors

```json
{
  "RC0603JR-071KL": {
    "manufacturer": "Yageo",
    "type": "chip_resistor",
    "package": "0603",
    "specifications": {
      "resistance": {"value": 1000, "unit": "ohm"},
      "tolerance": {"value": 5, "unit": "percent"},
      "power_rating": {"value": 0.1, "unit": "W"},
      "voltage_rating": {"value": 75, "unit": "V"},
      "temp_coefficient": {"value": 200, "unit": "ppm/C"}
    },
    "operating_conditions": {
      "temperature_range": {"min": -55, "max": 155, "unit": "C"},
      "humidity": {"max": 95, "unit": "percent_RH"}
    },
    "applications": ["general_purpose", "pull_up_down", "current_limiting"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 2,
      "second_sources": ["CRCW06031K00FKEA", "ERJ-3EKF1001V"]
    }
  }
}
```

### Capacitors

```json
{
  "C0603X7R1C104K030BA": {
    "manufacturer": "TDK",
    "type": "ceramic_capacitor",
    "dielectric": "X7R",
    "package": "0603",
    "specifications": {
      "capacitance": {"value": 0.1, "unit": "uF"},
      "tolerance": {"value": 10, "unit": "percent"},
      "voltage_rating": {"value": 16, "unit": "V"},
      "temperature_range": {"min": -55, "max": 125, "unit": "C"},
      "temperature_coefficient": "±15%_over_temp_range"
    },
    "electrical_properties": {
      "esr": {"value": 0.025, "unit": "ohm", "frequency": "100kHz"},
      "self_resonant_frequency": {"typ": 32, "unit": "MHz"}
    },
    "applications": ["decoupling", "filtering", "timing"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 4,
      "second_sources": ["GRM188R71C104KA01D", "CC0603KRX7R9BB104"]
    }
  },
  "UWX1A101MCL1GB": {
    "manufacturer": "Nichicon",
    "type": "aluminum_electrolytic",
    "package": "radial_leaded",
    "specifications": {
      "capacitance": {"value": 100, "unit": "uF"},
      "tolerance": {"value": 20, "unit": "percent"},
      "voltage_rating": {"value": 10, "unit": "V"},
      "esr": {"max": 2.6, "unit": "ohm", "frequency": "100kHz"},
      "ripple_current": {"value": 105, "unit": "mA", "frequency": "100kHz"}
    },
    "physical": {
      "diameter": {"value": 5, "unit": "mm"},
      "height": {"value": 11, "unit": "mm"},
      "lead_spacing": {"value": 2, "unit": "mm"}
    },
    "applications": ["power_supply_filtering", "audio_coupling", "energy_storage"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 8,
      "second_sources": ["ECA-1AM101", "25V100"]
    }
  }
}
```

### Inductors

```json
{
  "SRP7028A-4R7M": {
    "manufacturer": "Bourns",
    "type": "power_inductor",
    "core_material": "ferrite",
    "package": "7.3x6.6x2.8mm",
    "specifications": {
      "inductance": {"value": 4.7, "unit": "uH", "tolerance": 20},
      "saturation_current": {"value": 4.5, "unit": "A"},
      "rms_current": {"value": 3.9, "unit": "A"},
      "dc_resistance": {"max": 43, "unit": "mOhm"},
      "self_resonant_frequency": {"min": 30, "unit": "MHz"}
    },
    "applications": ["dc_dc_converters", "power_supplies", "automotive"],
    "availability": {
      "status": "Active", 
      "lead_time_weeks": 14,
      "second_sources": ["XAL7030-472ME", "IHLP2525CZER4R7M01"]
    }
  }
}
```

## Connectors Database

```json
{
  "22-28-4020": {
    "manufacturer": "Molex",
    "series": "Mini-Fit_Jr",
    "type": "wire_to_board",
    "specifications": {
      "positions": 2,
      "pitch": {"value": 4.2, "unit": "mm"},
      "current_rating": {"value": 9, "unit": "A"},
      "voltage_rating": {"value": 600, "unit": "V"},
      "wire_gauge": "18-24_AWG",
      "operating_temperature": {"min": -40, "max": 105, "unit": "C"}
    },
    "mating_connector": "22-01-3027",
    "applications": ["power_connections", "automotive", "industrial"],
    "availability": {
      "status": "Active",
      "lead_time_weeks": 6,
      "second_sources": ["640456-2", "43045-0200"]
    }
  }
}
```

## Component Selection Algorithms

### Power MOSFET Selection
```python
def select_power_mosfet(requirements):
    selection_criteria = {
        "voltage_rating": requirements['max_voltage'] * 1.5,  # 50% derating
        "current_rating": requirements['max_current'] * 1.3,  # 30% derating
        "rds_on_max": calculate_max_rds_on(requirements),
        "package_thermal": requirements['thermal_requirements'],
        "switching_frequency": requirements['switching_freq']
    }
    
    candidates = filter_components(power_mosfet_database, selection_criteria)
    
    # Optimization criteria
    optimization_weights = {
        "efficiency": 0.4,
        "cost": 0.3,
        "availability": 0.2,
        "thermal_performance": 0.1
    }
    
    return optimize_selection(candidates, optimization_weights)
```

### Decoupling Capacitor Selection
```python
def select_decoupling_capacitors(power_requirements):
    decoupling_strategy = {
        "bulk_capacitors": {
            "value_range": [47, 220],  # uF
            "type": "aluminum_electrolytic",
            "esr_requirement": "< 0.1_ohm_at_100kHz"
        },
        "ceramic_capacitors": {
            "values": [0.1, 1.0, 10.0],  # uF 
            "dielectric": "X7R_or_X5R",
            "voltage_derating": "50%_minimum"
        },
        "placement": {
            "bulk_distance": "< 20mm_from_power_input",
            "ceramic_distance": "< 5mm_from_IC_power_pins"
        }
    }
    
    return generate_decoupling_bom(power_requirements, decoupling_strategy)
```

*Edison's Component Philosophy: "The electric light has caused me the greatest amount of study and has required the most elaborate experiments." Every component selection requires systematic analysis of electrical, thermal, mechanical, and supply chain constraints.*