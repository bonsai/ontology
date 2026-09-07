# Semantic Graph — Skeleton

## Purpose

Represent repositories, concepts, tags, domains, capabilities, agents, workflows, and human preference profiles as a multi-layer semantic graph.

## Node types

- `repo`
- `concept`
- `tag`
- `domain`
- `capability`
- `agent`
- `workflow`
- `person`
- `evidence`

## Edge model

Edges are relation states rather than immutable facts.

```text
node A ↔ relation state ↔ node B
```

Each edge state may carry strength, confidence, evidence, time, and transition history.

## Layering

```text
observation
  ↓
tag
  ↓
concept
  ↓
relation state
  ↓
cluster / domain
  ↓
capability
  ↓
agent
  ↓
workflow
```

## Open questions

- How should relation states be aggregated?
- How should conflicting evidence be represented?
- When should a cluster become a declared domain?
- How should expired relations remain queryable?
