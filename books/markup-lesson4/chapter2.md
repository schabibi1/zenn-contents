---
title: "ベンダープレフィックス（vendor prefixes）"
free: true
---

さて、Flexboxが普及したため、ほとんどの最新バージョンのブラウザであれば問題はないと上記でお伝えしました。

しかし、注意が必要なブラウザとバージョンがあるのも事実です。

このような場合、どう対応すると良いのでしょうか？

そんな時は、 **ベンダープレフィックス（vendor prefixes）** を使って対処します。

ベンダープレフィックスとは、 **CSSスタイルの比較的新しい技法のサポートを補うもの** です。

全てとは言い切れませんが、ブラウザで完全対応する前のCSSスタイルでも、サポートを補うことができます。

ベンダープレフィックスの書き方は以下です。

```css
セレクタ名 {
  /* ベンダープレフィックス */
  display: -webkit-box;
  display: -ms-flexbox;

  /* 通常の設定記述 */
  display: flex;
}
```

ベンダープレフィックスは、ブラウザごとに設定を書きます。

以下は、各ブラウザのベンダープレフィックスの書き方の一覧です。

ブラウザ名 | ベンダープレフィックスの記述
------------ | -------------
Chrome, Safari, 新しいバージョンのOpera, ほとんどのiOSブラウザ | -webkit-
Firefox | -moz-
古いバージョンのOpera | -o-
Internet Explorer(IE), Microsoft Edge | -ms-

ただし、今回学習するFlexboxもそうですが、スタイルによって、ベンダープレフィックスは、若干書き方が異なるので、以下の **Autoprefixer CSS online** というサービスを利用すると良いでしょう。

実装しようとしているCSSスタイルを書き込めば、その場でベンダープレフィックスの書き方を表示してくれる、便利なサービスです。

> [Autoprefixer CSS online](https://autoprefixer.github.io/)

![autoprefixer](https://storage.googleapis.com/zenn-user-upload/918r5yg6jl1t9919g9vsc2pid9dj)