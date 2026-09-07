# BONSAI Ontology

## Tag-Set Matching Ontology

This repository defines a semantic ontology for organizing heterogeneous repositories, domains, capabilities, agents, and workflows through **tag sets as semantic signatures**.

### Core idea

A repository is not classified only by a single domain. It can participate in multiple semantic clusters through an explicit set of concepts, tags, capabilities, representations, and transformations.

- `repo` = responsibility
- `tag set` = semantic signature
- `domain` = semantic cluster
- `capability` = reusable connection
- `ontology` = declared meaning graph
- `agent` = executable semantic role
- `workflow` = path from meaning to action
- `evidence` = feedback from the real world

The central matching operation compares two tag sets and discovers semantic affinity:

`T_A = {a1, ..., an}`

`T_B = {b1, ..., bm}`

A basic similarity is the Jaccard-style score:

`M(A,B) = |T_A ∩ T_B| / |T_A ∪ T_B|`

For production use, semantic relations may be weighted so that exact concepts, related concepts, and transformations contribute differently.

## Multi-layer semantic graph

```text
repo
  ↕
cluster
  ↕
concept / tag-set
  ↕
capability
  ↕
agent
  ↕
workflow
  ↕
provider / real world
```

This allows apparently unrelated repositories to become connected when they share a deeper representation.

### Example: Dots

The concept `dots` connects domains such as:

- Famicom / pixel art: `pixel`, `tile`, `sprite`, `grid`
- knitting: `stitch`, `grid`, `pattern`
- embroidery: `stitch`, `grid`, `motif`
- textile: `pattern`, `grid`, `repeat`

The important relation is not that these projects belong to the same business domain. It is that they share a **discrete representation** and can support transformations such as:

`pixel_grid → stitch_grid`

`pixel/sprite → textile_pattern`

## Declaration and inference

Ontology data distinguishes observation from semantic commitment:

```text
observed → inferred → proposed → validated → declared
```

Repository facts should come from observation systems such as `bonsai/repos`. The ontology records the canonical semantic declaration. AI may propose clusters and relations, while the ontology remains the source of declared meaning.

## Self-organization loop

```text
repo
 ↓
tags
 ↓
ontology
 ↓
cluster
 ↓
capability
 ↓
agent
 ↓
workflow
 ↓
real world
 ↓
evidence
 ↓
new tags / semantic review
```

This ontology is intended to provide the semantic layer for the wider BONSAI ecosystem and to support `repo2agent`: repository facts can be transformed into semantic roles, capabilities, agents, and executable workflows.

## Related implementation

The semantic registry can be maintained in `bonsai/ecosystem.md`, while repository observations remain in `bonsai/repos`.

The ontology is therefore the contract between observed repository state and executable organization.
