---
title: "justify-self"
---

`justify-self` の役割については、アイテム用に用意された、CSSグリッドプロパティ一覧のチャプターで、簡単に確認をしましたね。

プロパティ名 | 役割
------------ | -------------
 `justify-self` | 各グリッドトラック内の横方向の位置を指定するプロパティ

例えば、今まで見てきた3つの要素のサンプルで、「Item 1」だけ左寄せにしたり、右寄せにしたり、配置に変更を加えたいとしましょう。

これまでのグリッドアイテムに対するプロパティでは、個別のグリッドアイテムに対して、個別の配置操作をするものはありませんでしたが、 `justify-self` では、それが可能です。

実際に、以下の反映結果になるようにするには、 `justify-self` で以下のように書くことができます。

![](https://storage.googleapis.com/zenn-user-upload/0zg8csrbrm6ggv0a2aeursovas6m)

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson6-justify-self」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-justify-self)

```css
/* コンテナーに対する、CSSグリッドのスタイル省略 */

/* アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  grid-row: 1 / 2;
  grid-column: 1 / 2;
  justify-self: start;/* 👈 */
}

.item-2 {
  grid-row: 1 / 2;
  grid-column: 2 / 3;
}

.item-3 {
  grid-row: 1 / 2;
  grid-column: 3 / 4;
}
```

# 値一覧（使用頻度の高いもの）

使用できる値 | 役割 | 付与できるケースのカテゴリ
------------ | ------------- | -------------
`normal` | レイアウトに応じて、 `start` や `stretch` のようにも振る舞う | 基本キーワード
`stretch` | 横幅が `auto` であるグリッドアイテムは軸の領域いっぱいにグリッドを広げる | 基本キーワード
`center` | 中央寄せ | 位置による配置
`start` | 左寄せ | 位置による配置
`end` | 右寄せ | 位置による配置