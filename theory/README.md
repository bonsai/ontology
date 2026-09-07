# BONSAI Ontology Theory

This directory contains the conceptual and formal theory of the BONSAI ontology.

## Field-first reference architecture

A useful reference from Palantir's public Ontology architecture is that an ontology should connect objects and relationships to logic, actions, security, and operational workflows rather than stop at a static semantic/data catalog.

BONSAI adds a prior step: **field observation and scope definition**.

```text
                 FIELD / REAL WORLD
                         │
                         ↓
                   FDE OBSERVATION
                         │
                         ↓
                      EVIDENCE
                         │
                         ↓
                    SCOPE WEDGE
                         │
                         ↓
                     ONTOLOGY
                         │
        ┌────────────────┼────────────────┐
        ↓                ↓                ↓
     Objects          Relations        States
     Properties       Links            Evidence
        │                │                │
        └────────────────┼────────────────┘
                         ↓
                       Logic
                         ↓
                 Possible Actions
                         ↓
                   Authorization
                         ↓
                     Execution
                         ↓
                    Real World
                         ↓
                 Outcome / Evidence
                         ↺
```

> **野に降り立って観察してから、世界観を構築する。**

The ontology is also a **scope boundary**: it defines the smallest world that must be represented for the mission, including explicit exclusions.

## Two layers we must make explicit

### 1. World data layer — nouns

`world-model.yaml` defines the bounded representation of the world:

- objects
- properties
- states
- relations
- relation state
- observations
- evidence
- time
- exclusions

This is not merely a database schema. It is an evidence-backed, mission-scoped model of what is currently known about the world.

### 2. Possible action layer — verbs

`action-model.yaml` defines what can be done to that world:

- action type
- targets and inputs
- preconditions
- authorization
- expected effects
- external side effects
- executor/workflow
- verification evidence
- rollback/deviation handling
- audit lineage

An action is a **capability definition**, not permission to execute it. The default is proposal until authorization is established.

## Relation as State

The key BONSAI extension is that relations are states, not permanent deterministic edges. A relation carries confidence, evidence, time, and transition history.

```text
A ↔ Relation State ↔ B
```

## Skeleton

```text
theory/
├── README.md
├── field-observation.md    # field → evidence → scope → ontology
├── scope-wedge.yaml        # bounded world definition
├── world-model.yaml        # world data layer
├── relation-state.yaml
├── state-transition.yaml
├── domain-state.yaml
├── tag-signature.yaml
├── capability.yaml
├── decision-model.yaml     # data + logic + action + security + outcome
├── action-model.yaml       # possible actions / verbs
├── security-model.yaml
└── semantic-graph.md
```

## Field → Ontology → Action boundary

```text
bonsai/fde-agent
  OBSERVE
     ↓
  Evidence
     ↓
  Observation Package
     ↓
bonsai/ontology
  Scope / Meaning
     ↓
  World Data
     ↓
  Relation State
     ↓
  Logic / Decision
     ↓
  Possible Actions
     ↓
  Authorization
     ↓
bonsai/aw
  Workflow / Execution
     ↓
  Real World
     ↓
  Result / Deviation / Evidence
     ↓
bonsai/fde-agent
```

## Four operational primitives

```text
Data      → what exists / is observed now
Logic     → how the state is evaluated
Action    → what can change the state/world
Security  → who/what may read, evaluate, propose, or act
```

## BONSAI state model

```text
observation
    ↓
world state
    ↓
relation state
    ↓
logic / matrix / BQML
    ↓
action candidates
    ↓
decision proposal
    ↓
authorization
    ↓
AW execution
    ↓
outcome
    ↓
evidence
    ↓
state transition
    ↺
```

Therefore:

- `fde-agent` observes reality and preserves field evidence
- `ontology` defines bounded meaning, world data, and possible actions
- `repos` provides observed repository facts
- `synapse` represents changing relations
- `matrix` performs deterministic computation
- `bqml` performs statistical discovery/prediction
- `aw` routes, generates, and executes workflows
- `journal` records chronological events
- `History` preserves origin and narrative

## Decision-centric design

The ontology should support not only:

> "What is this?"

but also:

> "What is happening now?"
>
> "What is inside the current mission scope?"
>
> "What is deliberately outside the scope?"
>
> "What evidence supports this model?"
>
> "What actions are possible?"
>
> "What must be true before an action is allowed?"
>
> "Who or which agent is authorized to perform it?"
>
> "What happened after the action?"
>
> "Did the world change as expected?"

## Core principle

> **Reality before model; evidence before interpretation; scope before abstraction; ontology defines meaning; data represents the bounded world; state defines the current relation; time defines change; computation evaluates state; actions define possible change; security governs access; authorization permits execution; workflows change the world; evidence closes the loop.**

## Separation

Theory defines **what the model means**.

Research defines **how the model is tested**.

Implementation belongs in the operational repositories such as `bonsai/ecosystem`, `bonsai/synapse`, `bonsai/matrix`, `bonsai/bqml`, and `bonsai/aw`.
