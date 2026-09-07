# Human Tag Matrix Matching

## 嗜好タグから出会い・発見へ

> Skeleton / working paper.

## Abstract

人間の嗜好をタグ群として表現し、タグ行列とオントロジマッチングによって人と人の意味的関係を発見する応用モデルを検討する。

## Input axes

- 酒
- 本
- レコード
- 映画
- 食
- 旅行
- 趣味
- 価値観

## Model

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

## Matching dimensions

### Similarity

共通する嗜好・概念・経験を測る。

### Complementarity

異なる嗜好の組み合わせが新しい経験を生む可能性を測る。

### Shared Values

趣味そのものではなく、その背後にある価値観・関心・行動原理の共有を測る。

## Central hypothesis

> 良いマッチングは「同じものが好きな人」を探すだけでなく、「違いを持ちながら共通の価値によって新しい発見を生み出せる人」を発見する。

## Research questions

- 嗜好タグは人間の意味的特徴をどの程度表現できるか。
- 単純一致と意味マッチングの差は何か。
- Complementarity を導入すると発見可能性は向上するか。
- Shared Values は長期的な相互作用の説明変数になり得るか。
- 実際の出会い・反応を evidence として再学習できるか。

## Ethical considerations

人間を固定的に分類するのではなく、本人の自己申告と更新可能な嗜好を中心に扱う。推論された属性と本人が宣言した属性を分離し、センシティブな属性を不必要に推論・利用しない。

## Future work

- preference ontology
- tag matrix schema
- weighted semantic matching
- complementarity model
- shared-value model
- interaction feedback
- privacy-preserving evaluation
