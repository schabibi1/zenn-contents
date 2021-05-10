---
title: "display: grid;"
free: true
---

 `display: grid;` は、前半チャプターの「グリッドコンテナー」の項目でも説明がありましたね。

Flexboxに馴染みのある方であれば、そう難しくはありません。

![](https://storage.googleapis.com/zenn-user-upload/oj9wof0vdi1myn40xw66tkscel9t)

```html
<div class="container">
  <div class="item item-1">1</div>
  <div class="item item-2">2</div>
  <div class="item item-3">3</div>
</div>
```

```css
/* Flexboxの場合 */

.container {
  display: flex;
}
```

CSSグリッドでは、 `flex` という値の代わりに、 `grid` という値を、コンテナー要素に指定するだけで、CSSグリッドが、この範囲に有効化されます。

```css
/* CSSグリッドの場合 */

.container {
  display: grid;
}
```

# 値一覧

使用できる値 | 役割
------------ | -------------
 `grid` | CSSグリッドを適用する