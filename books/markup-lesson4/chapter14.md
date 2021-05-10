---
title: "答え"
free: true
---

:::message alert
まずは答えを見ずに取り組みましょう。
:::

pinterest風webページ全てを、完成見本の通り実装できたでしょうか？

- Flexboxが有効化されやすいHTMLの構造
- Flexboxのコンテナーとアイテムの構造の理解
- 本書で学習したFlexboxレイアウト

上記がしっかりと理解できていれば、この課題はそこまで難しくはないかと思います。

高さをvhにし、横幅の単位を%にすることで、画面幅を変えてもある程度整った見た目になることが確認できます。

ブラウザの画面幅を伸ばしたり、縮めたりして確認してみましょう。

横幅と高さが、全体のバランスをもとに算出されて、スタイルのバランスが崩れにくいことがわかるかと思います。

:::message
モバイルやタブレットで見た際に、それぞれの画像が大きく見やすいようにするには、配置を変更するレスポンシブデザインを実装しますので、vhや%だけでは調整できません
:::

pxだと、数値を指定してしまうので、このような検証をした際には、スタイルのバランスが画面幅によって崩れやすくなります。

また、異なる端末幅への対応が、個々に必要になってしまい、コードが長くなってしまいます。

![](https://storage.googleapis.com/zenn-user-upload/h4yhyqf8b7hry1p8gghaf177mgbm)

![](https://storage.googleapis.com/zenn-user-upload/e2biixtchb6yfotlvjvrinvitpw0)

![](https://storage.googleapis.com/zenn-user-upload/7noqtxeudr6el25oh514qk8hl9uf)

模範解答は以下です。

[答えのソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson4-pinterest-answer)