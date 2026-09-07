# BONSAI Ontology Theory

This directory contains the conceptual and formal theory of the BONSAI ontology.

## Reference architecture

Palantir's public Ontology architecture is a useful reference for one important design principle: an ontology should connect **objects and relationships to logic, actions, security, and operational workflows**, rather than stop at a static semantic/data catalog.

BONSAI adopts that lesson while keeping its own model:

```text
                 ┌───────────────┐
                 │   Ontology    │
                 │ meaning/types │
                 └───────┬───────┘
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

The key extension for BONSAI is that **relations are states**, not permanent deterministic edges. A relation carries confidence, evidence, time, and transition history.

## Skeleton

```text
theory/
├── README.md
├── relation-state.yaml      # relation is a state
├── state-transition.yaml    # state lifecycle and transitions
├── domain-state.yaml        # domain as organizational state
├── tag-signature.yaml       # tags as semantic signatures
├── capability.yaml          # capability extraction boundary
├── decision-model.yaml      # data + logic + action + security
├── security-model.yaml      # authorization and governance boundary
└── semantic-graph.md        # multi-layer graph model
```

## Four operational primitives

```text
Data      → what is observed
Logic     → how the state is evaluated
Action    → what can change the state/world
Security  → who/what may read, evaluate, or act
```

This follows the useful distinction between semantic objects/links and the kinetic side of actions and workflows.

## BONSAI-specific state model

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

- `ontology` defines meaning
- `repos` provides observed repository facts
- `synapse` represents changing relations
- `matrix` performs deterministic computation
- `bqml` performs statistical discovery/prediction
- `aw` routes, generates, and executes workflows
- `journal` records chronological events
- `History` preserves origin and narrative

## Core principle

> **Ontology defines meaning; evidence defines observation; state defines the current relation; time defines change; computation evaluates state; security governs access; actions change the world; workflows close the loop.**

## Decision-centric design

The ontology should not merely answer:

> "What is this?"

It should also support:

> "What is happening now?"
>
> "What could happen next?"
>
> "What evidence supports that conclusion?"
>
> "What action is available?"
>
> "Who or which agent is allowed to perform it?"
>
> "What happened after the action?"

This makes the ontology an operational decision substrate rather than a passive taxonomy.

## Separation

Theory defines **what the model means**.

Research defines **how the model is tested**.

Implementation belongs in the operational repositories such as `bonsai/ecosystem`, `bonsai/synapse`, `bonsai/matrix`, `bonsai/bqml`, and `bonsai/aw`.
