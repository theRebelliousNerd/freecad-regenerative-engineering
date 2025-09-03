

# **Formal Specification and Architectural Blueprint for a Dependency-Driven Just-in-Time Context Framework**

## **Introduction to the Dependency-First Paradigm**

The contemporary landscape of agentic Artificial Intelligence (AI) is characterized by a focus on orchestration—the coordinated management of multiple AI agents, tools, and data sources to achieve complex goals.1 Frameworks such as LangChain, LangGraph, CrewAI, and Microsoft's AutoGen have demonstrated remarkable efficacy in simplifying the development of multi-agent systems, enabling sophisticated interactions and collaborative problem-solving.2 These systems excel at managing the procedural aspects of a task: defining workflows, maintaining state across interactions, and coordinating the sequence of operations.4 LangGraph, for example, employs a graph-based architecture to model stateful, non-linear workflows, affording developers precise control over agent interactions.2 Similarly, CrewAI abstracts collaboration into role-based agent teams, mirroring human organizational structures to tackle complex assignments.3

While powerful, these execution-centric frameworks treat the problem-solving process as a dynamic sequence of actions to be managed. The intelligence of the system is embedded in the agents' ability to react, reason, and decide on the next step within an unfolding workflow. This report proposes a fundamental paradigm shift through the architectural blueprint of a Just-in-Time Context (JITC) framework. The JITC framework is founded on a *dependency-first* philosophy, moving the locus of intelligence from dynamic execution to a priori formalization. It posits that for a significant class of complex design and engineering problems, the optimal path to a correct and robust solution is not to orchestrate a procedure, but to first construct and validate a complete, declarative model of the problem's entire constraint network.

This approach recasts the role of an agentic system. Instead of being an orchestrator of actions, the JITC system becomes an architect of certainty. Its primary function is to guide the transformation of ambiguous requirements into a mathematically precise and verifiable network of dependencies. The final output—be it a 3D model, a software application, or a logistical plan—is not the product of a clever agent's iterative process, but the deterministic, inevitable manifestation of a fully solved and validated dependency graph. This moves beyond task orchestration to a form of automated formal verification for the problem domain. The system's main purpose is to prove the solvability and correctness of the problem specification *before* any generative work commences. The subsequent orchestration is merely the guided process of constructing this proof, ensuring that late-stage failures, rework, and inconsistencies are virtually eliminated by design.

### **Beyond Execution Orchestration: A New Philosophy for Agentic Systems**

Current agentic frameworks function as sophisticated operating systems for AI agents. They provide essential services like process management (task sequencing), memory allocation (context and history), and I/O handling (tool integration).2 They are fundamentally procedural, concerned with the

*how* and *when* of task execution. The JITC framework, in contrast, introduces a declarative paradigm. It is not initially concerned with the sequence of actions required to build an artifact, but rather with exhaustively defining the complete, static set of rules—the dependencies and constraints—that the final artifact must satisfy. It prioritizes architecting the *what* before any consideration of the *how*.

This philosophy is rooted in the principles of Constraint Satisfaction Problems (CSPs), a field of AI that defines problems in terms of variables, their possible values (domains), and the constraints that restrict valid combinations of these values.9 A solution to a CSP is a complete and consistent assignment of values to all variables that satisfies every constraint.9 The JITC framework conceptualizes an entire design problem as a large-scale CSP. The "Axiom Repository," the central knowledge base of the framework, serves as the formal definition of this CSP. The "dependencies" are the constraints, and the "final artifact" is the solution. The phased, gate-driven workflow, therefore, is not just a project management methodology but a structured search algorithm designed to find a valid solution to this CSP.

This reframing has a profound impact on the architecture of the agent orchestra. In many contemporary systems, execution-level agents are highly sophisticated, LLM-powered reasoners that engage in complex dialogue and decision-making to carry out their tasks.12 The JITC architecture, however, deliberately front-loads all "intelligence"—reasoning, planning, conflict resolution, and knowledge integration—into the initial phases of the workflow, which are managed by specialized agents like the System Architect and the Constraint Validator. Once the underlying CSP is solved and the dependency graph is fully validated, the solution is a set of fixed, immutable values. The role of the final agent in the chain, the "Execution Agent," is thereby intentionally de-skilled. Its task is not to reason or create, but to deterministically transcribe the proven solution into the target format (e.g., FreeCAD code, a configuration file, a bill of materials). This design choice is critical: it eliminates the possibility of creative interpretation, hallucination, or error injection at the most critical stage of manifestation. The value of the Execution Agent lies in its perfect, unthinking fidelity to the validated plan, ensuring the final artifact is the mathematically certain result of the preceding formal verification process.

### **Core Analogy: The Problem as a "Network of Consequences"**

To fully grasp the JITC philosophy, it is essential to move beyond the traditional view of a design problem as an object to be built and instead see it as a "network of consequences" to be architected. In software engineering, a dependency graph is a directed graph where nodes represent entities (e.g., modules, libraries) and edges represent dependencies, such that an edge from node A to node B signifies that A depends on B.14 These graphs are instrumental for tasks like impact analysis, which seeks to understand how a change in one component will affect downstream elements.16

The JITC framework elevates this concept from a simple structural representation to a rich, causal model. A dependency is not merely a static link; it is a quantifiable *consequence*. For example, a decision to change a material from ABS plastic to aluminum does not just alter one line in a specification; it propagates a cascade of consequences throughout the network. This change directly affects dependencies related to cost, weight, and manufacturing\_process. These, in turn, have second-order effects on structural\_integrity, thermal\_conductivity, and RF\_shielding. The change in thermal\_conductivity might then necessitate a revision of the minimum\_clearance required for heat dissipation, which could impact the overall\_enclosure\_dimensions. This web of causal relationships forms the "network of consequences."

This perspective aligns with and extends concepts from the field of AI planning. Research into Action Dependency Graphs (ADGs) uses graph structures to represent temporal and causal dependencies between actions, ensuring that a plan is executed correctly (e.g., action b can only be performed after its prerequisite action a is complete).17 Other planning research utilizes dependency graphs to optimize complex action schemas by breaking them down into "micro-actions" based on the inherent dependencies between their preconditions and effects.19 The JITC framework generalizes this principle beyond the procedural or temporal domains. It aims to capture

*all* significant dependencies—physical, logical, geometric, financial, regulatory, and temporal—within a single, unified graph structure. This graph is not a model of the *process* to solve the problem; it is a formal model of the *problem itself*. The primary role of the agent orchestra is to map, navigate, and satisfy this network, with the physical or digital artifact being merely the final, tangible manifestation of this validated graph.

### **The JITC Framework: Achieving Deterministic Outcomes Through A Priori Validation**

The ultimate objective of the JITC framework is to deliver outputs that are correct by construction. By treating the problem as a formal CSP and building a validated dependency graph before manifestation, the system shifts the burden of verification from post-production testing to pre-production design. This "geometry-last" or "execution-last" approach ensures that resources are not expended on generating an artifact until its specification has been proven to be complete, consistent, and achievable.

This methodology directly addresses the root cause of many costly failures in complex projects: errors and inconsistencies that are discovered late in the development cycle. By leveraging a phased, gate-driven process inspired by established project management techniques like the Stage-Gate model 20, the JITC framework imposes rigorous quality control at every step. However, unlike its human-centric counterparts, these gates are not subjective review meetings. They are automated, formal verification steps where a specialized "Validator" agent executes a series of checks against the dependency graph. A "GO" decision from a gate is not an opinion but a computational proof that the current state of the design is valid and satisfies all known constraints up to that point. This transforms a management process into a formal method, providing a structured and auditable path from an ambiguous user request to a mathematically certain outcome.

## **Conceptual Architecture of the JITC Ecosystem**

The JITC ecosystem is designed around a clear separation of concerns, ensuring that the integrity of the dependency graph is maintained as the single source of truth throughout the problem-solving lifecycle. The conceptual architecture comprises three primary components: the JITC Orchestrator, the Axiom Repository, and the Specialist Agent Orchestra. These components interact within a hybrid architectural model that combines the benefits of centralized control for consistency with hierarchical delegation for efficient task execution.

### **System Overview: The Interplay of the Orchestrator, Axiom Repository, and Agent Orchestra**

The high-level architecture of the JITC framework is composed of the following core elements:

1. **JITC Orchestrator:** This is the central control unit of the system. It functions as a state machine manager, driving the entire workflow through its predefined phases. The Orchestrator is responsible for activating and deactivating agents based on the current phase, managing the transitions between phases via Verification Gates, and serving as the primary interface between the Agent Orchestra and the Axiom Repository for high-level control decisions. It does not engage in problem-solving itself but ensures the process is followed with absolute rigor.  
2. **Axiom Repository:** This is the persistent, centralized database that houses the dependency graph. It is the definitive single source of truth for the entire project. All constraints, requirements, parameters, and their interrelationships are stored here as structured, machine-readable dependency objects. The state of the Axiom Repository—its completeness, consistency, and validation status—defines the overall progress of the project. Agents do not hold their own state regarding the problem's constraints; they query and update the Axiom Repository under the Orchestrator's supervision.  
3. **Specialist Agent Orchestra:** This is a collection of distinct, role-based AI agents, each designed to perform a specific function within the dependency-driven workflow. Unlike general-purpose agents, these specialists are defined by their interaction with the Axiom Repository. The orchestra includes roles for eliciting requirements, formalizing constraints, validating the graph's integrity, and executing the final manifestation. This specialization ensures that each stage of the process is handled by an agent with the precise capabilities and context required for that task.22

The interplay between these components is strictly governed. The Orchestrator initiates a phase by activating the relevant agent (e.g., the "Requirements Interrogator" in Phase 1). This agent then performs its function, interacting with the user or external data sources and committing its findings to the Axiom Repository. Upon completion of the phase's objectives, the Orchestrator triggers a "Constraint Validator" agent to assess the state of the Axiom Repository against a set of gate criteria. Only upon a successful validation does the Orchestrator transition the system to the next phase.

### **Architectural Model: A Hybrid Centralized-Hierarchical Structure**

The architecture of a multi-agent system (MAS) significantly influences its capabilities, robustness, and scalability. Common patterns include centralized networks, where a central unit manages global knowledge, and decentralized or hierarchical structures, which distribute control and knowledge.22 A purely centralized model offers consistency but introduces a single point of failure, while a purely decentralized model enhances robustness but can complicate coordination.22

The JITC framework employs a hybrid architectural model to leverage the strengths of multiple patterns:

* **Centralized Core:** At its heart, the JITC system is centralized. The JITC Orchestrator and the Axiom Repository form a non-negotiable central hub. This design choice is critical for enforcing the "single source of truth" principle. All global state, which in this paradigm is the dependency graph itself, resides within the Axiom Repository. All major control flow decisions are made by the Orchestrator based on the state of this repository. This centralization is essential for maintaining global consistency and ensuring that all agents operate from the same verified set of facts, directly aligning with the strengths of centralized MAS architectures.22  
* **Hierarchical Agent Interaction:** While the core is centralized, the interaction with the agent orchestra is hierarchical. The JITC Orchestrator acts as the apex of the hierarchy, functioning as a top-level manager. It delegates responsibility for an entire phase to a primary agent for that phase (e.g., delegating the "Constraint Formalization" phase to the "System Architect"). This primary agent may, in turn, manage sub-tasks or coordinate with other specialized services to fulfill its objective, mirroring the manager-worker pattern seen in hierarchical and holonic MAS structures.22 This allows for modularity and specialization in agent function without compromising the centralized control over the project's state.

This hybrid model provides the best of both worlds: the strict consistency and verifiability of a centralized system for the critical dependency data, combined with the efficient, delegated execution of a hierarchical system for agent operations.

### **Information Flow: How Dependencies, Not Tasks, Dictate System State**

A defining characteristic of the JITC framework is its state management philosophy. In conventional agentic frameworks, the system's state is often tied to the execution of a plan or the history of a conversation. For instance, LangGraph maintains a shared state object that is passed between nodes in a computational graph, representing the evolving context of the task.6 CrewAI's "Flows" feature also provides mechanisms for managing and sharing state between different tasks in a workflow.25

In the JITC framework, the primary system state is not a task list or a conversational memory buffer; it is the **state of the Axiom Repository itself**. Progress is not measured by the number of tasks completed but by the evolving quality of the dependency graph. Key state indicators include:

* **Completeness:** The percentage of known requirements that have been formalized into dependency objects.  
* **Status Distribution:** The ratio of dependencies that are Provisional versus Validated versus Immutable.  
* **Consistency:** The absence of detected conflicts or circular dependencies within the graph.  
* **Confidence Score:** An aggregate measure of the certainty associated with the values and relationships in the graph.

A task such as "Generate CAD Model" is not considered "in progress" or even "ready" until the state of the Axiom Repository transitions to "fully validated and immutable." This dependency-centric view of state ensures that the system's focus remains on the integrity of the problem specification.

To manage the evolution of this state effectively, the Axiom Repository should be architected not as a simple database but as a **version-controlled knowledge base**. The design process is inherently iterative; requirements are clarified, assumptions are challenged, and trade-offs are made. A static database would overwrite this crucial history. By adopting a model analogous to a version control system like Git, which uses a directed acyclic graph (DAG) to represent the history of changes 26, the JITC framework can capture the entire design journey.

In this model, every significant modification to the dependency graph—such as adding a new set of constraints from a component datasheet, resolving a conflict between two dependencies, or a user-initiated change in requirements—is treated as a "commit." This creates an immutable, auditable history of the design's evolution. This versioning capability enables several advanced functions:

* **Branching:** To explore alternative design paths (e.g., one branch for an injection-molded enclosure, another for a 3D-printed one) without affecting the main design.  
* **Merging:** To integrate successful design explorations back into the primary branch.  
* **Reverting:** To instantly roll back to a previously known-good state if a design path proves unviable.  
* **Auditing:** To provide a complete, traceable record of every decision and its justification, which is invaluable for root-cause analysis, regulatory compliance, and knowledge transfer.

## **Formalization of the Dependency Graph and Axiom Repository**

The foundation of the JITC framework is the rigorous, unambiguous representation of the problem's constraint network. This requires moving from the abstract concept of "context" to a formal, machine-readable data structure for "dependencies." This section provides the technical specification for this structure, defining the atomic unit of a dependency, the architecture of the central repository that stores the dependency graph, and methods for modeling complex interactions.

### **The Atomic Unit: A Formal Schema for a "Dependency"**

A dependency within the JITC framework is not a simple key-value pair. It is a rich, structured object that captures not only a value but also its nature, origin, certainty, and relationships within the broader network. The following proposed schema, presented in YAML for readability, defines the fields of a single dependency object. This schema is designed to be sufficiently expressive to model a wide range of constraints found in complex engineering, software, and logistical problems.

YAML

dependency\_id: "DEP-00127"  
\# A unique, system-generated identifier for the dependency.

name: "PCB\_to\_Lid\_Min\_Clearance"  
\# A human-readable, concise name for the dependency.

description: "Minimum vertical clearance between the highest point on the main PCB assembly and the inner surface of the enclosure lid to prevent electrical shorting and allow for air circulation."  
\# A detailed description of the dependency's purpose and physical meaning.

type: "GeometricConstraint"  
\# The category of the dependency. Enumerated list, e.g., GeometricConstraint, ThermalConstraint, MaterialProperty, ElectricalParameter, TemporalConstraint, UserRequirement, FinancialBudget.

value:  
  target: 5.0  
  \# The nominal or target value. Can be a scalar, vector, string, or boolean.  
  unit: "mm"  
  \# The unit of measurement, if applicable (e.g., mm, Celsius, kg, seconds).  
  operator: "GREATER\_THAN\_OR\_EQUAL\_TO"  
  \# The logical operator defining the constraint, e.g., EQUAL\_TO, LESS\_THAN, IN\_RANGE \[min, max\], MEMBER\_OF\_SET \[...\].  
  tolerance: \[ \-0.0, \+0.5 \]  
  \# Optional field for specifying acceptable deviation from the target value.

status: "Validated"  
\# The current state of the dependency in its lifecycle. Enumerated list: Provisional (newly created, unverified), Inferred (derived by the system, needs validation), Validated (checked at a gate), Immutable (locked after final plan approval).

confidence: 0.99  
\# A float between 0 and 1 representing the certainty of the value and its source. A measured value might be 0.999, while an early user estimate might be 0.6.

source\_of\_truth:  
  type: "Derived"  
  \# The origin of the dependency. Enumerated list: UserRequirement, IndustryStandard, DirectMeasurement, SimulationResult, Derived (calculated from other dependencies).  
  details: "Derived from the maximum component height on the PCB (DEP-00125) plus a standard safety factor (DEP-00126)."  
  \# A textual explanation of the source.  
  source\_ids:  
  \# An array of dependency\_ids that this dependency is derived from, forming the edges of the graph.

affects:  
  \# A system-populated array of dependency\_ids that are influenced by this one. This represents the outgoing edges of the graph.  
  \- "DEP-00130" \# Enclosure\_Total\_Height  
  \- "DEP-00210" \# Assembly\_Sequence

metadata:  
  created\_by: "SystemArchitect\_Agent\_01"  
  \# The ID of the agent or user who created this dependency.  
  timestamp\_created: "2025-09-15T10:30:00Z"  
  \# The ISO 8601 timestamp of creation.  
  timestamp\_validated: "2025-09-15T14:00:00Z"  
  \# The ISO 8601 timestamp of its last validation.  
  validation\_log\_id: "GATE-LOG-G23-0042"  
  \# A reference to the log entry from the Verification Gate where this dependency was validated.  
  version\_hash: "a1b2c3d4e5f6..."  
  \# A hash of the dependency's state, for version control.

### **The Centralized Axiom Repository: A Verifiable Single Source of Truth**

The Axiom Repository is the architectural cornerstone of the JITC framework. It ingests, stores, and manages all dependency objects, materializing the "network of consequences" as a queryable and verifiable graph structure.

#### **Architectural Design**

Given that the core data structure is a graph of interconnected dependency objects, the ideal backend technology for the Axiom Repository is a **graph database**, such as Neo4j, Amazon Neptune, or ArangoDB. A relational database could be forced to model these relationships using join tables, but this would be inefficient and cumbersome for the types of queries required by the JITC framework.

Using a graph database, the implementation is direct and natural:

* **Nodes:** Each dependency object (as defined by the schema) is stored as a node in the graph. The node's properties would include fields like name, type, value, status, and confidence.  
* **Edges:** The relationships defined in the source\_ids and affects fields are stored as directed edges. An edge from DEP-00125 to DEP-00127 would be labeled with a type such as IS\_SOURCE\_FOR, explicitly representing the dependency link.

This native graph representation allows for highly efficient traversal of complex dependency chains, which is essential for impact analysis, root-cause analysis, and validation queries.16

#### **Query Language and Agent Interaction Protocols**

Agents do not interact directly with the database. Instead, they communicate with the Axiom Repository through a well-defined **RESTful API**. This API serves as a gatekeeper, ensuring that all modifications to the graph are authenticated, validated, and logged according to the framework's protocols.

The API endpoints would support CRUD (Create, Read, Update, Delete) operations on dependency nodes, as well as more complex query capabilities. The query endpoint would accept queries written in a graph-native query language (e.g., Cypher for Neo4j or Gremlin for Neptune). This allows agents to perform powerful and expressive queries.

**Example Query (executed by the Constraint Validator agent at a gate):**

* **Objective:** "Find all ThermalConstraint dependencies that are still in Provisional status and are affected by the MaterialProperty dependency for Enclosure\_Material."  
* **Cypher Query (Illustrative):**  
  Cypher  
  MATCH (m:Dependency {type: 'MaterialProperty', name: 'Enclosure\_Material'})--\>(t:Dependency {type: 'ThermalConstraint'})  
  WHERE t.status \= 'Provisional'  
  RETURN t.dependency\_id, t.name

This query traverses the graph up to 5 levels deep from the material choice to find any downstream thermal constraints that have not yet been validated. A non-empty result from this query would cause the gate to fail, preventing the design from proceeding with unverified thermal properties.

### **Advanced Dependency Modeling**

The formal schema and graph architecture provide the foundation for modeling sophisticated and realistic problem dynamics.

#### **Representing Coupled and Transitive Dependencies**

Many real-world systems exhibit complex coupling between different physical domains. For example, a change in a material's structural properties (Material Science) can automatically propagate consequences into the required dimensions for load-bearing elements (Structural Engineering).

The graph structure of the Axiom Repository natively handles these interactions. A transitive dependency is simply a path of two or more edges in the graph.16 The impact of changing a single, fundamental dependency (e.g.,

Material\_Choice) can be fully traced by performing a graph traversal from that node. The system can identify not only the direct, first-order consequences (e.g., Density, Tensile\_Strength) but also the second-order (Total\_Weight, Vibration\_Modes) and third-order (Shipping\_Cost, Acoustic\_Dampening\_Requirements) effects. This allows the System Architect agent to perform comprehensive "what-if" analyses before committing to a design change.

#### **Algorithms for Detecting and Resolving Conflicts and Circularities**

A valid dependency graph must be both acyclic and consistent. The JITC framework incorporates automated checks to enforce these properties.

* **Conflict Detection and Resolution:** A conflict arises when two or more dependencies impose mutually exclusive constraints (e.g., width \>= 10mm and width \<= 5mm). Such problems are known as over-constrained CSPs.10 While a human engineer might spot simple conflicts, complex interactions can easily be missed.

  To automate this, the JITC framework integrates a Constraint Programming (CP) solver. CP is a powerful paradigm for solving combinatorial problems by identifying feasible solutions from a large set of candidates based on arbitrary constraints.28 At each Verification Gate, the Validator agent extracts the complete set of  
  Validated constraints from the Axiom Repository and feeds them into an integrated CP solver (such as Google's CP-SAT solver, IBM's CPLEX CP Optimizer, or an open-source tool like Gecode).28 If the solver returns a status of "unsatisfiable," it means a conflict exists. The gate fails, and the solver can often provide information about the core set of conflicting constraints, which are then flagged for the System Architect agent to resolve.  
* **Circularity Detection:** A circular dependency (e.g., A depends on B, which depends on C, which in turn depends on A) makes a problem logically unresolvable and must be prohibited.15

  The System Architect agent is responsible for preventing the introduction of cycles into the graph. Each time a transaction of new dependencies is to be committed to the Axiom Repository, a cycle detection algorithm is run on the proposed new state of the graph. A standard algorithm based on Depth-First Search (DFS) can efficiently determine if any cycles exist. If a cycle is detected, the API rejects the commit and returns an error specifying the nodes involved in the cycle, forcing the agent to refactor the dependencies into a valid Directed Acyclic Graph (DAG) structure.

## **The Specialist Agent Orchestra**

A complex, dependency-driven workflow cannot be executed by a single, monolithic AI or a team of generic sub-agents. The JITC paradigm requires a new typology of agent roles, each defined by its specific function in the lifecycle of a dependency—from its initial elicitation to its final enforcement. The JITC framework is designed to orchestrate this team of specialists, providing each with the precise context necessary to perform its function effectively. This approach draws on the principle of domain specialization in Multi-Agent Systems (MAS), where individual agents possess specific expertise, leading to greater overall system performance.22 It formalizes this concept in a manner similar to role-based frameworks like CrewAI, but with roles tailored specifically to the dependency-first philosophy.3

### **A Typology of Dependency-Driven Agent Roles**

The JITC orchestra is composed of four primary agent roles, each with a distinct responsibility in the process of building and validating the Axiom Repository.

#### **The Requirements Interrogator**

* **Function:** The Interrogator is the primary interface with the human user during the initial phase of a project. Its objective is to elicit a comprehensive set of all explicit and implicit requirements, constraints, and goals. It employs techniques of Socratic questioning and context-aware clarification to transform vague user statements into structured, unambiguous information.  
* **JITC Context:** The Interrogator's effectiveness is amplified by its use of the JITC framework to retrieve external context. It is not merely a passive question-asker. When a user states a requirement like "the device must be waterproof," the Interrogator agent queries JITC-integrated knowledge bases for relevant industry standards. It might retrieve the specifications for IP (Ingress Protection) ratings. It then uses this context to formulate a precise, clarifying question: *"To clarify 'waterproof,' do you require compliance with IP67, which means the device can be submerged in 1 meter of water for 30 minutes? This choice will have specific consequences for material selection, gasket design, and fastener requirements. Or is a splash-proof rating like IP65 sufficient?"* This proactive clarification prevents ambiguity and ensures that the raw data passed to the next phase is as precise as possible.

#### **The System Architect**

* **Function:** The System Architect is the master builder and curator of the Axiom Repository. It is the most sophisticated agent in the orchestra, responsible for translating the structured information from the Interrogator into the formal, machine-readable dependency objects specified by the schema. It builds the dependency graph, establishes the relationships between nodes, and is responsible for maintaining the logical integrity of the entire network.  
* **JITC Context:** The Architect agent leverages JITC as a knowledge injection and validation engine. When formalizing a constraint for the enclosure's wall thickness, it receives the raw requirement (e.g., "must be durable") and the chosen manufacturing method (e.g., "injection molding"). It then uses JITC to query engineering databases for the material properties of ABS plastic, retrieves standard formulas for calculating structural integrity, and considers constraints like draft angles required for molding. It synthesizes this information to create a set of formal dependencies, such as DEP-0030 (Material\_Choice, value: 'ABS'), DEP-0031 (Min\_Wall\_Thickness, value: 2.5mm), and DEP-0032 (Draft\_Angle, value: 3 degrees). It is also the agent tasked with resolving conflicts and circularities flagged by the system's automated checks during the validation gates.

#### **The Constraint Validator**

* **Function:** The Validator is the automated, impartial guardian of the Verification Gates. Its role is purely analytical and binary; it does not create, modify, or interpret dependencies. Its sole purpose is to execute a predefined checklist of formal queries and constraint satisfaction checks against the Axiom Repository at the end of each phase.  
* **JITC Context:** The Validator's context is the set of gate criteria for the current phase transition. For the gate between Constraint Formalization and Topological Planning, its JITC-provided checklist might include:  
  1. Execute query: COUNT(dependencies WHERE status='Provisional'). The gate fails if the result is not 0\.  
  2. Execute query: DETECT\_CYCLES(current\_graph). The gate fails if a cycle is found.  
  3. Submit all validated constraints to the integrated CP solver. The gate fails if the solver returns UNSATISFIABLE.  
     The Validator's output is a simple GO/NO-GO decision, accompanied by a detailed, machine-readable log of every check performed and the specific dependencies that caused any failure. This provides an unambiguous, auditable record of the project's quality at each critical juncture.

#### **The Execution Agent**

* **Function:** The Execution Agent is the final "doer" in the workflow. It is a deterministic transcriber that translates the final, validated dependency graph into a tangible artifact. As previously established, this role is intentionally de-skilled to ensure perfect fidelity and eliminate any potential for creative deviation at the point of manifestation.  
* **JITC Context:** The context provided to the Execution Agent is the most restricted of all. After the final planning phase is approved, the JITC Orchestrator queries the Axiom Repository for the specific, immutable set of parameters required for generation. This is delivered to the Execution Agent not as a graph to be interpreted, but as a simple, flat dictionary of key-value pairs (e.g., {'wall\_thickness': 2.5, 'gasket\_groove\_width': 2.0, 'pcb\_mount\_hole\_diameter': 3.2}). The agent's logic is a straightforward script that iterates through this dictionary and uses the values to construct the final output, such as generating lines of freecad-mcp Python code. It has no access to the broader dependency graph, its history, or any alternative values.

### **Role-Specific Context Provisioning via JITC**

The JITC Orchestrator is responsible for providing this tailored context to each agent at the appropriate time. This Just-in-Time delivery ensures that each agent operates with maximum efficiency and security, adhering to the principle of least privilege.

* The **Interrogator** receives access to the user's conversation history and read-only access to external knowledge bases (e.g., standards libraries).  
* The **System Architect** receives the structured output from the Interrogator and is granted read/write access to the Axiom Repository, along with read access to engineering and scientific databases.  
* The **Constraint Validator** receives a read-only snapshot of the Axiom Repository and the specific gate criteria for its current task.  
* The **Execution Agent** receives only the final, immutable parameter dictionary and has no access to the Axiom Repository at all.

This carefully managed flow of context is central to the framework's name and function, ensuring that every agent has precisely the information it needs to perform its role within the dependency-first paradigm, and nothing more.

## **Phased, Gate-Driven Orchestration: A State Machine for Design**

The JITC framework operationalizes its dependency-first philosophy through a structured, sequential workflow. This workflow is not arbitrary but is adapted from formal project management methodologies, specifically the phase-gate (or Stage-Gate) process.20 This process divides a complex project into a series of distinct stages, separated by rigorous decision points, or gates, where progress is assessed against a set of clear criteria.20 In the JITC framework, this management model is transformed into a computational state machine, where phases are states, gates are guarded transitions, and the entire process is automated and driven by the formal validation of the dependency graph.

### **The Generic Phased Workflow: From Elicitation to Manifestation**

Drawing from the principles of the Stage-Gate model, which typically includes phases like Ideation, Business Case, Development, Testing, and Launch 21, the JITC framework proposes a generic, five-phase workflow applicable to a wide range of complex design and engineering tasks. Each phase has a clear objective related to the maturation of the Axiom Repository.

1. **Phase 1: Requirements Elicitation:** The objective of this initial phase is to capture all user needs, stakeholder requirements, environmental conditions, and implicit constraints. The primary agent is the Requirements Interrogator, which interacts with the user to convert ambiguous goals into structured, preliminary data. The Axiom Repository transitions from an empty state to being populated with raw, unstructured, or semi-structured information.  
2. **Phase 2: Constraint Formalization:** The goal of this phase is to translate the raw data from Phase 1 into the formal, machine-readable dependency objects that populate the Axiom Repository. The System Architect is the lead agent, using its specialized knowledge and access to external databases to define each dependency according to the formal schema, establish relationships, and build the initial dependency graph. At the end of this phase, the repository should contain a comprehensive, though not yet fully validated, graph of all known constraints.  
3. **Phase 3: Topological Planning:** This phase aims to find a high-level, globally consistent solution that satisfies the entire dependency graph, but *without* generating the final, detailed artifact. For a physical design, this would be a topological plan—a layout of component bounding boxes and spatial relationships that is proven to meet all clearance, thermal, and assembly constraints. For a software project, this might be a high-level architectural diagram and data flow model. The System Architect is responsible for generating and validating this plan against the Axiom Repository.  
4. **Phase 4: Geometric Manifestation (or Execution):** With a fully validated plan in place, this phase is dedicated to the deterministic generation of the final artifact. The Execution Agent is activated, receiving its immutable parameter set from the Orchestrator. Its task is simple and direct: translate the parameters into the target output format (e.g., CAD code, source code, configuration files).  
5. **Phase 5: Final Validation:** The final phase involves a comprehensive audit of the generated artifact against the specifications in the Axiom Repository. This can involve automated checks, such as running a simulation on the generated 3D model to verify its mass properties against the calculated dependency, or static analysis on generated code. The Validator agent performs these final checks to certify that the manifestation perfectly reflects the proven plan.

### **State-Machine Diagram: Visualizing the Flow of Control and Context**

This phased workflow can be formally represented as a state-machine diagram, which provides a clear visualization of the system's lifecycle.

* **States:** The five phases (Elicitation, Formalization, Planning, Manifestation, Validation) are the primary states of the machine.  
* **Transitions:** The transitions between states are the Verification Gates (e.g., G1→2, G2→3, G3→4, G4→5). A transition can only occur if the gate's conditions are met.  
* **Actions:** Within each state, specific actions are performed by the designated agents (e.g., Interrogator.elicit\_requirements() in the Elicitation state).  
* **Guards:** The conditions for each transition are the gate criteria, which are evaluated by the Constraint Validator. For example, the guard on the G2→3 transition is Validator.run\_gate\_check('G23') \== GO. If the guard condition is false, the system remains in its current state, and a "rework" loop is initiated, flagging the issues for the System Architect to resolve.

This state-machine model enforces a disciplined, forward-moving process. It explicitly prohibits skipping phases or proceeding to a more resource-intensive phase before the prerequisites of the current phase have been formally verified, thus preventing errors from propagating downstream.20

### **Verification Gates as Formal Proofs of Correctness**

In traditional Stage-Gate management, gates are typically meetings where a steering committee reviews project deliverables and makes a subjective, albeit data-informed, go/kill decision.20 The JITC framework transforms this concept into a fully automated, objective, and computational process. The Verification Gates are not review meetings; they are

**automated theorem-proving steps**.

When the Validator agent executes the checks at a gate, it is attempting to prove a proposition about the state of the Axiom Repository. For example, a "GO" decision from Gate G2→3 is not an opinion that the design looks good; it is a formal proof of the following theorem: *"The set of dependencies currently in the Axiom Repository is complete with respect to all elicited requirements, is internally consistent (contains no conflicts), is logically sound (contains no circularities), and therefore constitutes a solvable Constraint Satisfaction Problem."*

This reframing is central to the JITC framework's promise of reliability. It replaces human intuition and potential oversight with mathematical certainty at each critical checkpoint. The tables below provide a concrete definition of the phased workflow and the formal criteria for each Verification Gate.

**Table 1: Phased Workflow Definition**

| Phase | Objective | Primary Agent(s) | Axiom Repository State | JITC Function |
| :---- | :---- | :---- | :---- | :---- |
| 1\. Elicitation | Uncover all user needs and constraints. | Interrogator | Empty → Raw, unstructured data. | Context Retrieval (standards, specs). |
| 2\. Formalization | Convert raw data into formal, machine-readable dependencies. | System Architect | Raw → Structured, provisional dependencies. | Knowledge Injection (formulas, material data). |
| 3\. Planning | Find a valid, high-level arrangement of components that satisfies all constraints. | System Architect | Provisional → Validated, topologically solved graph. | Constraint Solving & Conflict Detection. |
| 4\. Manifestation | Translate the validated plan into a final, deterministic artifact. | Execution Agent | Validated → Immutable parameter set provided. | Parameter Injection & Enforcement. |
| 5\. Validation | Verify the final artifact perfectly matches the specification. | Validator | Immutable | Final Audit & Verification. |

**Table 2: Verification Gate Criteria**

| Gate | Transition | "Must Meet" Criteria (Formal Queries / Checks) | "Should Meet" Metrics (Scored) |
| :---- | :---- | :---- | :---- |
| G1→2 | Elicitation → Formalization | QUERY: IS\_EMPTY(unprocessed\_user\_inputs) \= TRUE CHECK: All requirements have a defined source. | METRIC: Confidence\_Score(all\_requirements) \> 0.9 |
| G2→3 | Formalization → Planning | QUERY: COUNT(dependencies WHERE status='Provisional') \= 0 CHECK: DETECT\_CYCLES(graph) \= FALSE CHECK: CSP\_SOLVER(all\_dependencies) \= SATISFIABLE | METRIC: Graph\_Completeness\_Metric \> 0.95 |
| G3→4 | Planning → Manifestation | CHECK: IS\_VALID(topological\_plan) \= TRUE CHECK: ALL\_CONSTRAINTS\_SATISFIED(topological\_plan) \= TRUE | METRIC: Cost\_Function(plan) \< budget\_dependency |
| G4→5 | Manifestation → Validation | CHECK: ARTIFACT\_GENERATED\_SUCCESSFULLY \= TRUE | N/A |

## **Application Case Study: "Geometry-Last" Engineering with freecad-mcp**

To illustrate the practical application and transformative potential of the JITC framework, this section provides a detailed walkthrough of a common engineering task: designing a custom waterproof enclosure for an electronic device using the freecad-mcp (Model-Code-Project) library. The traditional approach often involves an iterative process of geometric modeling, followed by analysis, which can lead to costly rework when issues like component interference or thermal problems are discovered late. The JITC framework inverts this process, focusing on building a complete, validated dependency graph *before* any geometry is generated.

### **Deconstructing the Design Problem: Building the Enclosure's Dependency Graph**

The process begins not with sketching shapes, but with a dialogue between the user and the Requirements Interrogator agent to populate the Axiom Repository.

* **User Input:** "I need a wall-mountable, waterproof enclosure for this custom PCB. It will be used outdoors in a temperate climate. The manufacturing method should be injection molding using ABS plastic." The user provides photos, a bill of materials, and the PCB's datasheet.  
* **Interrogator & Architect Collaboration:**  
  * The Interrogator parses "wall-mountable" and "waterproof." It queries its knowledge base and asks for clarification: "Does 'waterproof' require IP67 rating (submersible)? This will necessitate a gasket seal and specific fastener torque." The user confirms.  
  * The System Architect receives this structured input. It creates the initial, high-level dependencies:  
    * DEP-001: { name: "Ingress\_Protection", type: "IndustryStandard", value: { target: "IP67" } }  
    * DEP-002: { name: "Mounting\_Type", type: "UserRequirement", value: { target: "ExternalFlange" } }  
    * DEP-003: { name: "Manufacturing\_Method", type: "UserRequirement", value: { target: "InjectionMolding" } }  
    * DEP-004: { name: "Material\_Choice", type: "UserRequirement", value: { target: "ABS" } }  
  * Crucially, the Architect knows that DEP-001 (IP67) creates a cascade of child dependencies. It automatically populates the repository with new, Provisional dependencies derived from this standard:  
    * DEP-005: { name: "Sealing\_Method", type: "Derived", source\_ids:, value: { target: "Gasket" } }  
    * DEP-006: { name: "Gasket\_Material\_Type", type: "MaterialProperty", status: "Provisional" }  
    * DEP-007: { name: "Gasket\_Groove\_Design", type: "GeometricConstraint", status: "Provisional" }  
    * DEP-008: { name: "Fastener\_Torque\_Spec", type: "MechanicalConstraint", status: "Provisional" }

This process continues for every piece of information, creating a rich, interconnected graph of requirements and their consequences.

### **A Step-by-Step Walkthrough of the Phased Workflow**

Phase 1: Requirements Elicitation  
The Interrogator agent continues its dialogue, systematically extracting all necessary information. It parses the PCB datasheet, noting the board dimensions, mounting hole locations, and the height of the tallest component (a capacitor at 4.5 mm). It asks about the operating temperature range and any external connectors that must pass through the enclosure walls. All this information is stored as raw data linked to the initial user request.  
Phase 2: Constraint Formalization  
The System Architect takes over. It processes the raw data and, using JITC's knowledge injection capabilities, converts it into formal dependencies:

* From the datasheet, it creates:  
  * DEP-00125: { name: "PCB\_Max\_Component\_Height", value: { target: 4.5, unit: "mm", tolerance: \[-0.1, \+0.1\] }, confidence: 0.999 }  
* It then derives a critical clearance constraint:  
  * DEP-00127: { name: "PCB\_to\_Lid\_Min\_Clearance", value: { target: 5.0, unit: "mm", operator: "GREATER\_THAN\_OR\_EQUAL\_TO" }, source\_ids: } where DEP-SYS-001 is a system-level safety factor.  
* Based on DEP-003 (Injection Molding) and DEP-004 (ABS), it queries an engineering database and adds constraints for minimum wall thickness, draft angles, and the material's thermal conductivity.

Gate 1→2 & 2→3: The Power of A Priori Validation  
After Phase 2, the Orchestrator triggers the Validator agent for the G2→3 transition. The Validator executes its checks:

1. **Completeness Check:** It queries for any Provisional dependencies. It finds that DEP-006 (Gasket\_Material\_Type) is still undefined. **Result: NO-GO.**  
2. The System Architect is re-activated. It determines that for ABS plastic and an IP67 rating, a silicone gasket is appropriate. It updates DEP-006 and related dependencies.  
3. The Validator runs again. The completeness check now passes.  
4. **Consistency Check:** It submits all validated constraints to the integrated CP solver. The solver models the thermal properties of the enclosed PCB (based on its power consumption from the datasheet) and the thermal dissipation capacity of the ABS enclosure (based on its wall thickness and material properties). The solver finds an inconsistency. **Result: NO-GO.**  
5. **Failure Report:** The Validator outputs a detailed report: "Conflict detected. DEP-0045 (CPU\_Max\_Operating\_Temp \= 85°C) is violated. With DEP-0031 (Min\_Wall\_Thickness \= 2.5mm) and DEP-004 (Material \= ABS), the calculated internal steady-state temperature is 92°C. No passive cooling solution is feasible under current constraints."

This is the critical value proposition of the JITC framework. A fatal design flaw that might traditionally be discovered only after prototyping and testing has been identified and proven mathematically *before a single 3D surface has been created*. The problem is sent back to the System Architect, which resolves the conflict by adding new dependencies for a small heat sink on the CPU and a series of ventilation cutouts (which are then constrained to be compatible with the IP67 rating), and the gate is successfully passed.

Phase 3: Topological Planning  
The System Architect now generates a non-geometric, topological plan. This is a 3D layout of bounding boxes and abstract relationships. It defines the precise (x, y, z) position of the PCB, the location of the standoffs, the path for the gasket, and the placement of the ventilation cutouts. This layout is not just a rough sketch; it is a solution that is formally proven to satisfy every single geometric, thermal, and assembly constraint in the now-validated Axiom Repository.  
Phase 4: Geometric Manifestation  
The CAD Execution Agent is finally activated. Its task is simple and deterministic. The Orchestrator queries the Axiom Repository and provides the agent with a locked, immutable dictionary of parameters:

JSON

{  
  "enclosure\_length": 120.5,  
  "enclosure\_width": 80.0,  
  "enclosure\_height": 35.0,  
  "wall\_thickness": 2.5,  
  "corner\_radius": 5.0,  
  "pcb\_standoff\_height": 5.0,  
  "gasket\_groove\_width": 2.0,  
  "gasket\_groove\_depth": 1.5,  
  "vent\_slot\_width": 1.0,  
  "vent\_slot\_count": 8  
}

The Execution Agent's code is a direct, unambiguous translation of these parameters into freecad-mcp commands. The geometry is simply the inevitable result of the verified graph.

### **Analysis: How JITC Prevents Common Failures**

This "geometry-last" approach systematically prevents common and costly design failures:

* **Component Interference & Tolerance Stack-Up:** These issues are impossible in the final design because the CP solver used in Phase 2/3 must find a solution that is valid across the entire specified tolerance range for all components. The topological plan is only approved if a valid assembly exists for the worst-case tolerance combinations.  
* **Thermal Failure:** As demonstrated, thermal inconsistencies are caught and resolved at Gate 2→3, long before any physical or virtual prototype is built. The design cannot proceed to the expensive geometry phase until the thermal model is proven valid.  
* **Unmanufacturability:** Constraints related to the manufacturing process (e.g., draft angles for injection molding, minimum feature size for 3D printing) are formalized as dependencies in Phase 2\. The topological plan in Phase 3 must satisfy these constraints, ensuring the resulting geometry is manufacturable by design.  
* **Assembly Conflicts:** The dependency graph can include constraints for the assembly sequence (e.g., DEP-210: PCB\_must\_be\_installed\_before\_lid\_is\_fastened). The topological plan is validated against these constraints, guaranteeing a valid order of operations exists.

### **The Final Phase: Deterministic Code Generation**

The output of the Execution Agent is not a creative interpretation but a direct transcription. The parameter dictionary from the previous section would be consumed by a simple Python script using the freecad-mcp library:

Python

\# Illustrative snippet of the Execution Agent's deterministic script  
import freecad\_mcp

def generate\_enclosure(params):  
    \# Create the main body  
    box \= freecad\_mcp.Part.makeBox(  
        params\['enclosure\_length'\],  
        params\['enclosure\_width'\],  
        params\['enclosure\_height'\]  
    )  
      
    \# Shell the box to create walls  
    box \= box.makeThickness(  
        \[-box.Faces\], \# Open the top face  
        \-params\['wall\_thickness'\],  
        1e-3  
    )  
      
    \# Add fillets to corners  
    box \= box.fillet(  
        params\['corner\_radius'\],  
        \[e for e in box.Edges if 'Z' in e.normalAt(0)\]  
    )  
      
    \#... and so on, for every parameter in the dictionary.  
    \# No decisions, no logic, just direct translation.  
      
    return box

\# The Orchestrator provides the validated parameter dictionary  
validated\_parameters \= {... }   
final\_part \= generate\_enclosure(validated\_parameters)

This clear separation of concerns—complex, multi-domain reasoning in the early phases versus simple, deterministic transcription in the final phase—is the ultimate expression of the JITC framework's power to deliver correct, reliable, and verifiable results.

## **System Robustness and Implementation Blueprint**

A conceptual architecture, no matter how sound, is only as valuable as its potential for robust implementation. This section addresses the practical considerations for building, deploying, and maintaining a JITC system. It focuses on protocols for failure recovery, root-cause analysis, and the essential logging and testing practices required to create a reliable and observable prototype.

### **Failure Recovery and Root-Cause Analysis via Dependency Tracing**

Even with a priori validation, failures can occur. A physical prototype might fail due to an unmodeled physical effect, a supplier might deliver a component that is out of spec, or a user requirement might be found to be incorrect after the fact. The JITC framework's architecture, particularly the version-controlled Axiom Repository, provides a powerful and unique toolkit for diagnostics and recovery.

When a failure is observed in the real world (e.g., a prototype enclosure cracks during a drop test), the analysis process is not a matter of guesswork. It is a systematic process of dependency tracing:

1. **Identify the Failed Constraint:** The observed failure is mapped back to a specific dependency in the Axiom Repository. In the drop test example, this would be DEP-0089: Impact\_Resistance.  
2. **Traverse the Dependency Graph:** The JITC system provides tools for an engineer or a diagnostic agent to perform a root-cause analysis by traversing the dependency graph *backwards* from the point of failure. The source\_of\_truth field in each dependency object creates a directed, auditable trail of causality.  
3. **Trace the Causal Chain:** The engineer can trace DEP-0089 back to its sources. They might find it was derived from DEP-004 (Material\_Choice \= 'ABS') and DEP-0031 (Wall\_Thickness \= 2.5mm). The engineer can then examine the source of DEP-004, which was a UserRequirement.  
4. **Pinpoint the Root Cause:** This process might reveal that the initial user requirement for ABS plastic was based on an incorrect assumption about the device's operational environment, and a more robust material like polycarbonate should have been specified. Because every dependency is linked to its source and timestamped, the system can pinpoint the exact origin of the faulty constraint.  
5. **Initiate Recovery:** With the root cause identified, the recovery process is structured and controlled. The System Architect initiates a new branch in the version-controlled repository, modifies the root dependency (DEP-004 is changed to 'Polycarbonate'), and re-runs the entire phased workflow from that point. The JITC system automatically propagates the consequences of this change throughout the graph, re-validating every affected dependency and generating a new, corrected design. This ability to trace dependencies is analogous to path analysis in software engineering, which is used for debugging and performance tracing by mapping connections between components.16

### **Guidelines for Prototyping: Test Outputs, Console Logging, and Error Logging Protocols**

Building a prototype of a JITC system requires a strong emphasis on observability, a principle central to enterprise-grade agentic frameworks.2 The internal state of the system, particularly the decisions made by the Orchestrator and the state of the Axiom Repository, must be transparent to developers and administrators. The following protocols are essential for a successful implementation.

#### **Console Logging**

Every significant event within the system must be logged to the console (or a dedicated logging service) in a structured format (e.g., JSON). Each log entry should include:

* **Timestamp:** ISO 8601 format for precise event ordering.  
* **Source:** The ID of the component generating the log (e.g., JITC\_Orchestrator, SystemArchitect\_Agent\_01, AxiomRepository\_API).  
* **EventType:** A clear, enumerated event type (e.g., PHASE\_TRANSITION, AGENT\_ACTIVATED, REPO\_QUERY, GATE\_CHECK\_START, GATE\_CHECK\_FAIL).  
* **Payload:** A JSON object containing relevant data, such as the agent's input, the query being executed, or the result of an action.

This structured logging allows for powerful filtering and analysis, enabling developers to reconstruct the exact sequence of events leading to any given state.

#### **Test Outputs**

To facilitate debugging and validation of the framework itself, the system should generate human-readable summary reports at key checkpoints, particularly after successfully passing a Verification Gate. This "Gate Report" should be saved as a test artifact and include:

* **Gate ID and Timestamp:** G2-\>3\_PASS\_2025-09-15T14:00:00Z.  
* **Repository State Summary:** Key metrics about the Axiom Repository at the time of validation (e.g., total number of dependencies, breakdown by status, overall graph completeness score).  
* **Validated Plan Summary:** For later gates, a summary of the validated plan (e.g., key parameters of the topological plan).  
* **Link to Full Log:** A reference to the detailed validation log for that gate run.

These outputs provide a clear, high-level snapshot of the system's progress and are invaluable for regression testing and quality assurance.

#### **Error Logging**

Failures, especially at Verification Gates, are not just errors; they are critical data points that drive the design process. Error logs must be detailed, specific, and actionable. A GATE\_CHECK\_FAIL event log must contain:

* **Failed Gate ID:** The specific gate that failed (e.g., G2→3).  
* **Failure Reason:** A clear, enumerated reason (e.g., COMPLETENESS\_CHECK\_FAILED, CONFLICT\_DETECTED, CYCLE\_DETECTED).  
* **Conflicting Dependencies:** A list of the dependency\_ids that are directly implicated in the failure.  
* **CP Solver Output:** If the failure was a constraint conflict, the raw output from the CP solver should be included to aid the System Architect in its resolution task.

By implementing these rigorous logging and output protocols from the outset, developers can ensure that the JITC system is not a "black box," but a transparent, auditable, and maintainable framework for building the next generation of reliable AI-driven design tools.

## **Conclusion and Future Directions**

The Just-in-Time Context (JITC) framework, as specified in this architectural blueprint, represents a deliberate and fundamental departure from prevailing execution-centric paradigms in agentic AI. By adopting a dependency-first philosophy, it redefines the primary role of an AI system from that of a dynamic task orchestrator to a rigorous architect of certainty. The core innovation lies in treating complex design problems as formal Constraint Satisfaction Problems, demanding that a complete, consistent, and verifiable "network of consequences" be constructed and validated *before* any final artifact is generated. This "geometry-last" approach, managed through a phased, gate-driven workflow, systematically engineers out the possibility of late-stage failures, ensuring that the final output is the deterministic and mathematically certain result of its validated specification.

### **Summary of the JITC Framework's Transformative Potential**

The transformative potential of the JITC framework can be summarized in four key areas:

1. **Shift from Reactive to Proactive Design:** The framework moves the core "intelligence" of the system to the very beginning of the process. Problems are not solved through iterative trial and error during execution but are proactively de-risked through formal modeling and a priori validation.  
2. **Elimination of Late-Stage Rework:** By identifying and resolving conflicts, inconsistencies, and unmanufacturable designs at automated Verification Gates, the framework prevents errors from propagating into more expensive stages of development, such as physical prototyping or software implementation.  
3. **Creation of Deterministic and Verifiable Outputs:** The intentional de-skilling of the final Execution Agent ensures that the generated artifact is a perfect transcription of the proven plan. This removes the variability and potential for hallucination inherent in letting a creative LLM perform the final step, leading to highly reliable and predictable outcomes.  
4. **A Fully Auditable Design Process:** The version-controlled Axiom Repository serves as an immutable ledger of the entire design journey. Every requirement, assumption, calculation, and decision is captured, timestamped, and linked, providing unprecedented transparency and enabling powerful root-cause analysis.

### **Avenues for Future Research**

While this blueprint specifies a robust framework for deterministic problems, its core principles can be extended to address more complex and uncertain domains. Two primary avenues for future research stand out.

#### **Probabilistic Dependencies**

The current JITC model operates on the assumption of deterministic constraints. However, many real-world problems involve uncertainty. For example, material properties can vary, supplier lead times are stochastic, and market forecasts are probabilistic. Future research could extend the framework by incorporating concepts from **Probabilistic Dependency Graphs (PDGs)**.33 PDGs are a class of graphical models designed to handle inconsistent beliefs and uncertainty, offering greater modularity than traditional Bayesian Networks.33

An advanced JITC framework could use a probabilistic schema for dependencies, allowing values to be represented as distributions rather than scalars (e.g., wall\_thickness: NORMAL(mean=2.5, std\_dev=0.1)). The CP solver could be replaced with a probabilistic constraint solver. This would enable the system to perform sophisticated risk analysis, calculate the probability of success for a given design, and optimize for robustness under uncertainty, answering questions like, "What is the design with the highest probability of meeting all performance targets given the known variability in our manufacturing process?"

#### **Dynamic Constraint Relaxation**

The current framework treats all constraints as hard constraints; a solution is only valid if it satisfies every single one. This can be brittle in the face of over-constrained problems, where no perfect solution exists.27 The field of

**Flexible CSPs** addresses this by allowing for the partial relaxation of constraints, treating some as preferences rather than strict requirements.9

A future iteration of the JITC framework could incorporate the concept of "soft" and "hard" constraints. When the Validator agent determines that a problem is unsolvable, a new "Negotiator" agent could be activated. This agent would analyze the dependency graph to identify the "softest" constraints (e.g., those derived from user preferences rather than physical laws) that are part of the conflict. It could then engage the user in a collaborative optimization dialogue: *"A solution is impossible with the current constraints. To proceed, would you prefer to relax the maximum weight by 5% (violating DEP-USER-012) or reduce the battery capacity by 10% (violating DEP-PERF-007)?"* This would transform the JITC system from a pure validator into an intelligent negotiation and trade-off analysis partner, guiding users toward the optimal achievable solution in a complex and constrained design space.

