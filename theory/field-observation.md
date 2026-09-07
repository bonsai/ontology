# Field Observation → Ontology

## Purpose

The ontology must not begin by deciding what the world is.
It begins by going into the field, observing a bounded scene, and documenting what is actually present.

`bonsai/fde-agent` is the reality-facing observation layer. `bonsai/ontology` turns verified observations into an explicit, limited semantic model.

## Principle

> **野に降り立って観察してから、世界観を構築する。**

Ontology is therefore also a **scope boundary**.
It defines the smallest world that must be represented to accomplish the mission.

## Field loop

```text
MISSION
  ↓
FIELD / SCENE
  ↓
ATTENTION
  ↓
OBSERVE
  ↓
EVIDENCE
  ↓
SYMBOLIZE
  ↓
SCOPE
  ↓
ONTOLOGY HYPOTHESIS
  ↓
VALIDATE
  ↓
DECLARE
  ↓
MODEL / LOGIC / ACTION
  ↓
REAL WORLD
  ↓
OUTCOME / DEVIATION
  ↺
```

## Observation boundary

FDE must separate:

| Layer | Meaning |
|---|---|
| Evidence | What was encountered or measured |
| Observation | A bounded description of evidence |
| Interpretation | A provisional explanation |
| Ontology | Explicit concepts needed for the mission |
| Worldview | The working model of the bounded scene |

An interpretation must not silently become an ontology declaration.

## Scope wedge

Start with a **scope wedge**, not the whole organization or world.

```yaml
scope:
  mission: ""
  scene: ""
  actors: []
  objects: []
  processes: []
  constraints: []
  decisions: []
  actions: []
  evidence_sources: []
  excluded: []
  success_boundary: ""
```

The `excluded` field is intentional: what is outside the scope is part of the ontology design.

## From field to ontology

1. FDE establishes Mission, Scene, Phase, Role, and Aware.
2. FDE observes the real environment before proposing structure.
3. Evidence is recorded with source, time, and locator.
4. Observed entities, events, constraints, and decisions are symbolized.
5. A minimum scope wedge is declared.
6. Candidate objects, relations, states, and actions are proposed.
7. Relations remain stateful and evidence-backed.
8. The ontology is validated against the field.
9. Only then is a semantic worldview declared.
10. Actions and workflows test whether the ontology is operationally useful.

## FDE ↔ Ontology contract

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

## Anti-patterns

- designing the ontology from imagination before field observation
- modeling the entire world when the mission needs a small wedge
- confusing a source schema with the world it describes
- treating inferred relations as declared facts
- optimizing before understanding the scene
- allowing the ontology to expand without a mission or evidence

## Completion criterion

A field-derived ontology is useful when:

- its scope is explicit;
- every important concept has evidence or an explicit declaration rationale;
- exclusions are known;
- uncertainty remains visible;
- the model supports an operational decision or workflow;
- actual outcomes can feed back into the model.
