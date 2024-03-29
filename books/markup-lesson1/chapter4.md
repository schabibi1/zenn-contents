---
title: "HTMLの基本的な構造"
free: true
---

HTML要素の階層の構造と、親子要素の構造、インデントについて学んだので、これらを意識しながら、まずはHTMLの基本的な構造から見ていきましょう。

# 宣言文

HTMLだけではなく、CSSにも宣言文はあります。
ここで言う宣言文は、一言で表すと、 **ファイル上に書く言語の種類、バージョンを伝えるもの** です。

すでにファイル名についている拡張子で十分なのでは？と、思われた方もいるかもしれませんね。

言語の種類のみであれば、拡張子ですでに定義していますが、言語にはバージョンというものがあり、「HTMLのバージョン〜〜を使って書きます」と宣言する必要があります。

みなさんが今学習しているHTMLのバージョンは5です。
そのため、「HTML5を書いています」と宣言する必要があるのです。

宣言文は、言語によって異なります。

HTMLの場合は、 **DOCTYPE宣言** というものを使用します。
CSSの宣言文は、次のLesson 2、「CSSの基本」で学習します。

DOCTYPE宣言は以下のように書きます。

```html
<!DOCTYPE html>
```

HTMLファイルの1行目にまず最初にこの1行を書くだけでOKです。
とても簡単ですね。

宣言文は、これからHTMLコードを書くための下準備と言える作業です。

以下の `<html></html>` や `<head></head>` も、DOCTYPE宣言と同様に、HTMLを書くための下準備に該当します。

コンテンツを書き始める前に、まずはこれら下準備の用意を先に済ませてしまうことで、HTMLの基本構造が整った状態でコンテンツの構造だけに集中してコードを書き進めることができます。

新しくHTMLファイルを用意したら、まずはこれら下準備を先に済ませてしまいましょう。

# <html></html>

DOCTYPE宣言を書き終えたら、次に以下のようにheadタグを用意しましょう。

head要素は、webページ内の全ての要素を囲み、「ルート要素」と呼ばれます。

DOCTYPE宣言には、例外として閉じタグがないものでしたが、htmlタグには閉じタグが必要です。

```html
<!DOCTYPE html>
<html>

</html>
```

# <head></head>

html要素の次は、head要素を用意します。

head要素は、主な役割を一言で言うと **「CSSファイルやJavaScriptファイルなどの外部ファイルを読み込む要素」** です。

そのほかの役割としては、Googleなどの検索エンジンで検索された時に表示される、ページタイトルや、サイトの概要、SNSで共有された際に、綺麗に画像付きでページリンクを表示させるための設定（OGP設定）など、SEO向上の設定をする役割も持ちます。

SEOとは、Search Engine Optimizationの略で、インターネット検索結果で自分のサイトを上位表示させたり、より多くのユーザーの目に留まるよう見せるための設定です。

SEOの設定をしておくことで、webサイトへの流入を増やしたり、それによってwebサイトによる売り上げが向上したします。

head要素内には、こうした上記のコンテンツが入ります。

このようなコンテンツのことを、 **メタ情報** と呼びます。

メタ情報を含めた場合のhead要素の書き方の一例は以下です。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>サイトタイトル</title>
    <link rel="stylesheet" href="styles.css" />
    <meta name="description" content="サイトの概要をここに書くと、検索エンジンで検索結果表示に表示されます。" />
  </head>
</html>
```

title要素を使うことで、サイトをブラウザで開いた際のウィンドウタブ上部に、「サイトタイトル」と上記の例では表示されます。

開発するwebサイト名に、状況に応じて変えると良いでしょう。

link要素は、例外として閉じタグを持ちません。

閉じタグを持たない要素の書き方ですが、山カッコ閉じの直前に、スペースとスラッシュを入れることが推奨されます。
こうすることで、視覚的にもわかりやすいですね。

link要素内では、外部ファイル、つまりここではCSSファイルを読み込んでいます。

rel属性は、CSSファイルを読み込むことを意味する「stylesheet」があります。

metaタグは、 `name="description"` とあるタイプのものは、サイト概要を設定することができます。

contentの中に概要を書いて使用します。

もう1つ、 `<meta charset="utf-8">` と言う記述のmetaタグがありますね。

これは、ブラウザに正しく文字化けなどをさせずにコンテンツを表示させるためのものです。

`utf-8` は、全ての数字、記号、アルファベットなどの文字をサポートする、Unicodeの一種です。

# <body></body>

head要素までの下準備の設定は、実は今の所、どれもブラウザに表示されるものではありません。

ここからは、いよいよ画像やテキスト文字など、ブラウザに表示をさせたいコンテンツを書いていきます。

ブラウザに表示をさせるコンテンツを書いて構成していくには、「ここからはコンテンツです」と明確にします。

body要素で囲むことで、「この範囲はブラウザに表示させるコンテンツです」と明確にすることができます。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>サイトタイトル</title>
    <link rel="stylesheet" href="styles.css" />
    <meta name="description" content="サイトの概要をここに書くと、検索エンジンで検索結果表示に表示されます。" />
  </head>
  <body>
    <div>この範囲がブラウザ表示されるコンテンツ</div>
  </body>
</html>
```

ここまでくれば、あともう一息でページコンテンツを構成するHTML要素を並べて構成するだけですね。

ただし、ページコンテンツを構成していくには、ある程度のページコンテンツ構成があった方が、それぞれのページパーツを把握しやすくなるので、ページコンテンツ構造を組み立ててからコンテンツの中身を埋めていきましょう。

# セマンティクスタグ

HTMLファイルを用意した後の、ページコンテンツを書くための下準備は整いました。

でも、闇雲にページ全体のコンテンツ構成をどうするか考えずにコンテンツの中身だけを羅列させると、どんなページ構成を作りたいのかが、開発をしている途中でわからなくなってしまいます。

しばらく時間が経ってから、メンテナンスでファイルを開いて編集することを想定して、どれだけ時間が経っていても瞬時にページ構成とコンテンツを把握できるよう、今の段階から意識をしてコードを書くと読みやすいコードになります。

webページの基本的なコンテンツの構造はだいたい決まっていて、以下の構造が一般的です。

![semantics](https://storage.googleapis.com/zenn-user-upload/h08eivjcbr95g7f3v5f0dlldsdpb)

ブログなどのサイトは、まさにこの構成ですね。

このコンテンツ構成がない状態の、まっさらな状態を想像すると、コンテンツ構成がある方は、中のコンテンツさえ埋めていけば良いので、コンテンツの構造がある方がわかりやすいですね。

このコンテンツの構造、枠組みをHTML要素でも用意をすることができ、 **セマンティクスタグ** を使うことで実現できます。

セマンティクスタグには、以下の種類があります。

* header
* nav
* main
* aside
* footer

それぞれの役割は、以下の通りです。

セマンティクスタグの種類 | 役割
------------ | -------------
header | 上記画像のヘッダー部分を構成
nav | サイト内の他のページへのリンクや、そのページ内のセクションへのリンクを貼ることが多い
main | 上記画像のメインボディ部分を構成
aside | 上記画像のサイドバー部分を構成
footer | 上記画像のフッター部分を構成

これを実際にHTML要素として、今までの下準備と合わせて書くと以下のようになります。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>サイトタイトル</title>
    <link rel="stylesheet" href="styles.css" />
    <meta name="description" content="サイトの概要をここに書くと、検索エンジンで検索結果表示に表示されます。" />
  </head>
  <body>
    <header>
      <div>ヘッダー部分。サイト名やロゴを入れることが多い</div>
    </header>

    <nav>
      <ul>
        <li>TOP</li>
        <li>ABOUT</li>
        <li>CONTACT</li>
      </ul>
    </nav>

    <main>
      <div>メインボディコンテンツ部分。</div>
    </main>

    <aside>
      <div>サイドバー部分</div>
    </aside>

    <footer>
      <div>フッター部分。コピーライトなどを入れることが多い</div>
      <div>©︎ Lilac</div>
    </footer>
  </body>
</html>
```

HTMLコードだけを見ても、ページコンテンツの構造が視覚的にわかりますね。

ここまでくれば、あとはコンテンツの中身をそれぞれ埋めていくだけです。