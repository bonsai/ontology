# Topology / Ontology / Entropy — Measurement Proposal

- Status: Research proposal; not yet canonical ontology
- Source: [Issue #2](https://github.com/bonsai/ontology/issues/2), RAW11-15 (2026-10-18)

## 1. Purpose

Create reproducible metadata for skills, agents, and MCP servers so their structural connections, semantic coverage, and description variability can be compared as JSONL records. Numeric scores must be accompanied by definitions, evidence, and limitations.

## 2. Indicator definitions

### Topology

**Question:** What is connected to what?

- Type: object
- Proposed fields: `node_count`, `edge_count`, `in_degree`, `out_degree`, `components`, `dependency_depth`
- Evidence: declared imports, MCP/tool references, explicit workflow links, or observed calls.
- Rule: distinguish declared edges from inferred edges; inferred edges require method and confidence.
- Missing graph evidence: `null` plus reason, not zero.

### Ontology coverage

**Question:** Which declared concepts/capabilities does this item cover?

- Type: object
- Proposed fields: `taxonomy_version`, `declared_concepts`, `observed_concepts`, `coverage_ratio`, `unmapped_terms`
- Denominator: only the versioned, applicable concept set for the evaluated item class.
- `coverage_ratio` is null if the denominator is undefined or zero.
- Keep declared metadata separate from concepts extracted by a model.

### Entropy / variability

**Question:** How much does the description or structure vary under a defined representation?

- Type: object
- Proposed fields: `method`, `unit`, `value`, `range`, `sample_size`, `uncertainty`
- A score is meaningful only with a defined distribution, tokenization/feature representation, and normalization.
- Do not label a generic complexity score as entropy.
- If the required observations or distribution are unavailable, value is null with a reason.

## 3. JSONL record proposal

```json
{
  "schema_version": "1",
  "subject": {"kind": "skill", "id": "example", "source": "path-or-url"},
  "observed_at": "2026-10-18T00:00:00Z",
  "topology": {"node_count": null, "edge_count": null, "method": "declared-edges-v1"},
  "ontology": {"taxonomy_version": "pending", "coverage_ratio": null, "method": "taxonomy-match-v1"},
  "entropy": {"method": "pending", "value": null, "unit": null, "range": null},
  "evidence": [],
  "limitations": ["taxonomy and entropy method not yet validated"]
}
```

This is a proposal, not a final schema. Values unavailable at collection time must use null/unknown and include a reason.

## 4. Parity checks

Parity means the same subject and schema version can be compared across representations or repeated collection runs. Before failing a parity check, specify:
- compared fields and canonicalization
- tolerated omissions and null handling
- numeric tolerance, if applicable
- source/version drift rules
- evidence required to reproduce the mismatch

A parity failure must report the fields, expected/actual values, source references, and comparison method. It must not imply semantic disagreement when the only difference is formatting or missing evidence.

## 5. Natural-language explanation

Every generated explanation should include:
1. result and value (or unknown)
2. operational definition/method version
3. evidence and observation time
4. comparison baseline, if any
5. limitations and confidence

Avoid causal claims from correlation alone. Distinguish measured, inferred, estimated, and unknown values.

## 6. Validation plan

1. Freeze schema and definitions as versioned research artifacts.
2. Collect a small hand-audited sample across skill, agent, and MCP subjects.
3. Run deterministic repeatability tests.
4. Compare automated metadata with manual annotations.
5. Measure missingness and false-positive inferred edges.
6. Publish thresholds only after empirical validation.

## 7. Promotion rule

This document remains research, not canonical theory. Only validated definitions may be promoted into `theory/`; experimental results and revisions stay in `research/`.
