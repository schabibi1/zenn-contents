---
title: "flex-direction"
free: true
---

# コンテナに使用するFlexboxのプロパティ

## flex-direction: アイテムの方向を指定

Flexコンテナー内のアイテムの、方向を指定します。

アイテムの方向とは、「左から右へ並列」などの方向を意味します。

デフォルトは、先ほど上記で見た例のように、左から右に並列をします。

逆に、右から左へ並列させたい場合の反映結果は以下です。

![flex-direction-row-reverse](https://storage.googleapis.com/zenn-user-upload/hev8acd6n320mos8gnyryphw68js)

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/7fp0snby/2/)

`flex-direction` を使った、上記のレイアウトの書き方は以下です。

```html
<ul class="container-body"><!-- コンテナー -->
  <li>Item 1</li><!-- アイテム -->
  <li>Item 2</li><!-- アイテム -->
  <li>Item 3</li><!-- アイテム -->
</ul>
```

```css
.container-body {
  /* コンテナーにFlexboxのスタイルを指定 */
  display: flex;
  flex-direction: row-reverse;

  /* 以下省略: その他のスタイル */
}
```

`row-reverse` と言う値を指定することによって、上記の図のように、右から左へ要素を並べ替えて並列させることができます。

flex-direction 値 | 役割
------------ | -------------
row | デフォルト。左から右へ要素を並列させる
row-reverse | 右から左へ要素を並べ替えて並列させる

実は、この `flex-direction` 、左右の並び替えだけでなく、上下の並び替えもできます。

上下はどういう時に使うかと言うと、LINEなどのチャットアプリで、最新のチャットのやりとりを上に、古いものほど下に表示する時に使うことができます。

本来であれば、スタイルを何もしないデフォルトの状態であれば反対の表示なのですが、それでは新しいやりとりが下に表示されてしまい、ユーザーにとって不便です。

### flex-directionデフォルト値の表示

![chat-default-order](https://storage.googleapis.com/zenn-user-upload/8cad90k2lv6v9hgt6zd2q37fsoq8)

### flex-directionで上下を反転させた表示

![column-reverse](https://storage.googleapis.com/zenn-user-upload/f74pklfovtjk8jg9zbtqbut91hst)

上記の実例のように、上下の要素並べ替えをflex-directionで実装するには、以下のように書きます。

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson4-flex-direction-chat」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

```html
<ul class="chat-wrapper">
  <li class="chat-content bottom-end">
    <img src="./img/agnieszka-kowalczyk-c0VRNWVEjOA-unsplash.jpg" alt="Truper" />
    <div class="chat-body">
      <div class="name-and-time">
        <p>Eric</p>
        <p>Thu, 19:05</p>
      </div>
      <p>Are you free on this Saturday for the movie night?🎬 I'll order some pizza but you can bring something to eat too👍</p>
    </div>
  </li>

  <li class="chat-content">
    <img src="./img/alvin-balemesa-lJstr7OYCoM-unsplash.jpg" alt="dog" />
    <div class="chat-body">
      <div class="name-and-time">
        <p>Karen</p>
        <p>Thu, 20:37</p>
      </div>
      <p>Hey Kyle, do you go to the movie night on Saturday? Eric will host this time :)</p>
    </div>
  </li>

  <!-- ...以下、他のチャットメッセージ要素が続く -->
</ul>
```

```css
/* ...その他CSSスタイルは割愛 */

.chat-wrapper {
  display: flex;
  flex-direction: column-reverse;/* 上下の要素順番入れ替えの値 */
}
```

flex-directionによる、上下要素の順番入れ替えの値は以下です。

flex-direction 値 | 役割
------------ | -------------
column | デフォルト。上から下へ要素が並ぶ。
column-reverse | 上下の順を逆転させる。