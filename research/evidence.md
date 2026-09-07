# Evidence Registry — Skeleton

Evidence is the bridge between observed repository reality and ontology state.

## Evidence record

```yaml
id: ""
source: ""
type: repository # repository|commit|issue|workflow|document|human|model|event
observed_at: ""
locator: ""
claim: ""
confidence: 0.0
supports: []
contradicts: []
notes: ""
```

## Provenance requirements

- source is identifiable
- observation time is recorded
- claim is traceable
- confidence is explicit
- contradictory evidence is preserved

## Intended consumers

- ontology relation state
- domain discovery
- BQML features
- Matrix calculations
- AW routing
- repo2agent generation
