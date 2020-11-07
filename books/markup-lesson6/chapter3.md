---
title: "CSSグリッドの超基礎"
free: true
---

# Flexboxとの構造の違いと、共通概念

簡単にCSSグリッドとFlexboxの**構造の違い**を説明すると、

Flexbox | Gridレイアウト
------------ | -------------
**1つの軸（`flex-direction`）** で、アイテムを縦方向か横方向か**どちらか**を決める構造 |  `横(row: 行)` と `縦(column: 列)` の**2つの軸**で、アイテムを縦方向か横方向か決める構造

です。

:::message
「rowとcolumnの、どちらが縦方向と横方向で...」と考えると混乱しやすいので、先グリッドラインのチャプターで覚え方を紹介します。
今は2方向の軸、rowとcolumnがあることを、情報として読んでおくところまででOKです。
:::

対照的に、**共通する考え方**を簡単に説明すると、

- 親要素（コンテナー）がある
- 子要素（アイテム）がある

です。

![container-and-item](https://storage.googleapis.com/zenn-user-upload/0nsst3asvpjvsiba72sz0a18r5i4)

[マークアプ言語シリーズ: Lesson 4 並列、Flexbox](https://zenn.dev/arisa_dev/books/markup-lesson4)の、[「基本構文 1: Flexコンテナーとアイテム」（無料公開部分）](https://zenn.dev/arisa_dev/books/markup-lesson4/viewer/chapter3)で、この構造を学習しましたね。

上記の、特にFlexboxとCSSグリッドの構造の違いについては、詳しくはこれから学習していきます。