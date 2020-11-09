---
title: "grid-row, grid-column"
---

`grid-row` と `grid-column` の役割については、実は、説明はありませんでしたが、プロパティが実装されている例とコード自体は、本書にも、既にいくつか出てきています。

一番最初に本書で出てきた例としては、「グリッド軸(Grid axis)」のチャプターです。

ここには、実はコードも実例として載っていました。

実は、この例を用いて解説をしている、ほとんどのプロパティのチャプターで、 `grid-row` と `grid-column` は使用されています。（ `grid-areas` 以外 ）

プロパティ名 | 役割
------------ | -------------
`grid-row` | 行(row)のグリッドアイテムの位置を指定するプロパティ
`grid-column` | 列(column)のグリッドアイテムの位置を指定するプロパティ

では、ここで、まだ着目をしていなかった `grid-row` と `grid-column` を、これまでの例を使って、具体的にどのように使われていたのかを、見ていきましょう。

# グリッド軸(Grid axis)チャプターでの例

![](https://storage.googleapis.com/zenn-user-upload/vc70krthn5xnule0zis1tfeygwz0)

以下のソースコードをダウンロードして、手元のブラウザでも確認しながら見ていきましょう。

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-flexbox-axis)

```css
/* その他スタイル省略 */

.container-body {
  /* コンテナーに対する、CSSグリッドのスタイル */
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-row-gap: 1em;

  /* その他のスタイル */
  background-color: #9fbef8;
  margin: 0 auto;
  max-width: 80%;
}

/* 👇 アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  grid-row: 3 / 3;
  grid-column: 3 / 4;
}

.item-2 {
  grid-row: 2 / 3;
  grid-column: 3 / 4;
}

.item-3 {
  grid-row: 2 / 1;
  grid-column: 3 / 4;
}
```

グリッドアイテムのコードに、 `grid-row` と `grid-column` が、各アイテムに使用されているのがわかりますね。

ただ、値のコードを見ただけでは予測がしづらいので、値の書き方の解説をしていきます。

まず、ブラウザでDeveloper Toolsを開き、グリッドラインが視覚的に確認できる状態にします。

その上で、以下の画像を見ていきましょう。

![](https://storage.googleapis.com/zenn-user-upload/g7rvjreujme9bneqosvnk54dsq2t)

まず、この例では、「Item 1」から「Item 3」が上下逆の順で配置されていますね。

Flexboxを使用せず、順番を逆転させることができていますね。

CSSグリッドには、グリッドアイテムの順を反転させるプロパティに `order` があることを一覧で確認はしましたが、上記の例では使用していません。

では、どうやってグリッドアイテムの順を入れ替えているのでしょうか？

`grid-row` と `gird-column` で値を指定するときに、上記の画像にあるように、グリッドラインで

**「row/columnラインのxx番目とoo番目の線の間」**

と、表現をすることで、並ぶ順番ではなく、個々のアイテムの配置を指定しているのです。

### クイズ1

では、上記の画像で「Item 2」を `grid-row` と `gird-column` を、グリッド線/グリッドラインを使って表現してみてください。

考えてみてわかったら、以下の表現と同じになっているか、確認をしましょう。

もしわからなかった場合は、前のチャプターの内容にヒントがあります。

:::message alert
まずは自分で答えを考えて、以下を読み進めましょう。
:::

### 答え1

正解は、以下です。

:::details 「Item 2」の配置の表現、答え
横/行: 「**rowグリッドライン**の**2番目の線と、3番目の線の間**」
縦/列: 「**columnグリッドライン**の**3番目の線と、4番目の線の間**」
:::

スラッシュで「xx番目 / oo番目」と区切って書いていますので、

```css
grid-row: 2 / 3;/* 2番目 / 3番目の間 */
grid-column: 3 / 4;/* 3番目 / 4番目の間 */
```

という書き方になるということです。

### クイズ2

では、今度は、以下の完成見本の配置になるように、 `grid-row` と `gird-column` を、それぞれのグリッドアイテムに付与してみましょう。

![](https://storage.googleapis.com/zenn-user-upload/2vwh2jq1bbqm5wkifzn4j5r2f001)

ソースコードを、上記のリンクよりダウンロードして編集をしてください。

Developer Toolsで、グリッドライン表示にして作業をすると、わかりやすいです。

:::message alert
まずは自分で答えを考えて、以下を読み進めましょう。
:::

### 答え2

正解は、以下です。

:::details クイズ2 答え
```css
/* Item 1: */
grid-row: 1 / 2;
grid-column: 2 / 3;

/* Item 2: */
grid-row: 3 / 4;
grid-column: 1 / 2;

/* Item 3: */
grid-row: 3 / 4;
grid-column: 2 / 3;
```
:::