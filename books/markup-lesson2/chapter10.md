---
title: "ボックスレイアウト"
free: true
---

HTML要素は、四角い形で存在しています。

この四角い形（領域）のことを **ボックスレイアウト（ボックスモデル）** と言います。

HTML要素の四角い形の構成は、以下の構成をしています。

![box-model](https://storage.googleapis.com/zenn-user-upload/s5rxrw6etasclfdiz21j9zan7ip2)

水色のコンテンツエリアが、視覚的に要素を構成する部分です。

コンテンツエリアは、いわゆる要素の面積なので、数学の面積の計算「縦幅 x 横幅 = 面積」の公式の通り、縦幅（height）と横幅（width）で構成されています。

marginやpaddingは、コンテンツエリアの周りを囲むスペースです。

borderは、名前の通り、囲み枠の線のことです。

marginとpaddingは、厳密に言うと、少し異なるスペースです。

marginは、囲み枠の線よりも外に存在するので、隣り合う他の要素との距離を開けます。

paddingは、囲み枠の線よりも内側に存在するので、囲み枠の線と、コンテンツの距離を開けます。

視覚的に違いを見てみましょう。


* コンテンツエリアのみ、その他ボックスレイアウトなしの場合

```html
<div class="main-content">コンテンツエリア</div>
```

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![box_only_width_height](https://storage.googleapis.com/zenn-user-upload/wlyy77wxvl3u69y6lh1vu7id27b8)

* コンテンツエリア + margin設定の場合

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* その他ボックスレイアウト設定 */
  margin: 100px 200px;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![box_with_margin](https://storage.googleapis.com/zenn-user-upload/rwtzq1bjv9ct2mhe4n0ojdxvognm)

* コンテンツエリア + padding設定の場合

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* その他ボックスレイアウト設定 */
  padding: 100px 200px;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![box_padding](https://storage.googleapis.com/zenn-user-upload/pwgq6t8oa3k229ic1v3bggr5rm8l)

* コンテンツエリア + margin + padding設定の場合

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* その他ボックスレイアウト設定 */
  margin: 100px 200px;
  padding: 100px 200px;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![box_padding_margin](https://storage.googleapis.com/zenn-user-upload/6vvei01ije7m4am7d1j21r4hnszo)

* コンテンツ + border設定の場合

```css
.main-content {
  /* コンテンツ面積の設定 */
  width: 500px;
  height: 250px;

  /* その他ボックスレイアウト設定 */
  border: 5px solid #808080;

  /* 背景色と文字色の設定 */
  background-color: #4b0082;
  color: #ffffff;
}
```

![box_border](https://storage.googleapis.com/zenn-user-upload/mt2nvcljeyxbctbf83z0h9ozrv7t)

paddingとmarginの違いを見るために、値の数値を全く同じにして、プロパティ名だけ変えていますが、囲み枠の線を界に、marginは外のスペース、paddingは内側のスペースを確保することが、視覚的にも確認ができますね。

特にmarginやpaddingは、 **要素間の距離** を調整するための考え方として利用をすると良いでしょう。

要素の配置調整は、ボックスレイアウトの別のCSSプロパティを使用して行います。