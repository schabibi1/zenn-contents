---
title: "使用頻度の高いHTML要素"
free: true
---

ここからは使用頻度の高いHTML要素を学習していきましょう。

HTML要素は、たくさん種類が用意されていますので、一度に暗記するのではなく、以下の一覧をチャレンジに取り組む際に見ながら取り組むと、次第に覚えることができます。

まずはどんなものがあるのかを、ここではざっくりと見ていきましょう。

タグ名 | 役割
------------ | -------------
div | 範囲の指定。どのタグにしたら良いか迷った場合にも使用可能。初期設定は縦並び。
h1, h2, h3, h4, h5, h6 | ヘッダータグ。タイトル文字の表示。（h1がもっとも大きいタイトル表示で、h6が最小のタイトル表示。）
p | パラグラフタグ。段落を表現する。テキスト文字をコンテンツにもつ
a | アンカータグ。URLなどのリンク先に飛ばすことができる
ul, li | unlistedタグとリストタグ。順不同の箇条書きリスト。
ol, li | ordered listタグとリストタグ。順序つき箇条書きリスト。
span | スパンタグ。範囲の指定。初期設定で横並びに並列する。
br | 改行を表現する。閉じタグを持たない。
img | 画像の埋め込み。
table | 表。
tbody | 表のメインボディ。
tr | 表の行。
form | フォームの外枠。
input | フォームの記入欄。
textarea | フォームの複数行記入欄。
select | セレクトボックス。
button | ボタン要素。
label | ラベル名。フォームの項目名によく使用する。
script | スクリプトの読み込み。JavaScriptファイルを読み込む際に使用する。
style | CSSコードをHTMLファイルに混合して書く範囲。非推奨だが、知識として知っておくと良い。

全てのHTML要素はここでは紹介しませんが、以上が使用頻度の高い要素です。

まずは使用頻度の高いものから使えるように、役割を把握していきましょう。

そのほかのHTML要素やタグの種類については、検索して調べるとたくさん出てきますので、必要に応じて確認をしてください。

参考ソースの項目でもお話ししますが、 **MDN** というソースを参考にすると良いでしょう。

# ブロック要素インライン要素

HTMLには、様々な種類の要素（タグ）が用意されていることがわかりましたね。

それぞれコンテンツによって使い分けるということも学習しました。

ここでは、次のレッスンから学習をするCSSスタイルを整える際に役に立つ、それぞれのHTML要素にすでに初期設定でついているスタイルの一部を学びます。

CSSは、HTML要素のスタイルを整え、よりモダンなwebサイトへと仕上げる役割を果たします。

基本的に、CSS、つまりスタイルがまだ適応されていないHTMLファイルだけのプロジェクトは、ブラウザで読み込んで見ても、全て縦並び、左寄せの構成になってしまいます。

しかし、要素の並び方、つまり縦並びか横並びかについては、一部のHTML要素では、初期設定として、あらかじめこちらが何もしていなくてもついているスタイルの設定があるのです。

多くのHTML要素には、初期設定として縦並びになるスタイル設定があります。

そのため、HTMLファイルのみのプロジェクトをブラウザで開いても、縦並びの要素がほとんどというのは、このためです。

その中で、例外の一部のHTML要素は、初期設定で横並びになるようスタイルの設定があるものもあります。

初期設定で縦並びになるよう設定されているHTML要素を **ブロック要素** 、反対に横並びに並列するよう設定がされているものは **インライン要素** と呼ばれます。

プログラミングには、頻繁に英語のキーワードが出てきたり、英語で検索をする方が情報が豊富だったりするのですが、「ブロック」と「インライン」も英語の意味を知るとわかりやすいです。

英単語 | 日本語訳
------------ | -------------
block | 縦並び
inline | 並列

どの要素がインラインで、ブロックで...と全て覚えようとすると大変なので、よく使用する要素の中で、インライン要素のものを知っておくと便利です。

理由としては、インライン要素の方が数が少なく、大半のHTML要素はブロック要素だからです。

以下の要素が、よく使用するHTML要素の中でも、インライン要素のものです。

暗記するのではなく、テキストのこの箇所を見ると載っているところまで知っておくだけで、初めはOKです。

これらの要素の使用回数が増えるにつれて、自然に覚えるので、暗記に頼らず、書く回数を増やして定着させていきましょう。

インライン要素 | タグ名読み方
------------ | -------------
a | アンカータグ
br | ブレークタグ
button | ボタンタグ
img | イメージタグ
input | インプットタグ
label | ラベルタグ
script | スクリプトタグ
select | セレクトタグ
span | スパンタグ
svg | SVGタグ
textarea | テキストエリアタグ

ブラウザでの反映も見ておきましょう。

```html
<h1>ブロック要素</h1>
<div>ブロック要素</div>
<p>ブロック要素</p>

<span>インライン要素</span>
<span>インライン要素</span>

<label>インライン要素</label>
<label>インライン要素</label>

<button>インライン要素</button>
<button>インライン要素</button>
```

![block_and_inline](https://storage.googleapis.com/zenn-user-upload/1cshjc3xhffoxjakyq41o8tiymz0)

# 属性: class属性, id属性

この章では「属性」の中でも、特にclass属性とid属性について学びます。

ここで、みなさんがwebページを1ページ開発するとしましょう。

もちろん、HTML要素を使って構成を指定浮くわけですが、ここで問題が出てきます。

2つあるヘッダー要素h1のうち、1つ目のh1は黒い文字色で表示をしたいのですが、2つ目のh1は緑の文字色で表示をしたい場合、どうやって1つ目のh1と2つ目のh1要素の区別をつければ良いのでしょうか？

単純に以下のように書くと、どちらの文字も同じ文字色になってしまうのです。

```html
<h1>1つ目のh1要素：文字色は黒</h1>
<h1>2つ目のh1要素：文字色は緑</h1>
```

![class_name](https://storage.googleapis.com/zenn-user-upload/tey9pucuxcv6daqhabgmc848gbeo)

どちらもh1要素で出力はしたいのですが、文字色は区別をつけたい場合、 **class属性** を使うと解決します。

class属性とは、同じ種類のHTML要素に、それぞれユニークな名前をつけて、同じ要素でも区別をつけるためのものです。

* h1要素のgreenという名前の要素
* h1要素のblackという名前の要素

と、このようにニックネームをつけることで、同じ種類の要素であっても、区別や指定がしやすくなります。

class属性を追加、付与するには、以下の書き方をします。

```html
<h1 class="black">1つ目のh1要素：文字色は黒</h1>
<h1 class="green">2つ目のh1要素：文字色は緑</h1>
```

こうすることで、2つのh1要素は、それぞれ異なるh1要素として認識できるので、それぞれ異なるスタイルの付与ができるようになります。

推奨はされていませんが、HTMLコードにCSSコードを混ぜて書く方法を用いると、実際にこの例の文字色を変えることも可能です。

文字色を変えるためには、以下のようにstyle属性を追加し、CSSの文字色を変えるコードを書きます。

```html
<h1 class="black" style="color: black;">1つ目のh1要素：文字色は黒</h1>
<h1 class="green" style="color: green;">2つ目のh1要素：文字色は緑</h1>
```

![class_name_with_style](https://storage.googleapis.com/zenn-user-upload/wcwhilyh061b1vmct5fnxsyz4ld4)

ただし、スタイル（CSS）は、別のCSS用のファイルを用意して、そこに全て書くことが推奨されていますので、上記のようなstyle属性を使う書き方は、通常行わないようにしましょう。

さて、class属性については理解が深まりましたが、id属性についてはまだですね。

id属性は、class属性の性質を比較をすると違いがわかりやすいです。

class属性は、同じclass名を何度でも繰り返し使うことが可能です。

反対にid属性は、一度使ったid名は、それ以上は使用ができません。

具体例を挙げると、同じスタイル（文字色、フォントの大きさなど）を、複数の要素に適応したいときに、同じclass名を付与すると、同じスタイルをいくつもの要素に一度に付与することができます。

id属性にはそれはできないということになります。

そのため、基本的にはclass属性を使用して書くことが推奨されています。