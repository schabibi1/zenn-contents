---
title: "justify-content"
free: true
---

# コンテナに使用するFlexboxのプロパティ

## justify-content: 水平方向の位置

`justify-content` は、「水平方向の位置を指定するプロパティ」です。

`justify-content` で用意されている値を使って、それぞれの反映結果を実例で見ながら、各値の違いを学んでいきましょう。

## justify-content: flex-start;

先ほどの `flex-wrap` で見た、ミュージック ストリーミングアプリの実例を使います。

:::message
チャプター9で使用したソースコードを使用して、以下と同様に変更を加えて、反映結果を確認してみましょう。
:::

`flex-start` を値に、 `justify-content` を実装してみます。

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;/* flex-startを値に指定 */
}
```

![flex-start](https://storage.googleapis.com/zenn-user-upload/7bi5u0q84dvudqbfn94z6pkdji6g)

反映に変化はありませんね。

これは、 `flex-start` の値が、デフォルトの値だからです。

デフォルトは左揃えで並ぶので、 `justify-content` を指定しない場合は、自動で `flex-start` の値が、付与されているということになります。

この実例は、marginやpaddingで、ある程度整っている部分もありますが、よく見ると、コンテンツも若干左寄りですね。

## justify-content: flex-end;

`flex-end` は、アイテム要素を右に寄せます。

先ほどの実例の値を、 `flex-end` に変えて見てみましょう。

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-end;/* flex-endを値に指定 */
}
```

![flex-end](https://storage.googleapis.com/zenn-user-upload/1ozix5iif1mmjejyny4j6ed3i2bq)

アイテム要素が、全体的に右に寄りましたね。

## justify-content: center;

`center` は、アイテムを左右中央揃えで配置します。

先ほどの実例の値を、 `center` に変えて見てみましょう。

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;/* centerを値に指定 */
}
```

![center](https://storage.googleapis.com/zenn-user-upload/xofnz7s8e8hblp2t2ylf2viarnyh)

アイテム要素が、中央配置に変化しました。

## justify-content: space-between;

`space-between` は、両端のアイテムを余白を空けずに配置し、他の要素は均等に間隔をあけて配置します。

先ほどの実例の値を、 `space-between` に変えて見てみましょう。

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;/* space-betweenを値に指定 */
}
```

![space-between](https://storage.googleapis.com/zenn-user-upload/uorzrspka0d7w3wl11ldor6x6dwb)

アイテム要素が、均等にスペースをあけて配置されていますね。

この実例自体には、全体の左右にmarginが入っているので、左右が空いている様に見えますが、dev toolで確認をすると、アイテム自体にあらかじめついているmargin以外、両端のアイテムの画面端にはスペースがないことが確認できます。

画面下の要素では、 `space-between` の効果が顕著です。

![margin-right-left](https://storage.googleapis.com/zenn-user-upload/o4oveqt45p3vsc9nqs4dyew2b85x)

## justify-content: space-around;

`space-around` は、両端のアイテムも含めて、均等な間隔をあけて配置します。

先ほどの実例の値を、 `space-around` に変えて見てみましょう。

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;/* space-aroundを値に指定 */
}
```

![space-around](https://storage.googleapis.com/zenn-user-upload/c7814obe76pz1bczh6r6pit02j7i)

この実例自体には、全体の左右にmarginが入っているので、左右のスペースについて変化がない様に見えますが、dev toolで確認をすると、両端のアイテムの画面端にも、さらにスペースがあることが確認できます。

こちらも、画面下の要素では、特に `space-around` の効果が顕著です。

![space-around-margin-gap](https://storage.googleapis.com/zenn-user-upload/aqmpfy7c3vmfqa8b9l6zvvhxe38v)

`justify-content` の、値の一覧は以下です。

justify-content 値 | 役割
------------ | -------------
flex-start | デフォルト。左揃えで配置。
flex-end | 右揃えで配置。
center | 中央揃えで配置。
space-between | 両端アイテムの画面端の余白はなし。他の要素は均等に間隔をあけて配置
space-around | 両端アイテムの画面端の余白あり。他の要素も均等に間隔をあけて配置