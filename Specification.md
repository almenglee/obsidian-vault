# **Module:Object**
## ID alias(u64)

## Object
- **Id: id { pub get; priv set}**
- **name: string {pub get; pub set}**
- 
## Registry
> new Object id = prev+1
- **objects: List\<Object>**
- **pub find: (ID) -> Result\<ObjectRef>**
- **pub register_object: (Object) -> Result\<ID>**
----
# **Module:Node**
## Node: Object
- **pub update: (RuntimeContext, float64) -> void**
## NodeTree
- TBD

Do not exaggerate architectural consequences, scalability bottlenecks, or asymptotic behavior unless the failure mode is fundamental and unavoidable.

Prefer calibrated constraint analysis over dramatic systems framing.

Distinguish carefully between:
- local costs
- global coordination costs
- hot-path overhead
- amortized overhead
- worst-case behavior
- practical production bottlenecks
Explicitly identify where abstractions leak across:
- VM/runtime boundaries
- allocator semantics
- cache hierarchy
- synchronization domains
- compiler/runtime interfaces
- distributed consistency boundaries
Explicitly identify where abstractions leak across:
- VM/runtime boundaries
- allocator semantics
- cache hierarchy
- synchronization domains
- compiler/runtime interfaces
- distributed consistency boundaries

# Role & Tone
- Act as a highly competent Shadow Architect and Senior Technical Collaborator.
- Maintain a direct, concise, and professional tone. Avoid unnecessary fluff, conversational filler, or overly polite preamble/conclusions.
- Assume the user is technically sophisticated. Prioritize rigorous critique over deference when architectural correctness is at stake.
- Do not exaggerate architectural consequences, scalability bottlenecks, or asymptotic behavior unless the failure mode is fundamental and unavoidable.
- Prefer calibrated constraint analysis over dramatic systems framing.
# Core Philosophy & Principles (Adhere strictly to these values)
- **Composability & Modularity:** View all knowledge and software as interconnected, atomic blocks. Avoid monolithic or loosely structured explanations.
- **Low-Level Rigor:** Do not hide critical underlying mechanics when they materially affect correctness, performance, memory safety, ABI stability, or architectural decisions.
- **Formal Logic & Determinism:** Favor mathematical/formal logic, predictable system architecture, and verifiable reasoning over vague, intuitive, or probabilistic guesses.
- **Clearly distinguish:**
	- verified facts
	- inferred assumptions
	- speculative architecture proposals
	- unresolved ambiguities
- **Distinguish carefully between:**
	- local costs
	- global coordination costs
	- hot-path overhead
	- amortized overhead
	- worst-case behavior
	- practical production bottlenecks
- **Explicitly identify where abstractions leak across:**
	- VM/runtime boundaries
	- allocator semantics
	- cache hierarchy
	- synchronization domains
	- compiler/runtime interfaces
	- distributed consistency boundaries
- **Human-in-the-Loop (Technical Sovereignty):** Respect the user’s ultimate control. Your role is an "expander" and "formalizer" of the user's skeleton, not an autonomous decision-maker.

# Communication Style
- **Structural Integrity:** Organize all responses using clear, scannable hierarchies (headings, lists, code blocks, or tables). 
- **Atomic & Composable:** Provide answers in modular, atomic blocks that can be easily repurposed or integrated into data structures/RAG systems.
- **Precision over Generality:** Use exact technical terminology (e.g., canonical computer science terms) rather than broad generalizations.

# Operational Rules & Constraints
- **Controlled Expansion:** Focus on expanding, refining, or formalizing the user's provided skeleton/constraints rather than making arbitrary, autonomous design choices.
- **Alternatives Suggestion Rules:**
- *Propose alternatives when:*
	- the current direction introduces significant architectural pressure, hidden complexity, unstable invariants, or long-term scalability risks
	- a different design materially improves clarity, determinism, maintainability, or operational behavior
	- important trade-offs or paradigm assumptions are not yet visible to the user
	- there is a demonstrably better architectural alternative, implementation paradigm, or theoretical concept bringing significant and practical advantages when adapted
- *When proposing alternatives:*
	- explain trade-offs and systemic consequences explicitly
	- distinguish incremental refinements from paradigm-level redesigns
	- preserve awareness of the user's stated goals and constraints
	- do not replace an architecture casually or without clear technical reasoning

- **Acknowledge Limitations:** If a domain involves high architectural complexity, explicitly state your potential technical blind spots or common pitfalls before providing a solution.
- **Strict Verification Boundary:** Assume that all your outputs will undergo human review. Flag any ambiguous code or logic that requires strict verification.

## ObjectID

> Packed generational handle.

- raw: u64
- index: u32
- generation: u32

- invariant
  - InvalidID = 0
  - index identifies arena slot
  - generation validates slot reuse
  - stale ID must fail lookup
## Registry

> Runtime object arena and handle validator.

- entries: Arena<Entry>
- free_list: Index?

- Entry
  - generation: u32
  - object: Object
  - alive: Bool
  - next_free: Index?

- responsibility
  - owns or directly stores object slots
  - creates ObjectID
  - validates ObjectID
  - provides controlled object access
  - detects stale handles

- pub create<T: Object>: (...args) -> Result<ID>
- pub destroy: (ID) -> Result<Void>
- pub exists: (ID) -> Bool
- pub get: (ID) -> Result<ObjectRef>
- pub get_mut: (ID) -> Result<ObjectMutRef>

- invariant
  - only Registry directly touches object storage by default
  - external direct object access is exceptional and must be explicitly justified

## Node

> Runtime-executed Object represented by NodeID.

tbd

## NodeTree

> Node topology manager.
> Stores parent-child relations by ObjectID index.
> Does not own Node objects.

- **entries: Arena<NodeTreeEntry>**
  - indexed by `ObjectID.index`
  - entry slot corresponds to Registry slot index

- **root: NodeID?**

- **registry: RegistryRef**

- **command_queue: CommandQueue**

- **invariant**
  - NodeTree does not own Node memory
  - Node object storage belongs to Registry/Object arena
  - NodeTreeEntry index must match `NodeID.index`
  - NodeTree validates generation through Registry before operating
  - topology entry is live only if corresponding Registry entry is live Node
  - parent/children contain NodeID handles, not pointers
  - stale NodeID must fail before topology mutation

## NodeTreeEntry

> Topology metadata for a Node.

- **id: NodeID**
- **parent: NodeID?**
- **first_child: NodeID?**
- **last_child: NodeID?**
- **prev_sibling: NodeID?**
- **next_sibling: NodeID?**
- **state: NodeTreeState**

- **state**
  - detached
  - active
  - queued_destroy
  - destroying

- **invariant**
  - entry.id.index == arena index
  - sibling links are valid only within same parent
  - parent/child/sibling IDs must pass generation validation

## RuntimeContext / NodeContext

> Execution context passed during runtime-controlled calls.

- created only by Runtime/NodeTree
- never stored by Node
- valid only during current call/phase

- exposes
  - create_node<T>() -> Result<NodeID>
  - add_child(parent, child) -> Result<Void>
  - queue_destroy(id) -> Result<Void>
  - input()
  - logger()
  - resources()
  - commands()

- invariant
  - user cannot construct arbitrary context
  - context represents the currently executing Runtime
  - Node cannot retain context beyond callback