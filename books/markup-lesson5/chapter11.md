---
title: "コンポーネントを意識して組み立てよう"
free: true
---

練習問題1と2では、コンポーネントに切り分け、共通するコンポーネントに、共通するclass名の付与をする練習をしました。

しかし、実際にゼロから自分でHTML要素を構成し、CSSのスタイルを付与することは練習していませんね。

ここでは次の練習問題に取り組む前に、その練習をしていきます。

# コンポーネントの組み立て方

コンポーネントとは、**ページの1つ1つのパーツ要素のこと**だと、練習問題1で触れましたね。

コンポーネントの役割と、共通するコンポーネントに共通するclass名の命名を行うことは、練習問題1と2で練習をしたので、ここでは、コンポーネントを組み立てることを学習していきます。

メルカリの新着アイテムカード風のものを、コンポーネントを組み立てて作成してみましょう。

完成見本はこちらです。

![mercari-sample](https://storage.googleapis.com/zenn-user-upload/jqadu1160ejoc9vy9kjn6g8y5up0)

実践の場でも、まずは完成見本がwebデザイナーによって用意されているか、自分で用意をしてから、コードに落とし込んでいきますので、その想定をして、今回は取り組んでいきます。

この場合は、完成見本が既にあり、手渡された場合ということになります。

慣れれば、練習問題1で行った作業は、HTMLを書く時に考えていけば良いのですが、慣れるためにも、ここでもコンポーネントに視覚的に切り分ける作業から行っていきましょう。

以下のリンクより、上記のメルカリの新着アイテムカード風完成見本画像をダウンロードしてください。

もしくは、上記の画像上で右クリックに「Save images as...」/ 「画像を名前をつけて保存する」を選択してください。

> [完成見本画像ダウンロード](https://github.com/schabibi1/zenn-book-challenges/blob/main/lesson5-oocss-mercari/mercari-sample.png)

練習問題1と同様の方法で、コンポーネントをそれぞれ色分けします。

色分けをすると、以下のようになります。

:::message
上達のコツ:
以下の例を見る前に、まずは自分でコンポーネントの切り分けに取り組むと勉強になります。
:::

![mercari-components](https://storage.googleapis.com/zenn-user-upload/tzy9hu9xuxmp5hdox5qh9wn3rxbe)

このように、コンポーネントをあらかじめ切り分けることができていれば、HTMLで構成する際にも簡単ですね。

では、HTMLで上記のコンポーネントの区切りを参考に、コードを書いていきましょう。

コツは以下です。

1. 上にある構成から順に下へ取り組む
2. 左にある要素から右の要素の順に取り組む
3. 「人気のカテゴリー」とカテゴリータグが終わったら、まずは1つのカードの構成を組み立てる

まずは「人気のカテゴリー」とカテゴリータグの箇所から取り組みます。

![mercari-header](https://storage.googleapis.com/zenn-user-upload/ynlpyvoryv4c9iwdr4fdv5ctn077)

コンポーネントを意識してHTML要素を構成する時には、**コンテナー → コンテンツの順**で取り組むと、コードが書きやすいです。

上記のコンポーネントに切り分けた例で言うと、

1. 水色のコンテナー
2. オレンジ色のコンテンツ
3. 黄緑色のコンテナー
4. 薄ピンク色のコンテンツ

という順で構成すると良いということになります。

このような構成で組み立てることができます。

:::message
上達のコツ:
以下の例を見る前に、まずは自分でHTML要素で構成してみると勉強になります。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/v8kqyz6L/1/)

ここでは、まだスタイルを付与しないので、**コンテナーとコンテンツを意識**することを優先して構成しましょう。

構造とスキンの分離は、スタイル付与をする際に行うと良いです。

:::message
コンテナーとコンテンツの分離と、構成とスキンの分離を一度に意識すると、複雑化しやすいので、まずはコンテナーとコンテンツの分離を意識しましょう。
:::

「人気のカテゴリー」とカテゴリー部分のHTML構成が完成しました。

では、次は商品カード部分です。

5つカードがありますが、まずは1つ商品カードを構成することに集中します。

![mercari-card](https://storage.googleapis.com/zenn-user-upload/drtjjootc1jje1d9pijxo247qk0q)

先ほどと同様に、上記のコンポーネントに色分けをした見本をみながら、まずは、一番左のジャケット商品カードのHTML要素を構成しましょう。

構成していく順番としては、

1. 紫色のコンテナー
2. 黄色のコンテナー
3. 緑色のコンテンツ
4. 赤色のコンテンツ
5. ピンク色のコンテンツ

と、なります。

このような構成で組み立てることができます。

:::message
上達のコツ:
以下の例を見る前に、まずは自分でHTML要素で構成してみると勉強になります。
:::

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson5-oocss-mercari-cards」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="utf-8" />
    <title>mercari風 新着アイテムカード</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header class="popular-header">
      <h1 class="popular-title">人気のカテゴリー</h1>
      <ul class="category">
        <li class="category-item">レディース</li>
        <li class="category-item">メンズ</li>
        <li class="category-item">家電・スマホ・カメラ</li>
        <li class="category-item">おもちゃ・ホビー・グッズ</li>
      </ul>
    </header>

    <main class="wrapper">
      <a href="#" class="card-wrapper">
        <section class="card-image">
          <img src="./images/toa-heftiba-ua9ReZlzcIE-unsplash.jpg" alt="item-image" />
          <div class="price price-dark-gray">￥22,000</div>
        </section>
        <section class="item-title">
          <p class="item-name">
            【新作】秋物ジャケット レディース カジュアル
          </p>
        </section>
      </a>
    </main>
  </body>
</html>
```

スタイルの付与はまだなので、反映結果は、このようになります。

![mericari-card-no-style](https://storage.googleapis.com/zenn-user-upload/3n4od1gmsz7u9z7yojqgae2xhuay)

これから残り4つのカードのコンテンツのHTMLを増やしたいところですが、まだこのHTML要素の構成で100%問題ないかどうかの確信は持てません。

ここまでで、ひとまずCSSでスタイルの付与を行います。