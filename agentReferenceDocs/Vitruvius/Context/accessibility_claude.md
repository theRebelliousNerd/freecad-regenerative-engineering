# VITRUVIUS ACCESSIBILITY-FOCUSED DESIGN CONTEXT

## Universal Design Knowledge Loading
When designing for accessibility and inclusion, load this specialized context for comprehensive accommodation.

## Essential Knowledge Base for Accessible Design

### Core Accessibility References (Load Immediately):
- **`Standards/Accessibility/universal_accessibility_2024.md`** - Complete ADA, WCAG 2.1, ISO accessibility standards
- **`Core/Foundations/population_analysis.md`** - Disability demographics and accommodation strategies
- **`Core/Principles/vitruvian_ergonomic_principles.md`** - UTILITAS accessibility principles

### Supporting Accessibility Knowledge (Load as Needed):
- **`Standards/Safety/safety_standards_2024.md`** - Emergency accessibility requirements
- **`Core/Foundations/anthropometric_databases.md`** - Wheelchair and mobility aid dimensions
- **`Methods/Testing/ergonomic_validation_protocols.md`** - Assistive technology testing protocols

## Universal Design Philosophy
*"Good design enables, poor design disables"* - Every design decision either opens doors or closes them for users with disabilities.

## Accessibility-First Design Triggers
Load this context when ANY of these conditions exist:

### Regulated Environments:
- Government facilities (federal, state, local)
- Public accommodations (retail, hospitality, entertainment)
- Employment environments (offices, factories, workshops)
- Educational facilities (schools, universities, training centers)
- Healthcare facilities (hospitals, clinics, rehabilitation centers)
- Transportation systems (vehicles, terminals, infrastructure)

### Target Populations Include:
- People with permanent disabilities (mobility, vision, hearing, cognitive)
- People with temporary impairments (injuries, illness, recovery)
- People in situational contexts (carrying items, wearing gloves, noise)
- Aging population (declining vision, hearing, mobility, cognition)
- Children and small stature individuals

### Technology Integration:
- Digital interfaces (software, apps, websites)
- Interactive kiosks and public terminals
- Voice-controlled systems
- AR/VR immersive environments
- IoT and smart home devices

## The Seven Principles Applied

### 1. Equitable Use Implementation
**Design Checklist**:
- [ ] Same function available to all users
- [ ] No segregation or stigmatization
- [ ] Privacy and security equal for all
- [ ] Appealing design for diverse users

**FreeCAD Application**:
```python
def ensure_equitable_use(design):
    """Verify all functions are accessible to all user types."""
    
    user_types = ['able_bodied', 'wheelchair_user', 'visual_impaired', 
                  'hearing_impaired', 'one_handed', 'elderly']
    
    for function in design.functions:
        for user_type in user_types:
            if not function.accessible_to(user_type):
                add_alternative_access_method(function, user_type)
    
    return design
```

### 2. Flexibility in Use Implementation
**Accommodation Strategies**:
- Multiple input methods (touch, voice, gesture, keyboard)
- Adjustable interfaces (size, contrast, timing)
- Alternative output formats (visual, auditory, tactile)
- Customizable layouts and preferences

**Implementation Example**:
```python
def create_flexible_interface():
    """Create interface with multiple interaction methods."""
    
    interface_options = {
        'input_methods': ['touch', 'voice', 'eye_gaze', 'switch', 'keyboard'],
        'output_formats': ['visual', 'audio', 'braille', 'haptic'],
        'customization': ['font_size', 'contrast', 'color_scheme', 'layout'],
        'timing': ['adjustable_timeouts', 'pause_resume', 'replay_options']
    }
    
    return create_adaptive_interface(interface_options)
```

### 3. Simple and Intuitive Use
**Complexity Reduction Strategies**:
- Progressive disclosure of information
- Consistent interaction patterns
- Clear visual hierarchy
- Familiar conventions and metaphors

**Cognitive Load Assessment**:
```python
def assess_cognitive_accessibility(interface):
    """Evaluate interface cognitive demands."""
    
    complexity_factors = {
        'information_density': count_simultaneous_elements(interface),
        'decision_points': count_user_choices(interface),
        'memory_load': assess_information_retention_needs(interface),
        'navigation_depth': measure_menu_hierarchy(interface)
    }
    
    # Apply 7±2 rule and cognitive accessibility guidelines
    if complexity_factors['information_density'] > 7:
        recommend_information_chunking(interface)
    
    return complexity_factors
```

## Disability-Specific Design Guidelines

### Visual Accessibility

#### Low Vision (Partial Sight):
**Design Requirements**:
- Contrast ratio minimum 4.5:1 (normal text), 3:1 (large text)
- Font size minimum 16px (12pt), preferred 18px (14pt)
- Scalable text up to 200% without horizontal scrolling
- Color independent information (never rely on color alone)

**Enhanced Requirements**:
- Magnification support up to 400%
- High contrast mode (7:1 ratio or greater)
- Customizable color schemes
- Focus indicators clearly visible

#### Blindness (No Usable Vision):
**Screen Reader Support**:
- Semantic markup with proper headings (H1-H6)
- Alternative text for all images and graphics
- Table headers and captions for data tables
- Form labels explicitly associated with controls

**Navigation Support**:
- Skip links for main content areas
- Breadcrumb navigation
- Page titles that describe content
- Logical tab order for keyboard navigation

**Implementation**:
```python
def ensure_screen_reader_compatibility(interface):
    """Verify complete screen reader accessibility."""
    
    accessibility_features = {
        'semantic_structure': add_proper_headings(interface),
        'alternative_text': add_alt_text_to_images(interface),
        'labels': associate_labels_with_controls(interface),
        'descriptions': add_descriptions_for_complex_content(interface),
        'landmarks': add_aria_landmarks(interface)
    }
    
    return accessibility_features
```

### Hearing Accessibility

#### Hard of Hearing (Partial Hearing):
**Audio Enhancement**:
- Volume controls for all audio content
- Frequency adjustment options
- Visual sound indicators (waveform, volume bars)
- Hearing loop compatibility

#### Deafness (No Usable Hearing):
**Visual Communication**:
- Captions for all audio content
- Sign language interpretation (when required)
- Visual alerts for system status
- Text alternatives for audio information

**Implementation**:
```python
def ensure_hearing_accessibility(system):
    """Provide visual alternatives to all audio information."""
    
    audio_alternatives = {
        'captions': add_closed_captions_to_video(system),
        'visual_alerts': replace_audio_alerts_with_visual(system),
        'transcripts': provide_text_transcripts(system),
        'vibration': add_tactile_notifications(system)
    }
    
    return audio_alternatives
```

### Motor Accessibility

#### Limited Hand/Arm Function:
**Control Requirements**:
- Maximum 22N (5 lbf) force for controls
- Controls operable with closed fist
- No tight grasping or pinching required
- Alternative to fine motor control tasks

#### Wheelchair Users:
**Physical Access**:
- Clear floor space: 760mm × 1220mm minimum
- Reach ranges: 380-1220mm height for controls
- Knee clearance: 685mm minimum height
- Approach clearance: 815mm minimum width

**Implementation**:
```python
def design_for_wheelchair_access(workspace):
    """Ensure wheelchair accessibility for all functions."""
    
    accessibility_zones = {
        'reach_zone': create_reach_envelope(380, 1220),  # mm height
        'clear_space': ensure_clear_floor_space(760, 1220),  # mm width x depth
        'knee_clearance': provide_knee_space(685),  # mm height
        'approach_space': ensure_approach_clearance(815)  # mm width
    }
    
    return validate_wheelchair_access(workspace, accessibility_zones)
```

### Cognitive Accessibility

#### Memory Impairments:
**Memory Support**:
- Minimize working memory demands
- Provide external memory aids (notes, bookmarks)
- Clear progress indicators for multi-step tasks
- Consistent navigation patterns

#### Attention Disorders:
**Attention Management**:
- Minimize distractions (animations, auto-playing content)
- Clear focus indicators
- Single-task interfaces when possible
- User control over timing

**Implementation**:
```python
def design_for_cognitive_accessibility(interface):
    """Reduce cognitive barriers and provide supports."""
    
    cognitive_supports = {
        'memory_aids': add_progress_indicators(interface),
        'attention_management': minimize_distractions(interface),
        'comprehension': use_plain_language(interface),
        'navigation': provide_consistent_patterns(interface)
    }
    
    return cognitive_supports
```

## Assistive Technology Integration

### Screen Readers:
- **JAWS** (Windows): Most common, feature-rich
- **NVDA** (Windows): Free, open-source
- **VoiceOver** (macOS/iOS): Built-in Apple solution
- **TalkBack** (Android): Built-in Google solution

### Voice Control:
- **Dragon NaturallySpeaking**: Professional dictation
- **Windows Speech Recognition**: Built-in Windows
- **Voice Control** (macOS): Built-in Apple solution
- **Voice Access** (Android): Built-in Google solution

### Switch Controls:
- **Single switches**: Simple activation devices
- **Dual switches**: Forward/backward navigation
- **Joystick switches**: Directional control
- **Sip-and-puff**: Breath-controlled switches

### Eye Tracking:
- **Tobii Eye Trackers**: Professional eye control
- **Eye Control** (Windows): Built-in solution
- **Look to Speak** (Android): Google's solution

## Testing Protocols for Accessibility

### Automated Testing:
```python
def run_accessibility_audit(design):
    """Comprehensive automated accessibility testing."""
    
    testing_tools = {
        'axe_core': run_axe_accessibility_scanner(design),
        'wave': run_wave_evaluation(design),
        'lighthouse': run_lighthouse_audit(design),
        'pa11y': run_pa11y_testing(design)
    }
    
    # Consolidate results
    audit_results = consolidate_audit_results(testing_tools)
    
    # Prioritize issues
    critical_issues = filter_critical_issues(audit_results)
    
    return {
        'overall_score': calculate_accessibility_score(audit_results),
        'critical_issues': critical_issues,
        'recommendations': generate_recommendations(audit_results)
    }
```

### User Testing with Disabilities:
**Recruitment Strategy**:
- Partner with disability organizations
- Include 20-30% users with disabilities in all testing
- Diverse disability types and severity levels
- Include assistive technology users

**Testing Protocol**:
1. **Accessibility screening**: Verify AT compatibility
2. **Task-based testing**: Real-world scenarios
3. **Usability assessment**: Effectiveness, efficiency, satisfaction
4. **Barrier identification**: Document access failures
5. **Recommendation development**: Prioritized improvement list

## Regulatory Compliance Framework

### Americans with Disabilities Act (ADA):
**Title II** (Public Entities): Government programs and services
**Title III** (Public Accommodations): Private businesses open to public
**Section 508** (Federal Agencies): Federal government technology

### Web Content Accessibility Guidelines (WCAG 2.1):
**Level A**: Minimum accessibility (basic compliance)
**Level AA**: Standard accessibility (legal requirement)
**Level AAA**: Enhanced accessibility (beyond legal requirement)

### International Standards:
- **EN 301 549** (Europe): Public procurement accessibility
- **JIS X 8341** (Japan): Web accessibility guidelines
- **DDA** (Australia): Disability Discrimination Act

## Emergency Accessibility Considerations

### Emergency Communication:
- Multiple sensory modalities (visual, auditory, tactile)
- Clear, simple language (6th grade reading level)
- Universal symbols and pictograms
- Backup communication methods

### Emergency Evacuation:
- Accessible egress routes maintained
- Areas of refuge for wheelchair users
- Visual and auditory alarm systems
- Emergency assistance communication systems

**Implementation**:
```python
def design_accessible_emergency_systems():
    """Ensure emergency systems accommodate all disabilities."""
    
    emergency_accommodations = {
        'alerts': {
            'visual': high_contrast_flashing_lights(),
            'auditory': voice_announcements_plus_tone(),
            'tactile': vibration_alerts()
        },
        'communication': {
            'text': emergency_text_messaging(),
            'voice': two_way_communication_devices(),
            'pictographic': universal_emergency_symbols()
        },
        'evacuation': {
            'wheelchair_routes': accessible_egress_paths(),
            'areas_of_refuge': safe_waiting_areas(),
            'assistance_devices': evacuation_chairs()
        }
    }
    
    return emergency_accommodations
```

## Accessibility Documentation and Training

### Accessibility Statement Template:
```markdown
# ACCESSIBILITY STATEMENT

## Commitment to Accessibility
[Organization] is committed to ensuring digital accessibility for people with disabilities.

## Conformance Status
This [product/service] is [fully conformant/partially conformant/non-conformant] 
with WCAG 2.1 Level AA.

## Feedback and Contact Information
We welcome your feedback on the accessibility of this [product/service].
- Email: [accessibility@organization.com]
- Phone: [accessibility phone number]
- Address: [physical address]

## Known Issues
[List any known accessibility barriers and planned remediation]

## Date
This statement was created on [date] and last reviewed on [date].
```

### Training Requirements:
**Design Team Training**:
- Disability awareness and etiquette
- Universal design principles
- WCAG 2.1 guidelines understanding
- Assistive technology demonstration
- Testing with users with disabilities

**Development Team Training**:
- Accessible coding practices
- ARIA implementation
- Keyboard navigation programming
- Screen reader testing techniques
- Automated testing tool usage

## Accessibility Validation Checklist

### Pre-Design Phase:
- [ ] Target user population includes people with disabilities
- [ ] Accessibility requirements defined and documented
- [ ] Accessibility personas created
- [ ] Budget allocated for accessibility features
- [ ] Team trained in accessibility principles

### Design Phase:
- [ ] Universal design principles applied
- [ ] Color contrast ratios verified (4.5:1 minimum)
- [ ] Multiple input methods supported
- [ ] Clear visual hierarchy established
- [ ] Error prevention and recovery designed

### Development Phase:
- [ ] Semantic HTML markup used
- [ ] ARIA labels and descriptions added
- [ ] Keyboard navigation implemented
- [ ] Focus indicators clearly visible
- [ ] Alternative text provided for images

### Testing Phase:
- [ ] Automated accessibility testing completed
- [ ] Manual keyboard testing performed
- [ ] Screen reader testing conducted
- [ ] User testing with people with disabilities
- [ ] All critical issues resolved

### Deployment Phase:
- [ ] Accessibility statement published
- [ ] User documentation includes accessibility features
- [ ] Support team trained on accessibility issues
- [ ] Feedback mechanism established
- [ ] Ongoing monitoring plan implemented

---

**ACCESSIBILITY COMMITMENT**: Accessibility is not an accommodation—it's a human right. Every design decision should ask: "Who does this exclude?" When we design for the margins, we create better experiences for everyone. Accessibility is not about fixing things for "those people"—it's about recognizing that disability is part of human diversity and designing systems that celebrate rather than exclude that diversity.