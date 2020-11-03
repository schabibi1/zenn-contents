---
title: "文字検索と置換"
---

# 文字検索

文字検索を使ってみましょう。

まずは、テスト用のフォルダ「vscode\_tutorial」を作り、そこに「test.txt」というテキストファイルを作成します。

ファイルが出来たら、以下の文章を3回コピー&ペーストしてください。

```markup
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
```

この文章は、プログラマがよく文章を仮に埋めたい時に使う"Lorem Ipsum"という文章です。

準備が完了したらファイル内で `command + F` と押します。

検索ボックスが立ち上がります。

検索ボックスが立ち上がったら"Lorem"と入れてEnterキーを押して検索してみましょう。

すると画像のように"Lorem"の部分が枠で囲まれて表示されます。

![search](https://storage.googleapis.com/zenn-user-upload/7da26k0nejbl31r793amaruu7lzw)

# 文字の置換

文字の置換を使ってみましょう。

先程のファイルを開いたまま `Alt + command + F` を押しましょう。

Altキーが見当たらなければ、文字検索の `command + F` に、以下の「>」をクリックすると、文字置換が開きます。

![](https://storage.googleapis.com/zenn-user-upload/x9w0lhwfyaehh751ofzuo44h96ju)

![](https://storage.googleapis.com/zenn-user-upload/kueodi4k2zdt5sv1kizh8s3q6ieh)

検索用のウィンドウが、置換用のウィンドウに切り替わります。

![replace](https://storage.googleapis.com/zenn-user-upload/vttvbnyx15wjcpbj6tyj3utiy06e)

Loremの文字を、試しに"Test"と変更してみます。

Loremと書いた検索ボックスの下に、”Test”と書いてEnterキーを押すと、文字が置換されます。

Loremを3つ全て置換するには、Enterキーを3回押します。

![replaceall](https://storage.googleapis.com/zenn-user-upload/xu9yzsaczcafswjtxaqjmhinodxz)

検索や置換は、選択した範囲だけに適用することができるため、大文字と小文字を区別するかどうかを選んだり、1つずつ置換するか、一度に全ての箇所を置換するかを選べます。
