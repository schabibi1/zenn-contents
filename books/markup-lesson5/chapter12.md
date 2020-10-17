---
title: "コンポーネントにスタイルを付与しよう"
---

チャプター12では、メルカリの新着アイテムカード風のプロジェクトで、「人気のカテゴリー」とカテゴリー部分、そして商品カードの1枚目をHTMLで構成しました。

この段階では、複雑化を避けるために、コンテナーとコンテンツの分離のみを意識してHTML要素でコンポーネントを構成しています。

ここまでできている段階で、ひとまずCSSでスタイルの付与を行います。

:::message alert
残りのカード全てを、今の段階でHTML要素で構成した場合、HTMLの構成が100%確認が持てないままコードが長くなり、修正が発生した場合、工程が増えてしまいます。
:::

# コンポーネントのスタイル付与

「人気のカテゴリー」とカテゴリー部分までを、まずはスタイル付与してみます。

このようなスタイル付与ができます。

:::message
上達のコツ:
以下の例を見る前に、まずは自分でHTML要素で構成してみると勉強になります。
:::

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson5-oocss-mercari-header-css」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

```css
@charset "UTF-8";

* {
  padding: 0;
  margin: 0;
  font-family: Arial, 游ゴシック体, YuGothic, メイリオ, Meiryo, sans-serif;
  color: #000000;
}

/* コンテナー */
.popular-header {
  margin: 50px auto;
}

/* コンテンツ */
.popular-title {
  text-align: center;
  padding: 20px 0;
}

/* コンテナー */
.category {
  display: flex;
  list-style: none;
  justify-content: center;
}

/* コンテンツ */
.category-item {
  display: inline-block;
  padding: 5px 15px;
  margin: 0 10px;
  background-color: rgb(239, 239, 239);
  border-radius: 15px;
  font-size: 15px;
  font-weight: 600;
}
```

![mercari-header-styled](https://storage.googleapis.com/zenn-user-upload/n39okla4i0nx7ibwi1u019vr3k65)

では、ここで構造とスキンの分離を意識していきます。

CSSのセレクタは、それぞれコンテナーとコンテンツで分けることができていますが、構造とスキンに関してはまだですね。

ここでのコツは、まず**スキンから見ていくこと**です。

スキンが含められている箇所を探すと、以下の箇所が見つかります。

```css
/* 上記省略 */

/* コンテンツ */
.category-item {
  display: inline-block;
  padding: 5px 15px;
  margin: 0 10px;

  /* 以下はスキン */
  background-color: rgb(239, 239, 239);
  border-radius: 15px;
  font-size: 15px;
  font-weight: 600;
}
```

カテゴリー1つ1つのい背景色やそのほか見た目に関するスタイルが入っています。

もし、特定のカテゴリーだけ背景色やフォントの太さなどを変更したい場合は、このスキンのスタイル内容を変えたセレクタと、差し替えれば良いということになります。

そのことを踏まえると、これはスキンの新しいセレクタとして、以下のように用意するのが良さそうですね。

```css
/* 上記省略 */

/* コンテンツ */
.category-item {
  display: inline-block;
  padding: 5px 15px;
  margin: 0 10px;
}

/* スキン & コンテンツ */
.category-item-gray {
  background-color: rgb(239, 239, 239);
  border-radius: 15px;
  font-size: 15px;
  font-weight: 600;
}
```

スキン用のセレクタを分けましたので、HTMLにも、変更を加えます。

```html
<!-- 上記省略 -->
<header class="popular-header">
  <h1 class="popular-title">人気のカテゴリー</h1>
  <ul class="category">
    <!-- .category-item-gray 追加 -->
    <li class="category-item category-item-gray">レディース</li>
    <li class="category-item category-item-gray">メンズ</li>
    <li class="category-item category-item-gray">家電・スマホ・カメラ</li>
    <li class="category-item category-item-gray">おもちゃ・ホビー・グッズ</li>
  </ul>
</header>
```

スキンに関しては、分離をすることができましたので、最終的な仕上げとして、構造の分離を行います。

CSSファイルに戻りましょう。

ここで構造に該当するセレクタを探します。

```css
/* 構造 & コンテナー */
.popular-header {
  margin: 50px auto;
}

/* 構造 & コンテンツ */
.popular-title {
  text-align: center;
  padding: 20px 0;
}

/* 構造 & コンテナー */
.category {
  display: flex;
  list-style: none;
  justify-content: center;
}

/* 構造 & コンテンツ */
.category-item {
  display: inline-block;
  padding: 5px 15px;
  margin: 0 10px;
}

/* スキン & コンテンツ */
.category-item-gray {
  background-color: rgb(239, 239, 239);
  border-radius: 15px;
  font-size: 15px;
  font-weight: 600;
}
```

実は、スキンに先に着目することによって、そのほかの構造の分離も、既に完了していることに気がつきましたか？

このような手順で行うと、HTMLのコンポーネントの構造も100%確信が持てますし、CSSのスタイルも、オブジェクト指向CSS（OOCSS）を意識した構成になっている状態で、次の構成に進むことができます。

# OOCSSのコンポーネント構成とスタイル付与の方法まとめ

1. 完成見本をコンポーネントに分ける（慣れればHTMLを構成しながらこの工程はできます）
2. 切り分けたコンポーネントを元に、HTML要素を構成する（コンテナーとコンテンツの分離だけを意識）
3. 複数ある共通コンテンツ要素は、ひとまず1つ用意（例: 先頭のカードのみ）
4. CSSでスタイル付与をする（1つのコンテナーをまずは行う。例: ヘッダー）
5. スキンのセレクタを分離する
6. HTMLにスキンのセレクタを付与
7. コンテナーとコンテンツ、構造とスキンの分離が完了
8. 1〜7のステップを繰り返す