# AX — What Is and What Can Be Done

## Definition

**AX defines and operates both what something is and what an agent can do with it.**

AX is the operational interpretation of Ontology for agent action. It connects a bounded world model to typed actions, WorkTypes, Tasks, Workflows, Agents, and AW execution.

```text
AX
├── BE — であること
│   ├── Object Type
│   ├── Property Type
│   ├── State Type
│   ├── Relation Type
│   └── Evidence Type
│
└── DO — できること
    ├── Action
    ├── WorkType
    ├── Input / Output Type
    ├── Preconditions
    ├── Effects
    ├── Permission
    └── Verification
```

## 1. Ontology is not only nouns

A useful operational ontology must describe both:

- **nouns** — objects, properties, relations, states
- **verbs** — actions, work types, transitions

This follows the operational direction of modern ontology systems: semantic objects are complemented by kinetic actions. Palantir explicitly describes its Ontology as containing semantic elements such as objects, properties, and links together with kinetic elements such as actions and functions. BONSAI uses this as a reference, while adding field observation and explicit scope boundaries before ontology declaration.

BONSAI therefore treats ontology as a typed model of a bounded world **and** the possible changes that can be made to that world.

## 2. BE — であること

BE answers:

> What is this?

The BE layer contains:

| Primitive | Meaning |
|---|---|
| ObjectType | kind of entity |
| PropertyType | typed attribute |
| StateType | possible/current condition |
| RelationType | semantic connection between objects |
| EvidenceType | evidence supporting an observation or claim |

Example:

```text
Design
  status: review_pending
  image: Image
  dimensions: Dimensions
```

Relations are stateful. A relation is not assumed to be a permanent deterministic edge:

```text
A ↔ Relation State ↔ B
```

A relation may be observed, inferred, proposed, validated, strengthened, weakened, or removed as evidence and time change.

## 3. DO — できること

DO answers:

> What can be done?

The DO layer contains typed verbs and their operational constraints.

```text
Action
  = Verb
  + Input Type
  + Output Type
  + Preconditions
  + Effects
  + Authorization
  + Verification
```

The important distinction is:

> **Capability is not permission.**

An ontology may declare that an action is possible without granting an agent permission to execute it.

## 4. WorkType — 仕事の型

A WorkType is a typed work pattern.

```text
WorkType = Object/State → Verb → Object/State
```

Examples:

```text
create(Design)
  → EmbroideryPattern

approve(EmbroideryPattern)
  → ApprovedEmbroideryPattern

manufacture(ApprovedEmbroideryPattern)
  → Product
```

The verb is the semantic core of the WorkType. The input and output types constrain what the work means and where it can be applied.

A WorkType is not an Agent.

```text
WorkType = what work is possible
Agent    = who/how the work is performed
```

## 5. Task — 仕事の実行インスタンス

A Task is one concrete execution of a WorkType.

```text
Task = WorkType + concrete input + context + execution state
```

Example:

```yaml
task:
  type: create_embroidery_pattern
  input: design-001
  status: pending
```

A Task has its own lifecycle:

```text
proposed
  ↓
authorized
  ↓
ready
  ↓
running
  ↓
completed / failed / cancelled
  ↓
verified
```

## 6. Workflow — 仕事の流れ

Workflow composes WorkTypes and Tasks into an operational flow.

```text
Design
  ↓
create
  ↓
EmbroideryPattern
  ↓
approve
  ↓
ApprovedPattern
  ↓
manufacture
  ↓
Product
```

Therefore:

```text
WorkType = 仕事の型
Task     = WorkTypeの実行インスタンス
Workflow = 仕事の流れ
```

## 7. Agent — 実行主体

An Agent is an execution subject that can perform authorized work.

The Agent should not invent the ontology of its own action at execution time. It operates against declared types, WorkTypes, constraints, and authorization.

```text
Ontology
  ↓
possible WorkTypes
  ↓
Agent capability
  ↓
Task
```

The Agent may reason, select, propose, and execute within its authorized operational boundary.

## 8. AW — Taskを実行するオーケストレータ

AW is the orchestrator.

```text
AW
├── instantiate Task
├── select / assign Agent
├── sequence Workflow
├── check Preconditions
├── request / check Authorization
├── execute / delegate
├── collect Result
├── collect Evidence
├── handle Deviation
└── trigger State Transition
```

AW does not define the meaning of the world. It operationalizes the meaning and possible actions already represented by the ontology.

## 9. AX operating loop

```text
FIELD / REAL WORLD
        ↓
FDE OBSERVATION
        ↓
EVIDENCE
        ↓
SCOPE
        ↓
ONTOLOGY
        ↓
BE / DO
        ↓
POSSIBLE WORKTYPE
        ↓
PRECONDITIONS
        ↓
AUTHORIZATION
        ↓
TASK
        ↓
WORKFLOW
        ↓
AW
        ↓
AGENT
        ↓
ACTION
        ↓
REAL WORLD
        ↓
OUTCOME
        ↓
EVIDENCE
        ↓
STATE TRANSITION
        ↺
```

This makes AX an operating loop rather than a static vocabulary.

## 10. Decision and action lineage

Every meaningful action should be traceable.

```text
Object
  ↓
Evidence
  ↓
State
  ↓
WorkType
  ↓
Task
  ↓
Agent
  ↓
Authorization
  ↓
Action
  ↓
Outcome
  ↓
Evidence
  ↓
State Transition
```

This enables audit, verification, rollback/deviation handling, and later ontology review.

## 11. AX and the field-first BONSAI architecture

BONSAI does not begin with an imagined universal ontology.

```text
野に降り立つ
  ↓
観察する
  ↓
証拠を残す
  ↓
スコープを限定する
  ↓
世界を型付けする
  ↓
可能な行動を型付けする
  ↓
運用する
```

The ontology is therefore a boundary around a mission-relevant world. AX turns that bounded world into an actionable world.

## 12. Relation to Wittgenstein

The AX model must remain sensitive to actual use. A verb such as `approve`, `create`, `assign`, or `manufacture` has meaning within a practice and context; it should not be treated as an abstract universal essence merely because it has been given a name.

The Wittgenstein Agent can therefore act as a semantic reviewer:

```text
proposed Object / Verb / WorkType
        ↓
actual usage
        ↓
context / language-game
        ↓
form of life
        ↓
ambiguity / category confusion
        ↓
bounded definition
```

This complements the formal AX model: the schema provides structure, while field usage validates whether the structure actually matches practice.

## 13. Core rules

1. Ontology defines what is in the bounded world.
2. AX defines what is and what can be done in that world.
3. Object types are nouns; WorkTypes and Actions are typed verbs.
4. A WorkType is not an Agent.
5. A Task is an execution instance of a WorkType.
6. A Workflow is a flow of WorkTypes and Tasks.
7. AW orchestrates Tasks and Workflows.
8. An Agent performs authorized work.
9. Capability does not imply permission.
10. Preconditions must be satisfied before execution.
11. Effects must be observable or verifiable where practical.
12. Evidence closes the execution loop.
13. State transitions preserve change over time.
14. Relations are stateful observations, not assumed permanent truths.
15. Scope and exclusions are explicit.
16. Inference is not automatically canonical ontology.
17. Actual field usage can trigger ontology review.

## 14. BONSAI separation of responsibilities

```text
fde-agent   → observe reality
ontology    → define bounded meaning and possible actions
AX          → operationalize BE + DO for agents
synapse     → represent changing relations
matrix      → deterministic computation
bqml        → statistical discovery / prediction
aw          → orchestrate execution
journal     → chronological operational record
History     → origin and narrative
```

## 15. Final definition

> **AX is the operational ontology for agents: it defines what things are, what states and relations they have, what can be done to them, under which types and conditions, by whom, and with what evidence and state transition.**

The purpose is not merely to describe the world.

> **AX makes the bounded world actionable and operable.**
