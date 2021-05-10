---
title: "flex-wrap"
free: true
---

# コンテナに使用するFlexboxのプロパティ

## flex-wrap: アイテムの折り返し表示

`flex-wrap` は、画面幅に応じて、並列した要素を折り返して表示できます。

実例を見てみましょう。

以下の図では、並列する要素の数が多く、画面の全体幅に収まってはいますが、要素が左右から押しつぶされています。

![without-flex-wrap](https://storage.googleapis.com/zenn-user-upload/egiv475wv9s8xwsj4n1ip9g9wxl2)

この場合、画面幅に合わせて要素が折り返してくれると、全ての要素が綺麗に表示されます。

![with-flex-wrap](https://storage.googleapis.com/zenn-user-upload/ow71ll9p57wyvf60j203hq2awx44)

上記のように、画面幅に応じた要素の折り返しを設定するには、HTML要素に対して、以下のように `flex-wrap` を指定します。

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson4-flex-wrap」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

```html
<header>
  <h1>Recently Played</h1>
</header>
<main>
  <ul class="album-wrap">
    <li class="play-list">
      <img src="./img/magnezis-magnestic-TW62wXQ6Omc-unsplash.jpg" alt="tracks" />
      <div class="list-body">
        <h4>Tracks</h4>
        <p>sleepin' man</p>
        <button class="play-button">
          <img src="./img/play-button-arrowhead.png" alt="play" />
        </button>
      </div>
    </li>

    <li class="play-list">
      <img src="./img/marcela-laskoski-YrtFlrLo2DQ-unsplash.jpg" alt="electronics" />
      <div class="list-body">
        <h4>Electronic Focus</h4>
        <p>The Consmopolitan</p>
        <button class="play-button">
          <img src="./img/play-button-arrowhead.png" alt="play" />
        </button>
      </div>
    </li>

    <!-- ...以下、play-listアイテムが続く -->
  </ul>
</main>
<footer>
    <div class="icon-source">
      Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>
    </div>
</footer>
```

```css
/* ...その他スタイルは割愛 */

.album-wrap {
  display: flex;
  flex-wrap: wrap;
}
```

`display: flex;` の記述があることにより、Flexboxのレイアウトを使用することができるようになります。

Flexboxのレイアウトを使用するときは、必ずCSSに `display: flex;` を書いて、Flexboxのその他レイアウトを有効化するようにしましょう。

flex-wrapの値の一覧は以下です。

flex-wrap 値 | 役割
------------ | -------------
nowrap | デフォルト。折り返しなし。
wrap | 画面横幅に応じた、要素の折り返し。
wrap-reverse | 折り返し順を逆転させる。