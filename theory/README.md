# BONSAI Ontology Theory

This directory contains the conceptual and formal theory of the BONSAI ontology.

## Field-first reference architecture

A useful reference from Palantir's public Ontology architecture is that an ontology should connect objects and relationships to logic, actions, security, and operational workflows rather than stop at a static semantic/data catalog. citeturn0search0turn0search1

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
                       Action
                         ↓
                      Workflow
                         ↓
                    Real World
                         ↓
                      Evidence
                         ↺
```

> **野に降り立って観察してから、世界観を構築する。**

The ontology is also a **scope boundary**: it defines the smallest world that must be represented for the mission, including explicit exclusions.

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
├── relation-state.yaml
├── state-transition.yaml
├── domain-state.yaml
├── tag-signature.yaml
├── capability.yaml
├── decision-model.yaml
├── security-model.yaml
└── semantic-graph.md
```

## Field → Ontology boundary

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
  Relation State
     ↓
  Decision Model
     ↓
bonsai/aw
  Action / Workflow
     ↓
  Real World
     ↓
  Result / Deviation
     ↓
bonsai/fde-agent
```

## Four operational primitives

```text
Data      → what is observed
Logic     → how the state is evaluated
Action    → what can change the state/world
Security  → who/what may read, evaluate, or act
```

## BONSAI state model

```text
observation
    ↓
relation state
    ↓
logic / matrix / BQML
    ↓
decision proposal
    ↓
AW action
    ↓
workflow / agent
    ↓
outcome
    ↓
evidence
    ↓
relation-state transition
```

Therefore:

- `fde-agent` observes reality and preserves field evidence
- `ontology` defines bounded meaning and scope
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
> "What action is available?"
>
> "Who or which agent is allowed to perform it?"
>
> "What happened after the action?"

## Core principle

> **Reality before model; evidence before interpretation; scope before abstraction; ontology defines meaning; state defines the current relation; time defines change; computation evaluates state; security governs access; actions change the world; workflows close the loop.**

## Separation

Theory defines **what the model means**.

Research defines **how the model is tested**.

Implementation belongs in the operational repositories such as `bonsai/ecosystem`, `bonsai/synapse`, `bonsai/matrix`, `bonsai/bqml`, and `bonsai/aw`.
