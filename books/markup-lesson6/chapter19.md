---
title: "grid-template-areas"
free: true
---

`grid-template-areas` の役割は、コンテナー用に用意された、CSSグリッドプロパティ一覧のチャプターで、簡単に確認をしましたね。

プロパティ名 | 役割
------------ | -------------
 `grid-template-areas`  | グリッド領域に名前を付けて、アイテムを配置するプロパティ

もう少しわかりやすく説明すると、以下の例で言う、「Item 1」や「Item 2」のグリッドアイテムや、それ以外のグリッドセルに、それぞれ名前を付けることができるというものです。

```css
grid-template-areas:
  "box1 box2"
  "box3 box4";
```

![](https://storage.googleapis.com/zenn-user-upload/qppurylcklmdhs2lr8xe55xy8b0g)

少し画像では「box1」「box2」などの名前が見づらいかもしれませんが、以下のソースコードをダウンロードして、ブラウザで確認をしてみましょう。

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-grid-template-areas)

`grid` をDeveloper Toolsでクリックし、 `grid-template-areas` のプロパティ付与のCSS記述箇所にカーソルをホバーすると、上記の画像と全く同じ状態で表示がされます。

:::message
グリッドアイテムに、これら `grid-template-areas` でつけた名前を付与する記述をします。
`grid-template-areas` だけでは、グリッドエリアに名前が付与されただけの状態で、配置は動きません。
:::

グリッドアイテムの配置指定に関しては、グリッドアイテム用に用意されたプロパティがありますので、先のチャプターで学習をします。