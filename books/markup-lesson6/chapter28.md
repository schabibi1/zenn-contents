---
title: "練習問題"
free: true
---

# Pinterest風webページを、CSSグリッドに書き換えよう（所要時間の目安: 10分-20分）

# 要件

本書で取り組んだCSSグリッドと、今までのマークアップ言語シリーズで学習をしたHTMLと、CSSの基本の総復習として、[「マークアップ言語シリーズ: Lesson 4 並列、Flexbox」](https://zenn.dev/arisa_dev/books/markup-lesson4)の練習問題で取り組んだ、Piterestの課題を、FlexboxからCSSグリッドに一部書き換えてみましょう。

以下の完成見本の通りになるように、取り組んでみましょう。

![](https://storage.googleapis.com/zenn-user-upload/unzjc7x5j196gds8azna78p3elen)

:::message
Flexboxの時に実装したものより、若干画像の幅が異なりますが、それはFlexboxで実装した時は、列の幅の指定がなく、今回はfrの単位で指定をするためです。
:::

スターターフォルダを、以下よりダウンロードして取り組んでください。

スターターフォルダ名は、「lesson6-pinterest-starter」です。

> [スターターフォルダ](https://github.com/schabibi1/zenn-book-challenges)

以下の項目をヒントに取り組みましょう。

1. 全体の構造から、Flexboxのままの方が良いコンポーネントと、CSSグリッドに書き替えた方が良いコンポーネントの目星をつけます
2. Flexboxの方が記述が簡潔に済むものは、Flexboxで残してください
3. CSSグリッドレイアウトの方が、記述が簡潔に済むものは、CSSグリッドに書き換えましょう
4. 画像コンポーネント部分は、CSSグリッドを適用するのであれば、グリッド列の単位はfrで調整してください
5. なるべくpaddingやmarginではなく、余白はガターで対処してください