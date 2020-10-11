---
title: "FlexboxのCSS設定の基本"
free: true
---

Flexboxの基本的なCSS記述内容は、以下です。

チャプター5のHTML構造を踏まえた書き方です。

```css
.container-body {
  display: flex;
}
```

:::message
HTMLを含め、以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/f8epdro6/2/)

Flexboxを指定したHTML要素は、親要素のコンテナーですね。

必ず **親要素のコンテナー** にFlexboxのスタイルを指定します。

実際の反映を見ると、3つのアイテムが並列しています。

![flex-container-style](https://storage.googleapis.com/zenn-user-upload/5qksjzs2v3ykl21jl7idk8qyuu78)

上記の反映は、見やすくするために、その他のスタイルを加えていますが、その他のスタイルを含めたコードを見ても、コンテナーにFlexboxのスタイル指定をしていることがわかりますね。

```html
<ul class="container-body"><!-- コンテナー -->
  <li>Item 1</li><!-- アイテム -->
  <li>Item 2</li><!-- アイテム -->
  <li>Item 3</li><!-- アイテム -->
</ul>
```

```css
* {
  margin: 0;
  padding: 0;
  color: #ffffff;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: 700;
}

.container-body {
  /* コンテナーにFlexboxのスタイルを指定 */
  display: flex;

  /* その他のスタイル */
  background-color: #9fbef8;
  margin: 0 auto;
  max-width: 80%;
}

ul, li {
  /* その他のスタイル */
  list-style-type: none;
  border-radius: 3px;
  background-color: #fdeebc;
  padding: 40px;
  margin: 0 20px;
}
```
