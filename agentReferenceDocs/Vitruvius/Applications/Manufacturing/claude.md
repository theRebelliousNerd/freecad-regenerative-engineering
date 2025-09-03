# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Manufacturing Directory - Industrial Human Factors Cable Network

## JITC Framework for Industrial Human Factors

This directory contains knowledge modules for factory design, worker safety, production ergonomics, assembly processes, and all aspects of human factors in manufacturing environments. These modules define the critical "industrial cables" that connect worker capabilities and limitations to production system design.

### Manufacturing Cable Network

Industrial human factors create five primary cable types:

1. **Strength Cables** - Human force capabilities to lifting, pushing, tool operation
2. **Postural Cables** - Human biomechanics to work heights, reach, repetitive motion
3. **Environmental Cables** - Human tolerance to noise, vibration, temperature, lighting
4. **Cognitive Cables** - Human attention, decision-making to process complexity
5. **Safety Cables** - Injury prevention to all system design decisions

### Critical Manufacturing Cable Dependencies

#### Strength Cable Network
**Cable Sources**: Human strength capabilities (5th-95th percentile)
**Cable Destinations**: Tool weight, lifting requirements, force needed for operations

**Breaking Points**:
- Lifting >23kg without assistance (NIOSH guidelines)
- Push/pull forces >25kg initial, >10kg sustained
- Grip forces >30% of individual maximum for sustained work
- Tool weight >2.3kg for precision work, >4.5kg for general work

**Anthropometric Data Cables**:
```python
strength_limits = {
    'lifting_occasional': {'male_95%': 35, 'female_5%': 14},  # kg
    'lifting_frequent': {'male_95%': 23, 'female_5%': 9},    # kg  
    'grip_strength': {'male_95%': 500, 'female_5%': 220},    # N
    'push_force_initial': {'male_95%': 400, 'female_5%': 180}, # N
    'push_force_sustained': {'male_95%': 200, 'female_5%': 90}  # N
}
```

#### Postural Cable Network
**Cable Sources**: Human joint limits, biomechanical stress tolerance
**Cable Destinations**: Workstation height, reach distances, tool orientation

**Breaking Points**:
- Work above shoulder height (>1600mm for 5th percentile female)
- Forward reach beyond 600mm from body
- Sustained awkward postures (RULA scores >4)
- Repetitive motions >4/minute without variation

**Postural Assessment Integration**:
```python
def assess_postural_cables(workstation_design):
    """RULA/REBA integration for postural cable verification"""
    
    rula_scores = {
        'upper_arm': calculate_upper_arm_score(workstation_design.reach_distance),
        'lower_arm': calculate_lower_arm_score(workstation_design.tool_position),
        'wrist': calculate_wrist_score(workstation_design.wrist_angle),
        'neck': calculate_neck_score(workstation_design.visual_angle),
        'trunk': calculate_trunk_score(workstation_design.work_height)
    }
    
    final_score = calculate_final_rula_score(rula_scores)
    
    return {
        'acceptable': final_score <= 2,
        'investigate': 3 <= final_score <= 4,
        'change_required': final_score >= 5,
        'detailed_scores': rula_scores
    }
```

#### Environmental Cable Network
**Cable Sources**: Human physiological and psychological tolerance limits
**Cable Destinations**: Noise control, vibration isolation, climate control, illumination

**Breaking Points**:
- Noise levels >85 dBA (8-hour exposure limit)
- Vibration >2.5 m/s² hand-arm, >0.5 m/s² whole-body
- Temperature outside 18-24°C comfort zone
- Illumination <500 lux for detailed work, <200 lux for general work

### Manufacturing-Specific Cable Tracing

#### Assembly Cable Network
1. **Vision Cable**: Part identification → lighting requirements (500-1000 lux)
2. **Precision Cable**: Assembly tolerance → tool design and work surface stability
3. **Sequence Cable**: Assembly steps → cognitive load and error prevention
4. **Time Cable**: Production rate → realistic human performance limits

#### Machine Operation Cables
1. **Control Cable**: Human reaction time (250-500ms) → emergency stop accessibility
2. **Feedback Cable**: Machine status → clear visual/audio indicators
3. **Maintenance Cable**: Service access → human body dimensions and tool clearance
4. **Safety Cable**: Hazard exposure → guarding and safety systems

#### Material Handling Cables
1. **Weight Cable**: Item mass → lifting aid requirements
2. **Size Cable**: Item dimensions → grip design and carrying methods
3. **Frequency Cable**: Handling rate → rotation and rest break needs
4. **Distance Cable**: Transport length → mechanical aid requirements

### Just-in-Time Loading Patterns

#### High Uncertainty Triggers (Load Immediately)
```python
manufacturing_uncertainty_signals = [
    "worker_injury_risk",
    "repetitive_strain_concerns", 
    "lifting_weight_limits",
    "workstation_height_questions",
    "assembly_error_rates",
    "production_rate_feasibility",
    "safety_compliance_industrial",
    "environmental_exposure_limits"
]
```

#### Context-Specific Loading
- **Ergonomic Assessment**: Load when designing workstations or job tasks
- **Safety Analysis**: Load when machinery involves human interaction
- **Productivity Optimization**: Load when balancing human capabilities with targets
- **Compliance Verification**: Load when validating against OSHA/industry standards

### Integration Cables to Other Agents

**→ Brunel**: Structural requirements for lifting equipment, workstation support
**→ Watt**: Environmental control systems (HVAC, noise control) 
**→ Edison**: Control systems for human-machine interfaces
**→ Gabe**: DFM considerations for human assembly processes
**→ Tesla**: Motor systems designed for human interaction/safety
**→ Curie**: Material selection for tool handles, work surfaces, safety equipment

### Manufacturing Safety Cable Protocol

```python
def verify_manufacturing_safety_cables():
    """Critical safety cable integrity verification"""
    
    safety_checks = {
        'machinery_guarding': verify_pinch_point_protection(),
        'emergency_stops': verify_emergency_stop_reach(),  # <610mm from any position
        'hazardous_energy': verify_lockout_tagout_access(),
        'lifting_aids': verify_weight_limit_compliance(),
        'personal_protection': verify_ppe_requirements(),
        'environmental_controls': verify_exposure_limits()
    }
    
    critical_failures = [check for check, passed in safety_checks.items() if not passed]
    
    return {
        'safety_approved': len(critical_failures) == 0,
        'critical_failures': critical_failures,
        'immediate_action_required': len(critical_failures) > 0
    }
```

### Industrial Standards Cable Network

#### Regulatory Compliance Cables
- **OSHA Standards**: 29 CFR 1910 - General Industry Safety
- **NIOSH Guidelines**: Lifting equation and ergonomic recommendations  
- **ISO 11228**: Ergonomics - Manual handling
- **ISO 14738**: Safety of machinery - Anthropometric requirements

#### Industry-Specific Cables
- **Automotive**: Specific assembly and safety requirements
- **Electronics**: ESD protection and precision work considerations
- **Food Processing**: Hygiene and contamination prevention
- **Pharmaceutical**: Clean room and precision requirements

### Metacognitive Patterns for Manufacturing

**High Confidence** (Well-established knowledge):
- Basic lifting limits and NIOSH equation application
- Standard workstation height recommendations
- Common RULA/REBA assessment procedures

**Uncertainty Triggers** (Require knowledge retrieval):
- Industry-specific safety requirements
- Novel manufacturing processes or technologies
- Complex multi-task workstation design
- Unusual environmental conditions or constraints

### Failure Mode Prevention

**Common Manufacturing Cable Breaks**:
1. **Strength Overload**: Requiring forces beyond human capabilities
2. **Postural Stress**: Sustained awkward positions causing MSDs  
3. **Cognitive Overload**: Too many decisions or steps in process
4. **Environmental Stress**: Noise, temperature, or lighting beyond tolerance
5. **Safety Gap**: Inadequate protection from machinery hazards

**Cable Repair Strategies**:
- Mechanical aids for strength limitations
- Workstation redesign for postural improvements  
- Process simplification for cognitive load
- Environmental controls for comfort/safety
- Engineering controls for hazard elimination

Remember: Manufacturing human factors are about protecting workers while maintaining productivity. Every industrial process creates cables connecting human capabilities to system requirements. Breaking these cables doesn't just reduce efficiency - it injures real people. Design with human limitations as immutable constraints, not obstacles to overcome.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!