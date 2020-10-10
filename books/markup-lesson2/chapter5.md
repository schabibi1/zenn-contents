---
title: "CSSの構文: プロパティと値"
free: true
---

# プロパティと値

セレクタの役割と、セレクタ名の書き方を知ることができましたね。

セレクタは、単独では使用することができず、 **プロパティ** と **値** も一緒に書く必要があります。

プロパティとは、英語の5W1Hで言う「what（何を）」に該当します。

値は、5W1Hの「how（どうするか）」です。

そうすると、セレクタと合わせて5W1Hの意味合いをつなげると「どこに、何をどうするか」と言うことを、セレクタ、プロパティ、値の3つで表現していることがわかります。

セレクタと合わせて、プロパティと値は以下のように書きます。

```css
セレクタ名 {
  プロパティ: 値;
}

.main-body {
  color: #ffffff;
}
```

![property_value](https://storage.googleapis.com/zenn-user-upload/vk4g0aenoe7jd285zkqmafqyk8ih)

プロパティと値は、CSSですでに用意をされているものを使用します。

非常にたくさんありますので、まずは使用頻度の高いものから使い慣れていくと良いでしょう。

プロパティ | 意味
------------ | -------------
color | 文字色指定
font-size | 文字サイズ指定
font-weight | 文字の太さ指定
background-color | 背景色指定
background-image | 背景画像指定
display | 主に要素の配置指定（並列や縦並びなど）/ 要素の表示と非表示
font-family | テキスト文字のスタイル指定
text-align | テキスト要素の配置指定
align-items | 要素の配置指定
width | 要素の横幅指定
height | 要素の高さ指定
border | 囲み枠の太さ、色、線の種類の指定
border-radius | 囲み線の角の丸み指定
z-index | 要素の重なりの順番指定

MDNにも一覧がありますので、参考にしてみましょう。

> [MDN CSS カスケーディングスタイルシート](https://developer.mozilla.org/ja/docs/Web/CSS/Reference)