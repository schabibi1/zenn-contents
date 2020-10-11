---
title: "positionとz-index"
free: true
---

# 要素の重なり順調整: positionとz-index

[「マークアップ言語シリーズ: Lesson 2 CSSの基本」](https://zenn.dev/arisa_dev/books/markup-lesson2)の[「要素の配置: 中央」](https://zenn.dev/arisa_dev/books/markup-lesson2/viewer/chapter11)で、要素の配置に関するスタイルとしてpositionを学びました。

今度は、positionと組み合わせて、要素の重なり順を調整するスタイル、 **z-index** を習得していきましょう。

まず、z-indexとは、 **HTML要素の重なる順番を指定して調整することができる設定内容** です。

floatがどういうものか学んだ時に、webページを横面から見た図を確認しましたね。

z-indexも同じイメージでwebページを横面から見た時を想像すると、イメージしやすいです。

ただし、z-indexの場合は、どの要素が最も前面に出るか、後ろに配置させるか、順番を指定して変えることができます。

z-indexは、0が最も小さい値で、重なる順番が前面に出るにつれ、値の数値は大きくなります。

実例を見てみましょう。

以下の図を見てください。

![z-index_sample](https://storage.googleapis.com/zenn-user-upload/errws9x36hcntzpq2a72kt0chigd)

画像要素が、重なり順では一番前に来ていて、画像の下に背景色グレーの要素が配置されていますね。

このような表示に見せるためには、「配置の調整」と「要素の重なる順番調整」2つを組み合わせて一緒に実装することで実現可能です。

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson3-z-index」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

では、z-indexとpositionの関連性を見ていくために、まずは上記の例を、z-indexとpositionなしで反映結果を見てみましょう。

コードと反映結果は以下です。

```html
<div class="wrapper">
  <img src="khloe-arledge-xGNi3-Hn66w-unsplash.jpg" alt="breakfast" />
  <div class="shadow"></div>
</div>
```

```css
* {
  margin: 0;
  padding: 0;
}

.wrapper {
  max-width: 80%;
  margin: 30px auto;
}

img {
  width: 90%;
  height: auto;
  border-radius: 5px;
}

.shadow {
  padding: 300px 95px;
  width: 70%;
  height: auto;
  background-color: #b3c4d4;
  border-radius: 5px;
}
```

![disabled_z_index](https://storage.googleapis.com/zenn-user-upload/e72w8w9m3yob2cjtncmax4k8hq9m)

画像要素も、グレー背景色要素も、重なり順が決まっていないので、デフォルト（初期値）の表示で、どちらの要素も前後していない状態です。

では、試しにz-indexの設定のみ、両方の要素に実装してみるとどうなるでしょうか？

```css
/* 上記省略 */

img {
  width: 90%;
  height: auto;
  border-radius: 5px;

  /* z-index設定 */
  z-index: 1;
}

.shadow {
  padding: 300px 95px;
  width: 70%;
  height: auto;
  background-color: #b3c4d4;
  border-radius: 5px;

  /* z-index設定 */
  z-index: 0;
}
```

![disabled_z_index](https://storage.googleapis.com/zenn-user-upload/e72w8w9m3yob2cjtncmax4k8hq9m)

ブラウザでの反映結果が、z-indexもpositionも実装されていない時と、変化がないですね。

つまり、**z-indexの設定だけでは、要素の重なり順の指定が効かない**ということになります。

では、要素の配置設定のpositionだけ実装すると反映結果はどうなるのでしょうか？

```css
/* 上記省略 */

img {
  width: 90%;
  height: auto;
  border-radius: 5px;

  /* position設定 */
  position: relative;
}

.shadow {
  padding: 300px 95px;
  width: 70%;
  height: auto;
  background-color: #b3c4d4;
  border-radius: 5px;

  /* position設定 */
  position: relative;
  bottom: 580px;
  left: 35px;
}
```

![only_position](https://storage.googleapis.com/zenn-user-upload/t4ohekmtymyfnww2y01s3jf4ngbz)

今度は、背景色グレーの要素が前面に出て来てしまいました。

z-indexとpositionを一緒に組み合わせない場合は、なかなか思うようにスタイルの調整ができません。

上記の完成見本の図のように、画像を前面、背景色グレーの要素を後方と重なりを指定するには、z-indexとpositionの実装を一緒に行う必要があるということですね。

```css
/* 上記省略 */

img {
  width: 90%;
  height: auto;
  border-radius: 5px;

  /* z-indexとposition設定 */
  position: relative;
  z-index: 1;
}

.shadow {
  padding: 300px 95px;
  width: 70%;
  height: auto;
  background-color: #b3c4d4;
  border-radius: 5px;

  /* z-indexとposition設定 */
  position: relative;
  bottom: 580px;
  left: 35px;
  z-index: 0;
}
```

![z-index_sample](https://storage.googleapis.com/zenn-user-upload/errws9x36hcntzpq2a72kt0chigd)