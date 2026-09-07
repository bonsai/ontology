# 研究計画

## 1. 研究テーマ

**タグ群マッチ・オントロジシステム — 多層意味グラフによる異分野リポジトリの自己組織化**

## 2. 研究目的

異なるドメインに分散するリポジトリ・知識・能力を、タグ群を意味署名として接続し、意味グラフ、能力、エージェント、ワークフローへ変換できる計算可能なオントロジを構築する。

## 3. 中心仮説

> タグ群は対象の意味的特徴を表す署名であり、タグ群同士のマッチングによって異分野間の意味的接続と再利用可能な能力を発見できる。

## 4. 研究モデル

```text
repo
 ↓
semantic observation
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
 ↓
semantic review
```

## 5. 研究課題

### RQ1
タグ群は異分野リポジトリの意味的類似性をどの程度表現できるか。

### RQ2
単純な文字列一致を超えて、関連概念・上位概念・変換関係を導入するとマッチング精度は向上するか。

### RQ3
タグ群から抽出されたクロスドメイン能力は、実際の再利用可能な能力として検証できるか。

### RQ4
意味グラフから capability → agent → workflow を生成することで、リポジトリ群の自己組織化を実現できるか。

### RQ5
実行結果と現実世界の evidence をフィードバックすることで、オントロジの品質を継続的に改善できるか。

## 6. 実験対象

初期実験では BONSAI の実リポジトリ群を対象とする。

- repository
- README
- directory structure
- workflow
- declared metadata
- observed repository state

クロスドメイン実験の代表例として `dots` を使用する。

```text
pixel / tile / sprite
        ↕
       grid
        ↕
stitch / pattern / motif
        ↕
 knitting / embroidery / textile
```

## 7. 比較モデル

### Baseline A
単純なタグ集合による Jaccard similarity。

\[
M(A,B)=\frac{|T_A\cap T_B|}{|T_A\cup T_B|}
\]

### Baseline B
重み付きタグマッチング。

### Proposed Model
exact / related / parent / transformation を含む多層意味グラフによるマッチング。

## 8. 評価指標

- semantic similarity
- cross-domain discovery rate
- capability discovery rate
- transformation discovery rate
- cluster stability
- agent generation validity
- workflow execution success
- evidence-based validation rate
- false positive / false negative

## 9. 計算基盤

```text
bonsai/repos
     ↓
BigQuery
     ↓
BQML
     ↓
clustering / scoring
     ↓
ontology / synapse
     ↓
ecosystem
```

将来的には Synapse を weighted edge として扱い、行列・グラフへの射影と機械学習を組み合わせる。

## 10. 検証ステップ

1. リポジトリ観測データを収集する。
2. タグ群を生成する。
3. タグ群間の baseline similarity を計算する。
4. 意味関係を付与する。
5. 多層グラフを構築する。
6. クロスドメインクラスタを抽出する。
7. capability を抽出する。
8. agent / workflow への変換可能性を検証する。
9. 実行結果を evidence として収集する。
10. ontology を再評価する。

## 11. 最小実証実験

最初から全リポジトリを対象にせず、少数の異分野リポジトリで検証する。

```text
Famicom / pixel
       ↕
dots / grid
       ↕
knitting
       ↕
embroidery
       ↕
textile
```

この小規模実験で、単純 Jaccard と意味関係付きマッチングとの差を確認する。

## 12. 成果物

- ontology specification
- tag-set schema
- semantic relation schema
- synapse schema
- matrix projection
- benchmark dataset
- clustering experiments
- capability extraction experiment
- repo2agent prototype
- evidence feedback loop
- research paper

## 13. 研究の到達点

最終的な到達点は、リポジトリを固定カテゴリへ分類するシステムではなく、観測された資産から意味関係・能力・エージェント・ワークフローを発見し、実行結果によって意味モデルを更新する自己組織化システムである。

```text
Observation
    ↓
Meaning
    ↓
Relation
    ↓
Capability
    ↓
Agent
    ↓
Action
    ↓
Evidence
    ↺
```

## 14. 今後の研究

- タグ間意味距離の定量化
- Synapse の重み学習
- 行列分解・グラフ分析
- BQML によるクラスタリング
- クロスドメイン変換コストのモデル化
- ontology declaration の品質評価
- repo2agent の自動生成
- 大規模リポジトリ群での自己組織化評価
