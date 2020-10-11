---
title: "CSSファイルの作成方法と、HTMLファイルへの読み込み"
free: true
---

ファイルの拡張子を `.css` として、一般的には `styles.css` の名前で保存することが多いです。

HTMLファイルと同じフォルダに保存をすることで、スタイルを適応してくれます。

CSSファイルをHTMLファイルに適応するには、 **HTMLファイル内のhead要素内に、外部ファイルとして読み込み** ます。

[マークアップ言語シリーズ: Lesson 1 HTMLの基本](https://zenn.dev/arisa_dev/books/markup-lesson1)の本に、実例がありましたね。

link要素を使って、以下のようにCSSファイルを読み込みます。

```html
  <head>
    <link rel="stylesheet" href="styles.css" />
  </head>
```

注意したいのが、ファイル名のスペルミスです。

1文字でもスペルミスがあると、CSSファイルが読み込まれないので、CSSファイルの読み込み箇所と、CSSファイルの名前を統一させているか確認をするようにしましょう。