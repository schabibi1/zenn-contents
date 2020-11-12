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

```css
.container-body {
  /* コンテナーに対する、CSSグリッドのスタイル */
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  grid-row-gap: 1em;

  /* その他のスタイル省略 */
}

/* アイテムに対する、CSSグリッドのスタイル */
.item-1 {
  order: 2;
}

.item-2 {
  order: 1;
}

.item-3 {
  order: 3;
}
```

# 値一覧

使用できる値 | 役割
------------ | -------------
数値 | 順番指定をする
inherit | 
initial | 
unset | 