---
title: "横構造: グリッド行/Grid row"
free: true
---

グリッド行とは、webページの構成で、 **横の行(row)** に該当します。

![](https://storage.googleapis.com/zenn-user-upload/oeqk6h8y0ttzktfrhsu477rlcwji)

この図の青い領域が、グリッド行の範囲です。

この範囲(グリッド行)を操作するには、以下のプロパティが用意されています。

こちらのプロパティも、使用頻度が高く、優先的に使用できるようになると良いものです。

プロパティ名 | 役割
------------ | -------------
`grid-template-rows` | 行(row)の高さを指定するプロパティ

:::message
こちらも、プロパティ名が複数形の `rows` であることに気がついたでしょうか？
これも、 `grid-template-rows`が、グリッドコンテナーに付与するプロパティだからです。
:::