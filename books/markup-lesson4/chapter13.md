---
title: "練習問題"
---

# Pinterest風webページを作ろう（所要時間の目安: 30分-60分）

# 要件

本書で取り組んだFlexboxと、今までのマークアップ言語シリーズで学習をしたHTMLと、CSSの基本の総復習として、Piterest風のwebページを作りましょう。

以下の完成見本の通りになるよう、取り組んでみましょう。

![](https://storage.googleapis.com/zenn-user-upload/7ilnek6483avzqdnoe3u4wqjarme)

スターターフォルダを、以下よりダウンロードして取り組んでください。

スターターフォルダ名は、「lesson4-pinterest-starter」です。

> [スターターフォルダ](https://github.com/schabibi1/zenn-book-challenges)

以下の項目をヒントに取り組みましょう。

1. Flexboxが有効化されやすいHTML要素の構造を意識して、HTMLコードを構成しましょう
2. ページ上部のパーツからHTML要素を構成していきましょう
3. HTMLの構成が終わったら、CSSでスタイル付与を行いましょう
4. floatは使用せず、Flexboxで対応してください
5. 「Pinterest-ish」箇所と「Login」箇所の文字色と背景色は `#e60023` を使用してください
6. 「weeknight dinner idea」箇所の文字色は、 `#c28b00` を使用してください
7. 「Signup」の背景色は `#efefef` を使用してください
8. フォントはGoogle Fontsを使用しても良いです
9. widthを指定する場合は、pxではなく、%を単位として使用してください
10. heightを指定する場合は、pxではなく、vhを使用してください

### vhの単位

vhとは、表示画面に対しての高さを示す単位です。

異なる横幅や大きさの端末がたくさん出てきたことで、レスポンシブデザインという、画面サイズに合わせて、webサイトの構成をみやすく変化させる技術が必要になりました。

詳しくは、この先のマークアップ言語シリーズの本で取り扱いますが、その際に、ほぼ自動で画面幅のサイズから、指定された高さを算出して表示してくれるのが、vhという単位です。

vは「viewport」、hは「height」です。

viewportとは、「表示範囲」「表示領域」のことです。

何の表示領域かというと、皆さんが見ているパソコン画面の表示画面や、スマホ端末の表示画面、タブレット端末の表示画面のことです。

![](https://storage.googleapis.com/zenn-user-upload/0kxqapcur6hwqt3omlvqq01wml3a)

- [MDN: 相対的な長さの単位、vh](https://developer.mozilla.org/ja/docs/Web/CSS/CSS_Values_and_Units)