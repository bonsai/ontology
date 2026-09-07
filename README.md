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

## Multi-layer semantic graph

```text
repo / person
  ↕
cluster
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
```

This allows apparently unrelated repositories, domains, and human profiles to become connected when they share a deeper representation.

### Example: Dots

The concept `dots` connects domains such as:

- Famicom / pixel art: `pixel`, `tile`, `sprite`, `grid`
- knitting: `stitch`, `grid`, `pattern`
- embroidery: `stitch`, `grid`, `motif`
- textile: `pattern`, `grid`, `repeat`

The important relation is not that these projects belong to the same business domain. It is that they share a **discrete representation** and can support transformations such as:

`pixel_grid → stitch_grid`

`pixel/sprite → textile_pattern`

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
tags
 ↓
ontology
 ↓
cluster
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
new tags / semantic review
```

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
