# BONSAI Ontology

## Tag-Set Matching Ontology

This repository defines a semantic ontology for organizing heterogeneous repositories, domains, capabilities, agents, workflows, and eventually human preference profiles through **tag sets as semantic signatures**.

### Core idea

A repository or person is not classified only by a single domain. It can participate in multiple semantic clusters through explicit concepts, tags, capabilities, representations, transformations, preferences, and values.

- `repo` = responsibility
- `person` = preference/value profile
- `tag set` = semantic signature
- `domain` = semantic cluster
- `capability` = reusable connection
- `ontology` = declared meaning graph
- `agent` = executable semantic role
- `workflow` = path from meaning to action
- `evidence` = feedback from the real world

The basic matching operation compares semantic signatures. Beyond simple similarity, the system can model:

- `Similarity` — shared interests/concepts
- `Complementarity` — mutually useful differences
- `Shared Values` — common higher-level values or motivations
- `Transformation` — ability to translate one representation into another

## Relation as State

Ontology relations are not assumed to be permanent deterministic facts. A relation is a **stateful observation whose strength, confidence, evidence, and meaning may change over time**.

Instead of treating a relation as only:

```text
A ──related_to──> B
```

BONSAI models it as:

```text
A ↔ Relation State ↔ B
       │
       ├─ strength
       ├─ confidence
       ├─ evidence
       ├─ observed_at
       └─ transition history
```

A relation can therefore emerge, strengthen, weaken, disappear, or change its semantic interpretation. The ontology declares the kinds of relations that are possible; the knowledge state records their current observed status.

Example:

```yaml
relation:
  subject: bonsai/aw
  predicate: related_to
  object: bonsai/foo
  state:
    strength: 0.82
    confidence: 0.91
    observed_at: 2026-09-07
  evidence:
    - shared_topics
    - dependency
    - workflow
```

This separates **semantic possibility** from **current knowledge state**.

## State, Evidence, and Time

The ontology distinguishes relatively stable semantic definitions from changing knowledge about the world.

```text
Ontology
 ├─ concepts
 ├─ relation types
 └─ semantic constraints

Knowledge State
 ├─ relation state
 ├─ cluster membership
 ├─ confidence
 ├─ evidence
 ├─ time
 └─ transitions
```

A relation state follows the lifecycle:

```text
observed
   ↓
inferred
   ↓
proposed
   ↓
validated
   ↓
declared
```

Declaration is therefore not the same thing as observation. AI or statistical analysis may discover a useful relation or cluster, but canonical semantic meaning requires validation and declaration.

## Multi-layer semantic graph

```text
repo / person
  ↕
relation state
  ↕
cluster / domain
  ↕
concept / tag-set
  ↕
capability / preference / value
  ↕
agent
  ↕
workflow
  ↕
provider / real world
  ↕
evidence
```

This allows apparently unrelated repositories, domains, and human profiles to become connected when they share a deeper representation, while preserving the fact that those connections can change.

## Domain as a State of Organization

A `domain` is a semantic cluster, not a permanent ownership label.

Repository observations can produce candidate clusters through human reasoning, deterministic analysis, or statistical learning:

```text
repo observations
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

Thus a repository may have different domain affinities at different times, and a domain may emerge, split, merge, stabilize, or become obsolete.

## Deterministic Computation vs Stateful Semantics

The stateful relation model does not mean that every operation is non-deterministic.

The layers have different responsibilities:

```text
Ontology
  → declares concepts and possible relations

Evidence
  → records observations

State
  → represents current knowledge about relations

Matrix
  → performs deterministic calculations on state

BQML
  → discovers statistical patterns and predicts state

AW
  → routes state into workflows and actions
```

For example, similarity scores, distances, rankings, and feature calculations can be deterministic even though the underlying semantic relationship evolves over time.

## Example: Dots

The concept `dots` connects domains such as:

- Famicom / pixel art: `pixel`, `tile`, `sprite`, `grid`
- knitting: `stitch`, `grid`, `pattern`
- embroidery: `stitch`, `grid`, `motif`
- textile: `pattern`, `grid`, `repeat`

The important relation is not that these projects belong to the same business domain. It is that they share a **discrete representation** and can support transformations such as:

`pixel_grid → stitch_grid`

`pixel/sprite → textile_pattern`

The strength of these connections can itself be observed and updated as new repositories, capabilities, and transformations appear.

## Human preference extension

The same ontology can be applied to human preference profiles.

```text
person
 ↓
preference tags
 ↓
tag matrix
 ↓
ontology matching
 ↓
Similarity / Complementarity / Shared Values
 ↓
discovery / encounter
 ↓
real-world interaction
 ↓
evidence
 ↓
updated state
```

Possible input axes include:

`酒 / 本 / レコード / 映画 / 食 / 旅行 / 趣味 / 価値観`

The objective is not merely to find people who like the same things. It is to discover people whose interests, differences, and values can produce **new shared experiences and discoveries**.

## Declaration and inference

Ontology data distinguishes observation from semantic commitment:

```text
observed → inferred → proposed → validated → declared
```

Repository facts should come from observation systems such as `bonsai/repos`. Human preference data should likewise distinguish observed preference from inferred or proposed meaning. AI may propose clusters and relations, while the ontology remains the source of declared meaning.

## Self-organization loop

```text
repo / person
 ↓
tags / observations
 ↓
ontology
 ↓
relation state
 ↓
cluster / domain
 ↓
capability / preference / value
 ↓
agent / match
 ↓
workflow / encounter
 ↓
real world
 ↓
evidence
 ↓
state transition
 ↓
new tags / semantic review
```

The system is therefore not primarily a classification system. It is a **stateful semantic system** that observes changing relationships and uses those changes to reorganize executable structure.

## Research

### Papers

- [Tag-Set Matching Ontology System](papers/001-tag-set-matching-ontology.tex)
- [Human Tag Matrix Matching](papers/002-human-tag-matrix-matching.tex)

### Research plan

- [Research Plan](research/research-plan.md)

The research treats ontology as the semantic layer between observed assets and executable organization, and investigates whether the same computational model can generalize from repositories and agents to human preference matching.

## Related implementation

The semantic registry can be maintained in `bonsai/ecosystem.md`, while repository observations remain in `bonsai/repos`.

The ontology is therefore the contract between observed state and executable organization.

> **Core principle: ontology defines meaning; evidence defines observation; state defines the current relation; time defines change; computation evaluates state; workflows act on state.**
