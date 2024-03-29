---
title: "練習問題1"
free: true
---

# 共通するパーツ要素の切り分けをしよう！（所要時間の目安: 3分〜5分）

今回は、簡単なゲームの選択画面を使用します。

先に完成見本を見てみましょう。

![game_select_screen](https://storage.googleapis.com/zenn-user-upload/ynuvbnp01gyi70vvcitgdb0uz6zt)

構造がとてもよく似たパーツが多い構成ですね。

むしろ、コンテンツの文面や画像ファイルが違うだけで、特に用意されている選択肢のバトルに関しては、HTMLやCSSで構成される要素の構造は同じです。

このように、オブジェクト指向CSS（OOCSS）を意識した構成を構築するには、まずは開発物の完成イメージから、共通する構造のパーツ要素を、予め認識しておくことで、再利用しやすいclass名を付与することができます。

では、上記の完成見本を、大まかにパーツごとに区切ってみましょう。

# 要件

まずは以下の答えを見ずに、上記の完成見本画像をダウンロードし、パーツ要素を色分けした四角などで囲んで区切りましょう。

ダウンロードは、画像にカーソルをかざして、右クリックをすると手軽にできます。

Macユーザーは、デスクトップ上で画像を開く際に、デフォルトでPreviewというアプリケーションで画像を開くことができますので、Previewの編集機能を使用して見ると、色分けがしやすいです。

その際に、以下のことを守ってパーツ要素を区切ってください。

1. 共通する見た目（スタイル）のパーツ要素は、同じ色の四角で囲む
2. SELECT THE BATTLEのタイトルは、今回は四角で囲まなくてOK（共通するパーツ要素がないため）

上記に取り組んだ後に、以下にある答えを確認しながら続きを読み進めていきましょう。

# 取り組むときのコツ

上記の目安時間をもとに、自分で解く時間を決めて取り掛かり、それ以上経過した場合は、答えを見て確認します。

今回は、とても簡単なものなので、必要ないかもしれませんが、もしも答えを見てもわからない箇所があれば、10分〜20分ほど時間を決めて調べ、それ以上かかるようであれば、以下のソースに質問を投稿してみましょう。

- [terateil（テラテイル）](https://teratail.com/)
- [stack overflow](https://stackoverflow.com/)