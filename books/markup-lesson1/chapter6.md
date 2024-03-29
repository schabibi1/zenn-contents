---
title: "画像、コメント導入方法"
free: true
---

この項目では、img要素を使用した画像の埋め込み方の記述と、画像埋め込みに使用する、相対パスと絶対パスの違い、反映結果に影響しないメモ書き、コメントアウトについて学んでいきましょう。

# 画像の埋め込み

HTML要素のimg要素を使うと、画像を埋め込むことができます。

img要素を使った画像の埋め込みの書き方は以下です。

```html
<img src="./picture.png" alt="画像1" />
```

srcという属性に着目をしましょう。

src属性は、「ソース属性」と読み、画像ファイル名や画像ファイルが格納されている場所を書きます。

画像ファイルが格納されている場所のことを、 **相対パス** と言います。

ドットやスラッシュの記号を使って、画像ファイルのある場所を表します。

詳しくは、次の「相対パス、絶対パス」の項目で見ていきましょう。

src属性の他に、alt属性もありますね。

これは、画像ファイルがうまく場所が取得できずに表示されない場合に表示をさせる、テキスト文字です。

ここは日本語でも構いません。

# 相対パス、絶対パス

まずは相対パスについて説明をしていきます。

相対パスは、画像の埋め込みの際に、読み込む画像ファイルの場所を表すものだとわかりました。

この表記には、画像ファイル名とスラッシュやドットの記号を使って、画像ファイルの格納場所を示すことが決まっています。

上記の画像埋め込みの例のコードは、画像ファイルが以下のように格納されている場合の書き方です。

![img_path_simple](https://storage.googleapis.com/zenn-user-upload/lq8rjjhrd819x78hl7ikzh619l42)

testというプロジェクトフォルダにHTMLと並んで画像ファイルが格納されていますね。

でも、常にこの書き方はできません。

画像ファイルが、「images」という名前のフォルダにまとめてあるとすればどうしたら良いのでしょうか？

以下のように、フォルダimagesに入っていることをsrc属性に表記をすると解決します。

```html
<img src="./images/picture.png" alt="画像1" />
```

![image_path_in_folders](https://storage.googleapis.com/zenn-user-upload/ue3hadh0pgilu9snckfpw1hp5ptk)

画像が複数ある場合は、このように1つの画像用フォルダに画像ファイルを格納することで、プロジェクトフォルダ内がスッキリします。

絶対パスについても、相対パスとの違いを踏まえて見ていきましょう。

絶対パスとは、最も簡単な例で言うと、URLが該当します。

インターネット上にある画像をsrc属性に以下のように入れた場合は、絶対パスを使用した書き方と見なせます。

```html
<img src="https://sample-website.com/illustration-image-123456" alt="サンプル1" />
```

しかし、絶対パスを使用する場合は、もし絶対パスで取得をした画像が、引用元サイト上から削除されたり、サイトのURLが変わってしまった場合は、表示されなくなってしまうリスクがあります。

そのため、特別な理由がない限りは相対パスを使用して、画像ファイルを開発プロジェクトフォルダに格納しておくことが推奨されています。

# コメントアウト

コメントアウトとは、反映結果に影響しないメモ書きコメントのことです。

コードを書いていて、大きなプロジェクトになる程コードは長く複雑化します。

長く複雑化したコードを、他のチームメンバーと共同で取り組む際や、しばらく時間が経って自分でメンテナンスをする際のことを考えたときに、全体の構造を把握するところから始まると非効率ですね。

なるべく効率的にコードを書くことが好ましいので、そのためにメモ書きをすることができます。

これは反映結果に影響しないので、何を書いてもユーザーが見ることはありませんが、エンジニアは見ることができてしまいますので、書くコンテンツは短く、簡潔に必要な内容だけにしましょう。

言語によってコメントアウトの書き方は異なります。

HTMLでのコメントアウトの書き方は以下です。

```html
<!-- この文章はコメントアウトされます -->

<!--
  複数行書くときは、
  このように
  書くことが
  できます。
-->
```