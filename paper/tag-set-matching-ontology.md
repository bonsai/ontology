# タグ群マッチ・オントロジシステム

## 多層意味グラフによる異分野リポジトリの自己組織化

**Tag-Set Matching Ontology System — A Multi-Layer Semantic Graph for Self-Organization of Heterogeneous Repositories**

> Skeleton / working paper. The authoritative full manuscript is maintained in the corresponding `.tex` file under `papers/`.

## Abstract

異種リポジトリ、ドメイン、能力、エージェントおよびワークフローを、タグ群を意味署名として扱うことで接続・自己組織化するシステムを提案する。

## Core hypothesis

> タグ群は対象の意味的特徴を表す署名であり、タグ群同士のマッチングによって異分野間の意味的接続と再利用可能な能力を発見できる。

## Model

```text
repo
 ↓
tag set
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
```

## Matching

\[
M(A,B)=\frac{|T_A\cap T_B|}{|T_A\cup T_B|}
\]

実用化では `exact`, `related`, `parent`, `transformation` 等の意味関係を重み付けする。

## Cross-domain example: dots

```text
Famicom / pixel
       ↕
      grid
       ↕
knitting / embroidery
       ↕
    textile
```

代表的変換:

```text
pixel_grid → stitch_grid
sprite → textile_pattern
```

## Declaration and inference

```text
observed → inferred → proposed → validated → declared
```

観測事実と意味的宣言を分離し、AI の推論を正式な意味へ昇格させる過程を明示する。

## repo2agent

リポジトリの観測からタグ、能力、エージェント、ワークフローを導出する。

## Research directions

- semantic tag distance
- weighted synapse
- matrix projection
- BQML clustering
- transformation discovery
- capability extraction
- repo2agent
- evidence feedback
- self-organization
