---
title: "エクステンションとコマンドパレット"
---

# エクステンションのインストール1: Beautify

VS Codeは、様々なエクステンション\(プラグイン\)が公開されていて、これらをインストールすることでより快適にエディタを使えます。

エクステンションをインストールするには、エディタの左側の四角のアイコンをクリックします。

![installextension](https://storage.googleapis.com/zenn-user-upload/orgc8zkpo2v6bydnq5z2b4vdjl73)

すると、現在インストールされているエクステンションや、オススメのエクステンションが表示されます。

ここでは、便利なエクステンションの一つである「Beautify」をインストールしてみます。

まず、開いている画面の検索ボックスに「Beautify」と入れて検索します。

すると一番上に「Beautify」というエクステンションが表示されます。

「install」をクリックしてインストールします。

![beautify](https://storage.googleapis.com/zenn-user-upload/7d04ebo3lqxcgstijp2e2j7wt64z)

Beautifyを使うと、HTMLファイルやCSSファイルのインデント（段落始めのようなもの）を簡単に揃えることができます。

エクステンションは、インストールしなければエディタが使えないというわけではなく、何もインストールしなくてもVS Codeは使用できますので、必要がない場合はインストールしなくても問題ありません。

必要に応じてエクステンションはインストールしましょう。

# エクステンションのインストール2: Trailing Spaces

![trailing-spaces](https://storage.googleapis.com/zenn-user-upload/l6mbjiaj1907klbj9r1pghcfrldn)

Trailing Spacesは、余白を赤くハイライトして教えてくれるエクステンションです。

余白があると、言語によっては挙動を起こします。

気が付きにくい余白によるエラーのリスクを、あらかじめ、なくすことに役立つエクステンションですので、Trailing Spacesは、ぜひインストールしておきましょう。

# エクステンションのインストール3: Live Share

![live-share](https://storage.googleapis.com/zenn-user-upload/mo6xo6cl7tp1euv32edii19989ns)

Live Shareは、遠隔でGoogle Docsのように、1つのソースコードファイルを、リアルタイムで複数人が編集することができるエクステンションです。

スクリーンシェアをしなくても、ソースコードファイルを共有し、同時にリアルタイムで編集することができるため、リモートワークや、オンラインでのプログラミング学習のサポートで非常によく使用されています。

Live Shareも、インストールしておくと、とても便利なエクステンションの1つです。

使い方は非常に簡単で、以下の画像にあるように、画面左のツールバーにあるLive Shareのアイコンを選択します。

![live-share-how-to](https://storage.googleapis.com/zenn-user-upload/yl292oa0zqiywmsqob8eqvsbpzwb)

その次に、共有する場合は「Share（Read/Write）」もしくは「Share（Read-only）」のいずれかを選択すると、以下のように、Microsoftアカウントでログインをするか、Githubアカウントでログインをするかどうか聞かれます。

（共有してもらう場合は、「Join」をクリックし、共有コードを記入します。）

![](https://storage.googleapis.com/zenn-user-upload/mjovujhpsswirh12rtxsm9458n5z)

アカウントを持っている方を選択し、ログインをしてください。

今回はGithubのログインを例に見ていきます。

ログイン情報を記入して、ログインします。

![](https://storage.googleapis.com/zenn-user-upload/y127t9fb0ofay9naudzovf9nun0b)

以下のように、許可をするよう出てきますので、許可をします。

![](https://storage.googleapis.com/zenn-user-upload/s88pu8ptvciduxz4igi57ffuk3hg)

許可をすると、以下のように共有コードが発行されます。

![](https://storage.googleapis.com/zenn-user-upload/cf6pzvh54c9iick47qzibliicepy)

「Open with VS Code」もしくは、共有コードをコピーして、VS Codeに戻ります。

（「Open with VS Code」の方が簡単です）

「Open with VS Code」をクリックしたら、VS Codeのアプリケーションで、以下のように出てきますので、「open」を選択すると、ソースコードの共有が完了します。

![](https://storage.googleapis.com/zenn-user-upload/qyrpclx7r9c4ijnr0ml1m55m9mli)

Live Shareを使うと、スクリーンシェアをしなくてもブラウザの共有もできたり、コマンドラインの画面も共有できたり（閲覧のみ）するので、スクリーンシェアをしなくても共同作業が可能になります。

# 発展内容: コマンドパレット機能

VS Codeを使って開発するときは、コマンドパレットを上手く使うことで開発速度を上げることが出来ます。

コマンドパレット機能を開いてみましょう。

`command + shift + P` を同時に押すと、次の画像のようになります。

![pallet](https://storage.googleapis.com/zenn-user-upload/580hzkd7y2073fdjicqqwp3ipqeh)

コマンドパレットでは、フォントのサイズを変えたり、エディタのテーマカラーを変えることができたりもするので、試しにフォントサイズを変更してみましょう。

コマンドパレットを開き、「settings」と入力します。

「Preferences: Open Settings\(UI\)」をクリックします。

![settings](https://storage.googleapis.com/zenn-user-upload/6kowyfcaf1mmqmpra07gf2482e61)

「Editor: Font Size」という項目があるので、そこにある数値を「14」に変更して、フォントサイズの変更は完了です。

![fontsize](https://storage.googleapis.com/zenn-user-upload/jwjq8dofthd5eh6jf2ym03q3q0j1)

VS Codeの初期の状態では、コードのフォントがとても小さく、読みづらいので、「Settings（設定）」でフォントサイズを大きくすることで、読みやすくなります。

同じく、「Settings（設定）」の画面で、少しスクロールして画面の下を見ると「Editor: Word Wrap」という項目があります。

これは、長くなったコードを適度な箇所で折り返す設定で、VS Codeでは、何も設定しなければオフになっている機能です。

こちらも「On」に変更しておきましょう。

![wordwrap](https://storage.googleapis.com/zenn-user-upload/6pckdyc7horrwa11fqzvn84cyuuc)

先ほどのLoremの文章が、改行されて画面に全て収まるようになります。

最後にもう1つだけ、コードを書きやすくする設定を行いましょう。

同じく「Settings（設定）」画面にて、「Editor: Tab Size」という項目を、画面上部より探します。

ここの数値を「2」と変更しましょう。

Tabは何を意味するかというと、文章を書くときのことをイメージしてください。

段落を開けるには、新しい段落の開始に、1文字分あけてから文章を書きますね。

Tabとは、文章を書くときの改行を意味するスペースのようなものです。

Tabキーがパソコンにはあり、これを使うことでスペースをあけます。

これを **インデント** と呼びます。 [マークアップ言語シリーズ: Lesson 1 HTMLの基本](https://zenn.dev/arisa_dev/books/markup-lesson1)の本で、もう少し具体的に学びますが、Tabとはインデントのことを意味します。