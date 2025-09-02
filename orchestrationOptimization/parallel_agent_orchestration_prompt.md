# Parallel Agent Orchestration Workflow Prompt

## Core Objective
Launch ALL engineering specialist agents SIMULTANEOUSLY as independent, parallel processes - each with their own full context window and autonomous analysis capability. This is NOT sequential task delegation but true parallel execution.

## The Workflow

### Phase 1: Parallel Agent Initialization
Launch every subagent AT THE SAME TIME:
- Archimedes (Mathematical Verifier)
- DaVinci (Conceptual Designer)
- Brunel (Systems Engineer)
- Khan (Optimization Engineer)
- Orville (Test Engineer)
- Gabe (Manufacturing Optimizer)
- Tesla (Electromagnetic Expert)
- Hertz (RF Engineer)
- Curie (Materials Scientist)
- Watt (Fluid Dynamics Expert)
- Edison (Electronics Designer)
- Turing (Kinematics Specialist)
- Vitruvius (Human Factors Expert)
- Carson (Sustainability Analyst)

### Phase 2: Independent Analysis (All Agents Working Simultaneously)
Each agent independently:
1. Reads `C:\CodeProjects\freeCAD\CLAUDE.md` (the orchestration guide)
2. Reads their own definition in `C:\CodeProjects\freeCAD\.claude\agents\[agent-name].md`
3. Reads ALL other agent files in `C:\CodeProjects\freeCAD\.claude\agents\` to understand colleagues
4. Uses ULTRATHINKING to deeply analyze the orchestration system
5. Writes their optimization recommendations to `C:\CodeProjects\freeCAD\[agent-name]_orchestration_optimization.md`

### Phase 3: Cross-Pollination Round 1
After all agents complete initial analysis:
1. Claude (orchestrator) reads ALL agent optimization documents
2. Claude identifies key insights and conflicts
3. Claude launches agents AGAIN in parallel with new prompts:
   - "Agent X suggested Y. How does this affect your recommendations?"
   - "Agent Z identified conflict with your approach. Please address."
4. Each agent updates their markdown file with Round 2 insights

### Phase 4: Cross-Pollination Round 2
Repeat the process:
1. Agents read each other's UPDATED documents (through Claude as intermediary)
2. Further refinement of recommendations
3. Consensus building on conflicts
4. Final optimization proposals

### Phase 5: Synthesis
Claude synthesizes all agent inputs into:
- Updated `CLAUDE.md` with all optimizations
- Conflict resolution documentation
- New workflow patterns discovered
- Enhanced orchestration strategies

## Key Requirements

### Parallelization
- ALL agents must run SIMULTANEOUSLY, not sequentially
- Each agent gets their own independent context/memory
- No agent waits for another to complete (except between rounds)

### Agent Independence
- Agents cannot directly communicate with each other
- All inter-agent communication flows through Claude
- Each agent maintains their own perspective and expertise

### Ultrathinking
- Every agent must use deep, thorough analysis
- Consider edge cases, conflicts, optimizations
- Challenge assumptions in the current orchestration

### Output Format
Each agent creates a markdown document with:
```markdown
# [Agent Name] Orchestration Optimization Analysis

## Current System Assessment
- Strengths from my domain perspective
- Weaknesses and gaps identified
- Conflicts with other agents

## Proposed Optimizations
- Specific changes to CLAUDE.md
- New workflow patterns
- Better integration strategies

## Cross-Agent Insights (Round 2+)
- Response to other agents' suggestions
- Resolved conflicts
- Collaborative improvements

## Implementation Priority
1. Critical changes needed immediately
2. Important optimizations
3. Nice-to-have enhancements
```

## Example Launch Command (Conceptual)

```python
# Launch all agents in parallel
import concurrent.futures
import threading

agents = [
    "archimedes", "davinci", "brunel", "khan", "orville", 
    "gabe", "tesla", "hertz", "curie", "watt", 
    "edison", "turing", "vitruvius", "carson"
]

def launch_agent(agent_name):
    # Each agent runs independently with full context
    # Reads CLAUDE.md and all agent definitions
    # Performs ultrathinking analysis
    # Writes optimization document
    pass

# Execute all agents simultaneously
with concurrent.futures.ThreadPoolExecutor(max_workers=14) as executor:
    futures = [executor.submit(launch_agent, agent) for agent in agents]
    concurrent.futures.wait(futures)

# After all complete, begin cross-pollination rounds...
```

## The Goal
Create a massively parallel review process where every specialist simultaneously analyzes the orchestration system, then iteratively refines their recommendations based on colleague insights (passed through Claude). This should reveal:
- Hidden conflicts in the current system
- Optimization opportunities not visible to single agents
- Emergent workflow patterns from collective intelligence
- Robust improvements validated by multiple perspectives

The result should be a battle-tested, multi-perspective optimized orchestration system that leverages the full expertise of the engineering pantheon.