---
title: "flex-flow"
free: true
---

# コンテナに使用するFlexboxのプロパティ

## flex-flow: flex-directionとflex-wrapをひとまとめに

`flex-flow` の役割は、flex-directionとflex-wrapを1行で表します。

以下の `flex-flow` を使用していない例と、使用している例を見比べて、書き方を確認しましょう。

### flex-flow なし

```css
.sample {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
```

### flex-flow あり

```css
.sample {
  display: flex;
  flex-flow: column wrap;
}
```