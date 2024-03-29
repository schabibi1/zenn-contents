---
title: "HTML要素の並列"
free: true
---

HTML要素を並列させるには、主に2つのスタイルがあります。

1つはこのレッスンで学ぶ **float** です。

もう1つは、次の[マークアップ言語シリーズ: Lesson 4 並列、Flexbox](https://zenn.dev/arisa_dev/books/markup-lesson4)で学習をする **Flexbox** です。

floatの方が歴史は長く、Flexboxは新しい並列の技法です。

難易度はfloatの方が低く、Flexboxの方が少し高くなりますが、柔軟性はFlexboxの方があります。

まずは、並列の基本であるfloatから習得していきましょう。

# floatとは？

floatとは、HTML要素を並列させるための技法の1つです。

名前の意味合いに、「浮く」という意味がありますが、その名前の通り、HTML要素を浮かせることで並列をさせます。

HTML要素が浮いている状態というのは、言葉だけでは想像しにくいと思うので、webページを横面から見ていることをイメージして、以下の図を見てみましょう。

![float_system](https://storage.googleapis.com/zenn-user-upload/qrpkys1h5uqygi2syygt24345go3)

floatの設定が付いている要素は、floatの設定がない要素に比べて、前面に出て浮いていますね。

floatによって浮いた要素は、左右や上下に他の要素がいないので、その分移動ができるということになります。

この「浮いている状態」ということをfloatを使う時には意識をすると、うまく並列しない時にも疑問が解決しやすいので、今後意識していくと良いでしょう。