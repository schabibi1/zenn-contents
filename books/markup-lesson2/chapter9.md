---
title: "スタイルの検証方法、Developer Tool"
---

CSSの書き方を学習しましたが、スタイルの反映結果を、リアルタイムに視覚的に見て開発を進める方法があります。

**Developer Tool（検証ツール）** を使用する方法です。

スタイルの反映結果を検証しながら開発を進めることから、Developer Tool、検証ツールという名前が付いています。

Developer Toolの使い方を見ていきましょう。

Developer Toolは、ブラウザに付いている機能です。

取り組んでいるプロジェクトのHTMLファイルをブラウザで開いたら、以下の手順で開きます。

1. 右クリック（画面どこでも）/ 画面右上設定ボタン
2. 「Inspect」または「検証ツール」、「検証」をクリック
3. Developer Toolが画面下か、右に出てくる

![devtool](https://storage.googleapis.com/zenn-user-upload/7d9bxcmvb0815zg9r140qciwu3ab)

例の画像はGoogle Chrome Canaryですが、Firefoxでもほぼ同様です。

右クリックができない場合は、画面右上設定ボタンから開けます。

![devtool2](https://storage.googleapis.com/zenn-user-upload/ya5ufchvwjl5a2ra5hs7lkt7r8m3)

Developer Toolの配置は、レスポンシブデザインを学習するまでは、画面下に配置を固定しておきましょう。

![dock_to_bottom](https://storage.googleapis.com/zenn-user-upload/u476y1gm1icdj4r4cjv4d9jexzb6)

理由は、Developer Toolが横に配置されていると、Developer Toolの表示部分は端末画面位表示されているとみなされず、全画面で見たときに、右に大きなスペースができてしまう、コンテンツが崩れるなどの原因になるためです。

- Developer Toolが下に配置の時のコンテンツ表示
![bottom](https://storage.googleapis.com/zenn-user-upload/ryvnvayzpiva6cenwmyqy80t8bf7)

- Developer Toolが右横に配置の時のコンテンツ表示
![side](https://storage.googleapis.com/zenn-user-upload/oihv4b0ah7adddaz2lgpiq7409co)

Developer Tool分の画面の範囲だけ、画面が狭まっていますね。

そのため、レスポンシブデザインを勉強するまでは、常にデスクトップ端末を開発することになるので、Developer Toolを下に配置しておきましょう。

:::message
web開発をする際には、必ずブラウザを **全画面** にしておくようにしましょう。ブラウザウィンドウ分の大きさのみの表示になってしまうため、上記のように正確な反映がされないためです。
:::

Developer Toolの開き方がわかったので、今度は使い方を見ていきましょう。

Developer Toolは、以下の構成をしています。

![dev-tool-html-css](https://storage.googleapis.com/zenn-user-upload/pp4qy5dnj91ayso77xdjb2szap8a)

HTMLの特定の要素をクリックしてみると、該当のHTML要素が、ブラウザ内でハイライトされます。

ハイライトと、選択されたHTML要素のCSSを、青い部分は表示します。

選択したHTML要素のCSSを、「一時的に」Developer Toolでは編集することができます。

試しに、Googleのページを開きましょう。

Googleのページを開いたら、Developer Toolで、どのHTML要素でも良いので、以下の順のように選択し、スタイルを変えてみましょう。

![](https://storage.googleapis.com/zenn-user-upload/wgldm2h6rzyrp3bvzs48c2vv5xeg)

![](https://storage.googleapis.com/zenn-user-upload/hskb9puw884i5lta8f2q55cihiqg)

![](https://storage.googleapis.com/zenn-user-upload/4ngpqwyvxvpatfuas0juy26fmhee)

![](https://storage.googleapis.com/zenn-user-upload/j1uybcxx96lwsirxqvhdmphnrvmg)

![](https://storage.googleapis.com/zenn-user-upload/uoo3311c9lfevq5zflh4lanyebcs)

一時的なスタイルの変更なので、画面をリロード（再読み込み）すると全てリセットされます。

スタイルの編集は、Developer Toolで視覚的に反映を見ながら、上記のように一時的にコードを反映させる作業を行うことで、整ったスタイルの実装ができます。

CSSでスタイルの実装をするには、以下の手順を取るとスムーズに開発ができるでしょう。

1. Developer Toolで一時的に実装したいスタイルを付与
2. 反映を視覚的にリアルタイムでチェック
3. 希望通りの反映になれば、Developer Toolで試したCSSコードをコピー（ `command + C` ）
4. CSSコードのファイルにペースト
5. ブラウザリロードをして、最終チェック