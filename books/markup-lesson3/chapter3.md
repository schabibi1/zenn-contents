---
title: "練習問題"
free: true
---

# floatの練習をしてみよう！（所要時間の目安: 10分〜20分）

floatの基本構文や、値のそれぞれの役割、floatが要素を浮動させる状態のイメージができたところで、実際に手を動かしながら、簡単なfloatの練習をしてみましょう。

まず、以下のHTMLの構成でHTMLファイルを作成します。

HTMLファイルやCSSファイルの作成の仕方、検証ツールでの反映確認方法や開発手順については、こちらの本にあります。

- [「マークアップ言語シリーズ: Lesson 1 HTMLの基本」](https://zenn.dev/arisa_dev/books/markup-lesson1/viewer/chapter1)の、[「HTMLとは？」](https://zenn.dev/arisa_dev/books/markup-lesson1/viewer/chapter1)
- [「マークアップ言語シリーズ: Lesson 2 CSSの基本」](https://zenn.dev/arisa_dev/books/markup-lesson2)の[「スタイルの検証方法、Developer Tool」](https://zenn.dev/arisa_dev/books/markup-lesson2/viewer/chapter9)

```html
<!-- body内記述 -->
<div class="wrapper">
  <div class="left-body">Left Body</div>
  <div class="middle-body">Middle Body</div>
  <div class="right-body">Right Body</div>
</div>
```

次に、以下のコードをコピーしてCSSファイルも作成し、HTMLファイルに読み込みましょう。

```css
@charset "UTF-8";

* {
  margin: 0;
  padding: 0;
}

.wrapper {
  max-width: 80%;
  border: 5px solid #818181;
  margin: 30px auto;
  text-align: center;
}

.left-body {
  background-color: #add8e6;
  color: #ffffff;
  font-weight: 600;
  padding: 50px;
  height: 25px;
}

.middle-body {
  background-color: #ffffff;
  color: #000000;
  font-weight: 600;
  padding: 50px;
  height: 25px;
}

.right-body {
  background-color: #8f69b6;
  color: #ffffff;
  font-weight: 600;
  padding: 50px;
  height: 25px;
}
```

Left Body、Middle Body、Right Bodyの3つの要素があり、floatがない状態ではブロック要素は並列をしませんので、以下のような表示です。

![float_disabled](https://storage.googleapis.com/zenn-user-upload/c5fgycfg5ozjpcp1qpztqzs224if)

上記のHTML、CSSコードのスターターファイルから、floatの設定を書き加え、次の3つの要件を満たしましょう。

# 要件

以下の3つの要素を、配置方向の指示にしたがって並列させてください。

1. Left Bodyを左に配置
2. Middle Bodyを中央に配置
3. Right Bodyを右に配置

完成見本では、このようになります。

![float_on](https://storage.googleapis.com/zenn-user-upload/su0w60cgx14gpda2g0ffk758xw66)

うまく浮動を利用して、要素を並列させることができたでしょうか？

反映結果と正解は以下です。

:::message
検証をする際には、必ずブラウザで反映結果を確認しましょう。
Developer Toolを使用すると、視覚的にスタイルを確認しながら開発ができます。
:::

:::message alert
完成見本は、上記の完成見本添付画像を見本にしてください。
以下の回答コードによる反映結果、「Result」項目を見ると、埋め込み部分の画面幅の問題で正確な反映ではありません。
:::

# 取り組むときのコツ

上記の目安時間をもとに、自分で解く時間を決めて取り掛かり、それ以上経過した場合は、答えを見て確認します。

答えを見てもわからない箇所があれば、10分〜20分ほど時間を決めて調べ、それ以上かかるようであれば、以下のソースに質問を投稿してみましょう。

- [terateil（テラテイル）](https://teratail.com/)
- [stack overflow](https://stackoverflow.com/)

terateilは、日本語のみ、stack overflowは、日本語と英語で質問が可能です。

これらの質問投稿サービスは、既に同じ質問をしている人の回答がされていたり、似たケースの回答が見つかることもあります。

エンジニアがボランティアで回答をしています。

情報としては正しいものがほとんどで、間違っている情報は、ほかのエンジニアが修正をしていることが多く、情報としては信頼性が高いです。

これらの技術質問サービスで質問をすることは、わかりやすく状況を伝えることに加え、自分がわからない内容の把握にもつながりますので、同じ質問をしている人がいなければ、積極的に活用していきましょう。

今後、エンジニアになりたい人は、複数人で開発を行う**チーム開発**という形態で開発をする機会もあります。

その際に、先輩エンジニアやチームメンバーに、**自分が何がわからないのかを、簡潔に適切な表現で伝える練習**をすることにもつながりますので、勉強中の時から活用しておきましょう。

# 答え

:::message alert
まずは答えを見ずに取り組みましょう。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/52pwvsLr/1/)

:::message
上達のコツ:
上記埋め込みコードの「Edit in JSFiddle」をクリックすると、JSFiddleのページで編集ができます。
floatの仕組みを踏まえて、少しコードに手を加えて、アレンジをしてみるのも練習になります。
:::
