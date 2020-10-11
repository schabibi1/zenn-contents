---
title: "オブジェクト指向CSS（OOCSS）とは？"
free: true
---

**オブジェクト指向CSS（OOCSS）** とは、Object-Oriented CSSの略で、一言で説明すると、**再利用でき無駄がないclassを設計する事**です。

「再利用できること」という特徴が、ここではキーワードになりますが、もう少し分かりやすく、ブログの構造の例を交えて解説します。

class属性の性質をここでおさらいすると、class属性は、以下のように、何度でも同じclass名を付与することができます。

:::message
以下のソースコードは、下記のリンクから、ダウンロードすることができます。
「lesson5-oocss-blog」のフォルダが、このチャプター該当ソースコードです。
:::

> [ソースコード](https://github.com/schabibi1/zenn-book-challenges)

```html
<div class="article-body">
  <img src="./images/jason-leung-RCoZaAnnBug-unsplash.jpg" alt="mugs" />
  <h2>記事タイトル１</h2>
  <p>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repellat corporis, tempora placeat recusandae dolor aliquam tenetur modi, harum sunt quia ab aspernatur officia cum cupiditate soluta porro vero dignissimos nulla.
  </p>
</div>

<div class="article-body">
  <img src="images/mitchell-luo-JhE0G6ESH8A-unsplash.jpg" alt="landscape" />
  <h2>記事タイトル２</h2>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem deleniti aperiam laboriosam cupiditate sit! Numquam adipisci accusantium odit eligendi! Atque praesentium repellendus repellat quisquam numquam incidunt, vero vel voluptatibus illum?
  </p>
</div>
```

```css
/* その他スタイル省略 */

.article-body {
  padding: 30px;
  margin: 30px auto;
  background-color: #c5c5c5;
  border-radius: 5px;
  max-width: 70%;
}
```

![oocss_reusable_class_demo](https://storage.googleapis.com/zenn-user-upload/bxm8oaiou7srotxv4xz40vezfnth)

上記のように、**共通するclass名を持つ要素は、共通のスタイルを付与**することができます。

このことを「再利用できる」と、オブジェクト指向OOCSSでは表現しています。

共通するclass名を持つ要素に、同じスタイルを付与することで、スタイルの記述をコンパクトにすることができています。

同じスタイルを付与する要素にもかかわらず、別々のclass名がついていた場合は、以下のように、同じスタイルの内容で2つのセレクタをわざわざ用意しなければならず、コードも長くなり、classの再利用性もありません。

```html
<div class="article-body-first">
  <img src="./images/jason-leung-RCoZaAnnBug-unsplash.jpg" alt="mugs" />
  <h2>記事タイトル１</h2>
  <p>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repellat corporis, tempora placeat recusandae dolor aliquam tenetur modi, harum sunt quia ab aspernatur officia cum cupiditate soluta porro vero dignissimos nulla.
  </p>
</div>

<div class="article-body-second">
  <img src="images/mitchell-luo-JhE0G6ESH8A-unsplash.jpg" alt="landscape" />
  <h2>記事タイトル２</h2>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem deleniti aperiam laboriosam cupiditate sit! Numquam adipisci accusantium odit eligendi! Atque praesentium repellendus repellat quisquam numquam incidunt, vero vel voluptatibus illum?
  </p>
</div>
```

```css
/* その他スタイル省略 */

/* どちらのセレクタ内も、全く同じスタイルの指定だが、class名が異なるために二度書いてしまっている */
.article-body-first {
  padding: 30px;
  margin: 30px auto;
  background-color: #c5c5c5;
  border-radius: 5px;
  max-width: 70%;
}

.article-body-second {
  padding: 30px;
  margin: 30px auto;
  background-color: #c5c5c5;
  border-radius: 5px;
  max-width: 70%;
}
```

少しずつオブジェクト指向OOCSSの概念がわかってきたところで、別の具体例で簡単な練習をしながら、さらに理解していきましょう。