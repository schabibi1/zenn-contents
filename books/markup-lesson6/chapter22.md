---
title: "align-content"
---

`align-content` の役割は、コンテナー用に用意された、CSSグリッドプロパティ一覧のチャプターで、簡単に確認をしましたね。

プロパティ名 | 役割
------------ | -------------
 `align-content` | グリッドコンテナー内におけるグリッドトラックの縦方向（ブロック軸）の位置を指定するプロパティ

実は、Flexboxにも、似た役割のプロパティが用意されています。

`align-items` というもので、こちらも垂直方向の位置を指定するプロパティで、コンテナー用に用意されたプロパティです。

これまでのチャプタで取り組んだ例を使い、それぞれの値の違いを見ていきましょう。

:::message
コンテナー用に用意されたプロパティですが、 `align-content` は複数形ではなく、 **単数系の `content`** であることに注意してください。
開発をしていて、不具合がある場合に、まず最初に疑いたい原因の1つは、スペルミスです。
:::

# align-content: normal;

![](https://storage.googleapis.com/zenn-user-upload/icsdbw8alp1d4kddjtbeotv6c4vv)

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson6-align-content」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges/tree/main/lesson6-align-content)

```css
/* その他省略 */

.container-body {
  /* コンテナーに対する、CSSグリッドのスタイル */
  display: grid;
  grid-template-columns: auto auto;
  grid-auto-rows: auto auto;
  grid-row-gap: 1em;
  align-content: normal;/* 👈 */

  /* その他のスタイル */
  background-color: #9fbef8;
  margin: 0 auto;
  max-width: 80%;
  height: 400px;
}
```

Flexboxの `align-items` の初期値は、 `stretch` でしたが、CSSグリッドの `align-contet` の初期値は `normal` です。

`align-content` を付与しない場合は、 `normal` が付与された状態と同じ反映になります。

# align-content: start;

![](https://storage.googleapis.com/zenn-user-upload/zfiwbc4e6kbiibcguhkp3vkikm8q)

```css
align-content: start;
```

# align-content: end;

![](https://storage.googleapis.com/zenn-user-upload/ojtc6k68v8myj4qu4drse1qs6n08)

```css
align-content: end;
```

# align-content: center;

![](https://storage.googleapis.com/zenn-user-upload/hhhs8soqg5rs9bdfx37xf8wnxxzu)

```css
align-content: center;
```

# align-content: stretch;

![](https://storage.googleapis.com/zenn-user-upload/icsdbw8alp1d4kddjtbeotv6c4vv)

```css
align-content: stretch;
```

反映が `normal` と変わらないのですが、これは、 **グリッドトラックの範囲いっぱいに、グリッドセルを広げる** という意味なので、Developer Toolsのグリッドラインを見れば、それぞれグリッドトラックいっぱいに、グリッドセルが広がっていることがわかります。

# align-content: space-between;

![](https://storage.googleapis.com/zenn-user-upload/ue3dnuhx9fvn5wqz4kiga5ehcmaw)

```css
align-content: space-between;
```

# align-content: space-around;

![](https://storage.googleapis.com/zenn-user-upload/r77fznt7dxhfgex8fauo5xaut8vp)

```css
align-content: space-around;
```
以下の `space-evenly` と変わりなく見えますが、この例で、全体の `height` をもう少し増やすと、変化が見れます。

![](https://storage.googleapis.com/zenn-user-upload/l12g0q6rusqnuaa9ky1asw7ljb8g)


# align-content: space-evenly;

![](https://storage.googleapis.com/zenn-user-upload/r77fznt7dxhfgex8fauo5xaut8vp)

```css
align-content: space-evenly;
```

`space-around` と変わりなく見えますが、この例で、全体の `height` をもう少し増やすと、変化が見れます。

![](https://storage.googleapis.com/zenn-user-upload/8oi7pmw1s691iy8jdz9hhknnh95j)

# 値一覧

使用できる値 | 役割
------------ | -------------
`normal` | 初期値
`start` | 上部に寄せる配置
`end` | 下部に寄せる配置
`center` | 中央に寄せる配置
`stretch` | グリッドトラックの範囲いっぱいに、グリッドセルを広げる
`space-between` | 均等配置 / グリッドトラック外側の余白無し
`space-around` | 均等配置 / グリッドトラック外側の余白あり。余白はアイテム間の半分
`space-evenly` | 均等配置 / グリッドトラック外側の余白は、アイテム間と同じ幅
