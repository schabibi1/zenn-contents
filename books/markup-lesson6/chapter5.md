---
title: "グリッドコンテナー"
free: true
---

# グリッドコンテナー

グリッドコンテナーは、Flexboxにもコンテナーがあることを学習しましたので、そこまで難しくはないですね。

チャプター4にも、Flexboxのテキストで学習をした以下の図がありましたね。

![](https://storage.googleapis.com/zenn-user-upload/380pa6mt7gflcrslebu55dpamzcp)

Flexboxでは、親要素であるコンテナーに、Flexboxのスタイルを以下のように指定しました。

![](https://storage.googleapis.com/zenn-user-upload/oj9wof0vdi1myn40xw66tkscel9t)

```html
<div class="container">
  <div class="item item-1">1</div>
  <div class="item item-2">2</div>
  <div class="item item-3">3</div>
</div>
```

```css
.container {
  display: flex;
}
```

CSSグリッドでは、 `flex` という値の代わりに、 `grid` という値を、コンテナー要素に指定します。

```css
.container {
  display: grid;
}
```

**CSSグリッドを有効化する設定**、というイメージをするとわかりやすいかもしれません。