---
title: "縦構造: グリッド列/Grid column"
free: true
---

グリッド列とは、webページの構成で、 **縦の列(column)** に該当します。

![](https://storage.googleapis.com/zenn-user-upload/j88jygxlzmuavepq6sutwgfumf1b)

この図の青い領域が、グリッド列の範囲です。

この範囲(グリッド列)を操作するには、以下のプロパティが用意されています。

こちらのプロパティは、使用頻度が高く、優先的に使用できるようになると良いものです。

プロパティ名 | 役割
------------ | -------------
`grid-template-columns` | 列(column)の横幅の大きさを指定するプロパティ

:::message
プロパティ名が複数形の `columns` であることに気がついたでしょうか？
これは、 `grid-template-columns`が、グリッドコンテナーに付与するプロパティだからです。
:::