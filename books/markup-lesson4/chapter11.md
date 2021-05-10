---
title: "align-items"
free: true
---

# コンテナに使用するFlexboxのプロパティ

## align-items: 垂直方向の位置

`align-items` は、「要素の垂直方向の位置を指定するプロパティ」です。

先ほど学習した `justify-content` が水平方向の位置指定なのに対し、 `align-items` は「垂直方向の位置指定」ですね。

`align-items` で用意されている値を使って、それぞれの反映結果を実例で見ながら、各値の違いを学んでいきましょう。

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson4-align-items」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

## align-items: stretch;

**stretch** は、アイテムの上下を埋めるように配置します。

何も指定をしない限り、 **stretch** はデフォルトなので、初期値として付与されます。

```html
<div class="wrapper">
  <img src="./img/annie-spratt-V705bwrTnQI-unsplash.jpg" alt="christmas_decoration" />
  <img src="./img/kris-atomic-FiQcUMgD3Jk-unsplash.jpg" alt="red_branch" />
  <img src="./img/hannah-pemberton-bXi4eg4jyuU-unsplash.jpg" alt="gluwein" />
  <img src="./img/food-photographer-jennifer-pallian-_Skvg1Izyxc-unsplash.jpg" alt="stollen" />
</div>
```

```css
/* ...その他スタイルは割愛 */

.wrapper {
  max-width: 90%;
  margin: 0 auto;
  display: flex;
  align-items: stretch;/* stretchを値に指定 */
}
```

![stretch](https://storage.googleapis.com/zenn-user-upload/aabwpdayumlv4r64nuod3gnob3mf)

横長の画像が、縦にストレッチ（stretch）されて縦長に伸びていますね。

## align-items: flex-start;

**flex-start** は、アイテムを上揃えで配置します。

```css
/* ...その他スタイルは割愛 */

.wrapper {
  max-width: 90%;
  margin: 0 auto;
  display: flex;
  align-items: flex-start;/* flex-startを値に指定 */
}
```

![flex-start](https://storage.googleapis.com/zenn-user-upload/c867ebbpaihg5bgfopxy381h1lce)

stretchの時とは違い、横長の画像が縦に伸びることはなくなりました。

画像上部を基準に配置されていますね。

## align-items: flex-end;

**flex-end** は、アイテムを下揃えで配置します。

```css
/* ...その他スタイルは割愛 */

.wrapper {
  max-width: 90%;
  margin: 0 auto;
  display: flex;
  align-items: flex-end;/* flex-endを値に指定 */
}
```

![align-items-flex-end](https://storage.googleapis.com/zenn-user-upload/viezrvyzbi8fgjyurk2v2yfvr2qc)

こちらもflex-startと同様に、横長の画像が縦に引き伸ばされず、配置されています。

**flex-end** の場合は、画像下部を基準に配置されます。

## align-items: center;

**center** は、アイテムを上下中央揃えで配置します。

```css
/* ...その他スタイルは割愛 */

.wrapper {
  max-width: 90%;
  margin: 0 auto;
  display: flex;
  align-items: center;/* centerを値に指定 */
}
```

![align-items-center](https://storage.googleapis.com/zenn-user-upload/59wei5gnf3lfu6hh40aud917e45n)

今度は画像の上部や下部を基準にするのではなく、中央を基準に配置されていますね。

`align-items` の、値の一覧は以下です。

align-items 値 | 役割
------------ | -------------
stretch | デフォルト。アイテム上下余白を埋めて配置
flex-start | 上揃えで配置。
flex-end | 下揃えで配置。
center | 上下中央揃えで配置。
