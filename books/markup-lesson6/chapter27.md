---
title: "align-self"
---

`align-self` の役割については、アイテム用に用意された、CSSグリッドプロパティ一覧のチャプターで、簡単に確認をしましたね。

プロパティ名 | 役割
------------ | -------------
 `align-self` | 各グリッドトラック内の縦方向の位置を指定するプロパティ

前のチャプターの `justify-self` が、横方向の位置を指定するプロパティに対して、本チャプターの `align-self` は**縦方向の位置を指定**するプロパティですね。

例えば、「Item 1」を以下のように配置したい場合には、 `align-self` が活用できます。

![](https://storage.googleapis.com/zenn-user-upload/4u93vljg1g38h9qmhgxakyf4gad7)

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson6-align-self」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-align-self)

```css
/* コンテナーに対する、CSSグリッドのスタイル省略 */

/* アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  order: 2;
  align-self: end;/* 👈 */
}

.item-2 {
  order: 1;
}

.item-3 {
  order: 3;
}
```

# 値一覧（使用頻度の高いもの）

使用できる値 | 役割 | 付与できるケースのカテゴリ
------------ | ------------- | -------------
`normal` | レイアウトに応じて、 `start` や `stretch` のようにも振る舞う | 基本キーワード
`stretch` | 縦幅が `auto` であるグリッドアイテムは軸の領域いっぱいにグリッドを広げる | 基本キーワード
`center` | 中央寄せ | 位置による配置
`start` | 上寄せ | 位置による配置
`end` | 下寄せ | 位置による配置