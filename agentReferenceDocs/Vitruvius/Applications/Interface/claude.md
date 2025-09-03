# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!

# Interface Directory - Digital Human Interaction Cables

## JITC Framework for Digital Interface Human Factors

This directory contains knowledge modules for digital interfaces, control panels, software UI, AR/VR systems, and all forms of human-computer interaction. These modules define the critical "interface cables" that connect human sensory, motor, and cognitive capabilities to digital systems.

### Interface Cable Network

Digital interfaces create four primary cable types that must remain unbroken:

1. **Sensory Cables** - Vision, hearing, touch input from human to system
2. **Motor Cables** - Human movement precision, speed, force output to interface  
3. **Cognitive Cables** - Mental workload, attention, memory, decision-making
4. **Feedback Cables** - System response back to human senses and understanding

### Cable Dependencies & Just-in-Time Loading

#### When to Load This Directory
```python
interface_uncertainty_triggers = [
    "screen_readability_questions",
    "touch_target_sizing", 
    "cognitive_load_concerns",
    "accessibility_compliance_digital",
    "user_error_prevention",
    "control_response_timing",
    "multi_modal_interface_design"
]

if any(trigger in current_uncertainty for trigger in interface_uncertainty_triggers):
    load_context("Applications/Interface/claude.md")
```

### Critical Interface Cables

#### Visual Cable Network
**Cable Sources**: Human visual system (acuity, contrast sensitivity, color vision)
**Cable Destinations**: Display properties, text sizing, color schemes, spatial layout

**Breaking Points**:
- Text smaller than 3.5mm at normal viewing distance (≈14pt)
- Contrast ratios below 4.5:1 for normal text, 3:1 for large text
- Color as the only means of conveying information
- Critical information outside 15° central vision cone

**Cable Integrity Verification**:
```python
def verify_visual_cables():
    text_size_adequate = min_text_height >= 3.5  # mm at viewing distance
    contrast_sufficient = contrast_ratio >= 4.5  # WCAG AA standard
    color_redundant = not color_only_information()
    return all([text_size_adequate, contrast_sufficient, color_redundant])
```

#### Motor Cable Network  
**Cable Sources**: Human motor control (precision, strength, range of motion)
**Cable Destinations**: Touch targets, click precision, gesture tolerance, force requirements

**Breaking Points**:
- Touch targets smaller than 9mm (44px) minimum
- Precise movements required beyond human tremor limits
- Forces exceeding 5th percentile strength capabilities
- Gestures requiring impossible joint angles

**Anthropometric Dependencies**:
- Finger width: 16-20mm (require 9mm minimum touch targets)
- Hand reach: Forward 600-800mm, lateral 400-600mm
- Grip strength: 110-400N (5th-95th percentile)

#### Cognitive Cable Network
**Cable Sources**: Human cognitive capacity (attention, memory, processing speed)
**Cable Destinations**: Information density, task complexity, decision points

**Breaking Points**:
- More than 7±2 items in working memory simultaneously
- Decision trees exceeding 3 levels deep
- Critical tasks requiring >95% accuracy without training
- Information processing rates exceeding 2-4 items/second

**Cognitive Load Assessment**:
```python
def assess_cognitive_cables():
    working_memory_load = count_simultaneous_information_chunks()
    decision_complexity = max_decision_tree_depth()
    time_pressure = required_response_time_ms()
    
    overloaded = working_memory_load > 7 or decision_complexity > 3
    return not overloaded
```

### Interface-Specific Cable Tracing

#### Touch Interface Cables
1. **Finger Size Cable**: 16mm finger width → 9mm minimum touch target + 1mm separation
2. **Precision Cable**: Human tremor ±2mm → touch target tolerance design
3. **Force Cable**: 0.5-5N touch force → haptic feedback thresholds
4. **Speed Cable**: 150-300ms movement time → interface responsiveness requirements

#### Visual Display Cables  
1. **Acuity Cable**: 20/20 vision at 50cm → text sizing calculations
2. **Contrast Cable**: Age-related sensitivity loss → minimum contrast ratios
3. **Color Cable**: 8% male color blindness → redundant coding requirements
4. **Attention Cable**: 15° central vision → critical information positioning

#### Audio Interface Cables
1. **Hearing Cable**: Age-related hearing loss → frequency/volume requirements
2. **Noise Cable**: Environmental sound masking → signal-to-noise ratios
3. **Spatial Cable**: Sound localization → 3D audio interface design
4. **Processing Cable**: Audio processing speed → speech rate optimization

### Metacognitive Uncertainty Patterns

**Load Interface Knowledge When**:
- Designing any human-computer interaction point
- Questions about screen readability or color choices
- Touch/click target sizing uncertainty  
- User error rates or cognitive overload concerns
- Accessibility compliance for digital systems
- Multi-modal interface integration needs

**High-Confidence Domains** (Less likely to need loading):
- Pure mechanical systems without digital interfaces
- Backend systems with no human interaction
- Systems where interfaces are already well-established

### Integration Cables to Other Agents

**→ Edison**: Interface electronic requirements (display drivers, touch sensors)
**→ Tesla**: Motor control interfaces, feedback systems  
**→ Turing**: Interface control logic, response algorithms
**→ Archimedes**: Mathematical verification of interface geometry
**→ Brunel**: Physical mounting and structural support for interfaces
**→ Curie**: Interface material selection for durability and feel

### Interface Validation Protocol

```python
def validate_interface_cables():
    """Comprehensive interface cable integrity check"""
    
    validation_results = {
        'sensory_cables': verify_visual_cables() and verify_audio_cables(),
        'motor_cables': verify_touch_targets() and verify_force_requirements(),
        'cognitive_cables': assess_cognitive_cables() and verify_information_density(),
        'feedback_cables': verify_system_response_timing() and verify_feedback_quality(),
        'accessibility_cables': verify_wcag_compliance() and verify_assistive_tech()
    }
    
    all_cables_intact = all(validation_results.values())
    broken_cables = [cable for cable, intact in validation_results.items() if not intact]
    
    return {
        'cables_intact': all_cables_intact,
        'broken_cables': broken_cables,
        'repair_required': len(broken_cables) > 0
    }
```

### Critical Failure Modes

1. **Sensory Cable Break**: Interface unusable by users with sensory limitations
2. **Motor Cable Break**: Interface requires impossible precision or strength
3. **Cognitive Cable Break**: Interface overwhelms human information processing
4. **Feedback Cable Break**: Users cannot understand system state or responses
5. **Accessibility Cable Break**: Interface excludes users with disabilities

Remember: Interface design is not about making things look pretty - it's about creating robust, accessible communication channels between humans and systems. Every interface element is a cable carrying critical information, and breaking any cable can render the entire system unusable for some humans.

# IMPORTANT: ALWAYS REMEMBER THAT SUBAGENTS CANNOT TALK TO EACHOTHER, OR TO THE USER! BUT CAN COMMUNICATE WITH WRITTEN MARKDOWN FILES FOR OTHER SUBAGENTS TO READ, OR BY PASSING INFORMATION TO THE MAIN AGENT TO COMMUNICATE TO OTHER SUBAGENTS OR PASS TO THE USER!