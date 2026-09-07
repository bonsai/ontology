# BONSAI Ontology

BONSAI Ontology defines the semantic layer for connecting repositories, domains, capabilities, agents, workflows, and eventually human preference profiles.

## Separation of concerns

This repository is deliberately divided into **theory** and **research**.

```text
ontology/
├── theory/       # what the model means
├── research/    # how the model is tested
└── README.md    # navigation and contract
```

### Theory

[`theory/`](theory/) contains the conceptual model:

- concepts and relation types
- tag sets as semantic signatures
- relation-as-state
- state, evidence, time, and transition
- domain as a semantic cluster
- declaration vs inference
- semantic graph
- deterministic computation vs stateful semantics

The central principle is:

> **Ontology defines meaning; evidence defines observation; state defines the current relation; time defines change; computation evaluates state; workflows act on state.**

### Research

[`research/`](research/) contains the empirical side:

- research plans
- papers
- hypotheses
- experiments
- benchmarks
- evaluation
- evidence

Research may revise theory, but research results do not silently become canonical ontology meaning.

## Relation as State

A relation is not a permanent deterministic fact.

```text
A ↔ Relation State ↔ B
       │
       ├─ strength
       ├─ confidence
       ├─ evidence
       ├─ observed_at
       └─ transition history
```

A relation may emerge, strengthen, weaken, disappear, or change meaning over time.

## Domain as State of Organization

A domain is a semantic cluster rather than a permanent ownership label.

```text
observations
   ↓
features
   ↓
relation state
   ↓
cluster
   ↓
domain hypothesis
   ↓
validation
   ↓
declared domain
```

## Lifecycle

```text
observed → inferred → proposed → validated → declared
```

AI and statistical models may discover candidate relations and clusters. Canonical semantic meaning is explicitly declared.

## Architecture boundary

```text
Ontology
  → meaning
Evidence
  → observation
State
  → current knowledge
Matrix
  → deterministic computation
BQML
  → statistical discovery
AW
  → workflow and action
```

Operational implementation lives in the corresponding Bonsai repositories; this repository defines the semantic contract and its research basis.
