---
title: "order"
free: true
---

# アイテムに使用できるFlexboxのプロパティ

## order: アイテムの並び順を指定

* **order: アイテムの順番指定の数値;** 

 `order` を指定することで、HTML要素の記述順にかかわらず、特定の要素の並び順を指定することが可能になります。

先ほどの `align-items` の例で使用した実例に少し手を加えて `order` を適用した場合の反映結果を見ていきましょう。

先ほどの例では、画像の順番が以下だったのに対し、

![flex-start](https://storage.googleapis.com/zenn-user-upload/2zvl0s2qgab4q4owr0u7gpotglkx)

 `order` で順番を、以下のようにバラバラに指定することができます。

![order](https://storage.googleapis.com/zenn-user-upload/m50iz9j3l1zfppk0qfccp3sgo097)

:::message
チャプター12で使用したソースコードを使用して、以下と同様に変更を加えて、反映結果を確認してみましょう。
:::

ソースコードは以下です。

```html
<div class="wrapper">
  <img class="ornament" src="./img/annie-spratt-V705bwrTnQI-unsplash.jpg" alt="christmas_decoration" />
  <img class="red-branch" src="./img/kris-atomic-FiQcUMgD3Jk-unsplash.jpg" alt="red_branch" />
  <img class="gluwein" src="./img/hannah-pemberton-bXi4eg4jyuU-unsplash.jpg" alt="gluwein" />
  <img class="stollen" src="./img/food-photographer-jennifer-pallian-_Skvg1Izyxc-unsplash.jpg" alt="stollen" />
</div>
```

```css
.ornament {
  order: 3;
}

.red-branch {
  order: 4;
}

.gluwein {
  order: 1;
}

.stollen {
  order: 2;
}
```