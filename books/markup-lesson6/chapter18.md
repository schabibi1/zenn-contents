---
title: "grid-template-rows, grid-template-columns"
free: true
---

`grid-template-rows` と `grid-template-columns` の役割は、前半チャプターの「縦構造: グリッド列/Grid column」と「横構造: グリッド行/Grid row」で学習をしましたね。

プロパティ名 | 役割
------------ | -------------
 `grid-template-rows`  | 行(row)の高さを指定するプロパティ
 `grid-template-columns` | 列(column)の横幅の大きさを指定するプロパティ

![](https://storage.googleapis.com/zenn-user-upload/tswoz8u2ox0e9n32ei45cp9iaxpu)

![](https://storage.googleapis.com/zenn-user-upload/b3d0s6dpni2iqw1yjvjz5n76dfod)

前半チャプターの「グリッド軸(Grid axis)」で、FlexboxとCSSグリッドの、一次元と二次元の軸の操作を比較した時の例を、もう一度振り返ってみましょう。

![](https://storage.googleapis.com/zenn-user-upload/tsps5dyjxykml09lhjoeqc53q984)

```css
/* その他スタイル省略 */

.container-body {
  /* コンテナーに対する、CSSグリッドのスタイル */
  display: grid;
  /* ✅ columnとrowの2方向の軸を同時に操作している */
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;

  /* その他省略 */
}

/* アイテムに対する、CSSグリッドのスタイル */
/* 省略 */
```

この構造を、とても見やすくするための機能が、実はChromeとFirefoxの検証ツール(Developer Tools)には搭載されています。

Lilac(ライレック)の教材では、推奨ブラウザのGoogle Chrome Canaryを使用して、お見せします。

以下のソースコードをダウンロードして、以下の解説にある内容を、手元の環境でも確認してみましょう。

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-flexbox-axis)

Developer Toolsをブラウザで開いたら、CSSグリッドの構造を持つHTML要素の横に、 `grid` というラベルが付くので、クリックしてみます。

![](https://storage.googleapis.com/zenn-user-upload/x6ql1tv18os5i645unx6hlv3pdzq)

上記の画像のように、CSSグリッドが有効化されている該当要素には、グリッドラインが付与されて表示されました。

CSSグリッドの構造が、視覚化されましたので、まずグリッド列(Grid column)と、グリッド行(Grid row)がそれぞれいくつあるかを確認します。

- グリッド列(Grid column): 3つ
- グリッド行(Grid row): 3つ

それぞれ3つずつありますね。

では、このチャプターの本題、 `grid-template-rows` と `grid-template-columns` に話を戻します。

値には以下のように記述がありました。

```css
grid-template-columns: 1fr 1fr 1fr;
grid-template-rows: 1fr 1fr 1fr;
```

この `fr` という単位は、CSSグリッド以外では、見かけたことがない単位かもしれません。

`fr` とは、「fraction(分割、分数)」の略で、グリッドコンテナーに合うサイズの大きさのグリッドトラックを配置してくれます。

つまり上記の例で言えば、**3等分にそれぞれ等しいグリッドトラックを、列と行で用意する**という事になります。

列と行の両方を2等分ずつに変更したければ、このようになるということでもあります。

:::message
グリッドアイテムの調整も、以下の反映を見るためには必要になるので、以下のソースコードをダウンロードして、ブラウザでDeveloper Toolsを使いながら確認していきましょう。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-grid-template-rows-columns)

```css
grid-template-columns: 1fr 1fr;
grid-template-rows: 1fr 1fr;
```

![](https://storage.googleapis.com/zenn-user-upload/utgwe5di1rjd31gk6f1eqfwpzt2g)


数値は1以外にも設定でき、例えば、2段目の「Item 1」のある行(row)だけ、2倍の高さにしたい場合は、以下のように書けます。

```css
grid-template-columns: 1fr 1fr;
grid-template-rows: 1fr 2fr;
```

![](https://storage.googleapis.com/zenn-user-upload/20ej2c7h4v5rv8jjiiq8dfp566yc)

「Item 1」と「Item 2」のある列だけを2倍にしたい場合も、以下のように書くだけです。

```css
grid-template-columns: 1fr 2fr;
grid-template-rows: 1fr 2fr;
```

![](https://storage.googleapis.com/zenn-user-upload/xrmddf0qwrskz2y1q4rofr5pcmli)

使用できる値一覧は以下です。

# 値一覧

使用できる値 | 役割
------------ | -------------
 `数値fr` | グリッドコンテナー(外側)を基準にしたグリッドトラック(列&行)を、分割して配置
 `数値px` | pxの数値を基準にしたグリッドトラック(列&行)を、分割して配置
 `数値em` | em(フォントの高さを基準とした単位)を基準にしたグリッドトラック(列&行)を、分割して配置
 `auto` | グリッドトラック中(内側)の、コンテンツのサイズに合わせてグリッドトラックの幅を調整
 `minmax(min数値px, max数値fr/max-content;` | min以上、max以下の寸法の範囲を定義する。`mixmax(min, max)`

これらが主によく使用する値です。

CSSには、pxと%以外にもたくさんの単位がありますが、ここでは、CSSグリッドでよく使用するものを紹介します。

 `minmax(min, max)` 以外に関しては、そういう単位があるのか、と上記の表を見て理解できるかと思うのですが、 `minmax(min, max)` に関しては、マークアップ言語シリーズのLesson 7以降の本で、とても重要になってくる技法なので、解説をします。

 # minmax(min, max)

`minmax(min, max)` とは、実は厳密には単位ではなく、**関数**というものになります。

ここで言う関数は、みなさんが学校で習った数学の関数とは少し異なり、数学的なイメージよりかは、 **機能** になります。

関数に関して詳しく学習をするのは、実はマークアップ言語ではなく、プログラミング言語で学習をしていきますので、関数を作る工程や仕組みに関しては、プログラミング言語で詳しく学習をしていきます。

本書では、関数の作り方や仕組みではなく、使い方について学習をしていきます。

まず、 `minmax(min, max)` の構造は、以下のようになっています。

```css
minmax(最小値の数値, 最大値の数値)
```

それぞれの数値に使用できる単位は、以下です。

最小値 | 最大値
------------ | -------------
px | fr / max-content

`minmax(min, max)` が指定をする行や列は、1つです。

1つのグリッドトラックに対して、 `数値fr` などで指定をしてきたのと、これは同じですね。

つまり、以下の書き方であれば、このような反映になるということです。

```css
grid-template-columns: 1fr 2fr;
grid-template-rows: auto minmax(300px, max-content);
```

![](https://storage.googleapis.com/zenn-user-upload/kv0viiibq82n8erv06d4vsqq5h94)

まず、 `auto` は、rowグリッドライン1から2の線の間にあるグリッドトラックに有効化されます。

「Item 2」のある行という事になりますね。

`auto` は、この「Item 2」というテキスト文字コンテンツのサイズに合わせて、グリッドトラックの幅を調整されています。

そして、rowグリッドライン2から3の線の間にあるグリッドトラックには、 `minmax(300px, max-content)` が適用されます。

コードだけを見て難しい場合は、文章に直すと理解がしやすいので、置き換えてみましょう。

**「行(row)の最小値を300px、最大値をコンテンツいっぱいまでの範囲とする」**

という意味になります。

最小値を `300px` と指定をしているだけあり、「Item 1」の行には、300pxが適用されていることも、上記画像のように、検証ツールで確認することができます。