---
title: "要素の配置：中央"
---

要素の配置調整は、paddingやmarginではなく、別のCSSプロパティを使って設定することがわかりましたね。

要素の配置調整には、

* position
* top
* right
* bottom
* left

このプロパティを主に組み合わせて使用することが多いです。

例を見てみましょう。

先ほどのボックスレイアウトの基本構造の例の要素を、画面中央に移動させてみましょう。

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* その他ボックスレイアウト、配置調整 */
  position: relative;
  top: 200px;
  left: 400px;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![position](https://storage.googleapis.com/zenn-user-upload/tojv8ky0kptl8b35u8mwi2cq66jk)

positionプロパティは、以下4つの値を持っています。

値 | 役割
------------ | -------------
relative | 元いた位置から〜〜px移動させる
absolute | 一番近い親要素の位置に対し、絶対的に配置
fixed | 要素の固定（スクロールしても付いてくるヘッダーなど）
static | 初期値 

何もしなければ初期値にはstaticが付いています。

absoluteが少し慣れが必要ですが、relativeから慣れていくと良いでしょう。

このことを踏まえると、上記の例では、「元いた位置の上から200px、左から400px移動させる」と設定していることがわかります。

上から詰め物をして移動させるのがtop、左に詰め物をして移動させるのがleftと言うことになりますね。