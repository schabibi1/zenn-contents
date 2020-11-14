---
title: "order"
---

`order` の役割については、アイテム用に用意された、CSSグリッドプロパティ一覧のチャプターで、簡単に確認をしましたね。

プロパティ名 | 役割
------------ | -------------
 `order` | グリッドアイテムの並び順を指定するプロパティ

`order` も、Flexboxに同じ役割の、同じ名前のプロパティがありました。

CSSグリッドの `order` も、Flexboxの `order` と同様に、グリッドアイテムに使用することができます。

以下のように、グリッドアイテムを配置してみたいと思います。

![](https://storage.googleapis.com/zenn-user-upload/kjj5kg6i3y21wlbfycp6huwhmkgn)

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson6-css-grid-order」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-css-grid-order)

```css
/* コンテナーに対する、CSSグリッドのスタイル省略 */

/* アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  order: 2;/* 👈 */
}

.item-2 {
  order: 1;/* 👈 */
}

.item-3 {
  order: 3;/* 👈 */
}
```

# 値一覧

使用できる値 | 役割
------------ | -------------
数値(整数値, integer) | グリッドアイテムの順番指定をする
inherit(グローバル値) | グリッドコンテナーを元にした値をグリッドアイテムに付与する
initial(グローバル値) | 初期値を付与する
unset(グローバル値) | 指定をしない

# 注意

1つだけ、 `order` プロパティを付与する時に、気をつけたいことがあります。

それは、 **`order` プロパティが無効になる場合がある** ということです。

例えば、先ほどの例では、、 `order: 数値;` としているだけで、 `grid-column` や `grid-row` でグリッドラインとグリッド列と行を基準にした、グリッドアイテムの配置の指定をしていません。

これらを、 `order` と一緒にスタイル付与するとどうなるでしょうか？

```css
/* コンテナーに対する、CSSグリッドのスタイル省略 */

/* アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  grid-row: 3 / 3;
  grid-column: 3 / 4;
  order: 2;
}

.item-2 {
  grid-row: 2 / 3;
  grid-column: 3 / 4;
  order: 1;
}

.item-3 {
  grid-row: 2 / 1;
  grid-column: 3 / 4;
  order: 3;
}
```

CSSは、下に書いてあるコードほど優先して読み込む習性があるので、それを利用して、 `order` をそれぞれ下に書いてみます。

![](https://storage.googleapis.com/zenn-user-upload/qrdnx8ybc71u4dcbwg9dppuslvub)

グリッドアイテムだけの順序崩れだけでなく、 `grid-template-rows` で指定をした行の数も、3つに増えてしまい、書いた通りのスタイルを実現できませんでしたね。

このように、 **`order` を使用するときは、グリッドアイテムの配置のプロパティである `grid-row` や `grid-column` と一緒に使用しないようにする** か、**`order` を使用せず、`grid-row` や `grid-column` だけの使用** にするようにしましょう。

どちらもグリッドアイテムの配置になるので、用途に応じて、グリッドラインに基づいたアイテム配置が良いのか、順序の指定でアイテム配置を行うのが良いのか、使い分けて使用しましょう。