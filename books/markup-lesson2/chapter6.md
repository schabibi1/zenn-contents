---
title: "CSSの構文: 子孫セレクタ"
free: true
---

# 子孫セレクタ

HTML、CSSを学んで気がつかれたかと思いますが、プログラミングでは、よく「親子」というキーワードを使って関連性を表現する方法を使います。

CSSでスタイルを付与する際にも、HTML要素の親子関係を意識すると、思い通りのスタイルを実装することができます。

例えば、以下のようなHTML構成があったとします。

```html
<div class="parent-div">
  <p>class属性parrent-divの、直接の子（子孫）に該当する要素</p>
  <div>
    <p>class属性parrent-divの、直接の子孫に当てはまらない要素</p>
  </div>
</div>
```

class属性parent-divの直接の子孫、子要素のp要素は、以下のようにセレクタ名を指定することで、スタイルの付与ができます。

```css
.parent-div p {
  color: #800080;/* 紫 */
  font-weight: 800;
}
```

このようにセレクタを指定すると、2つとものp要素に上記のスタイルが適用されます。

![child_and_grandchild_same_style.png](https://storage.googleapis.com/zenn-user-upload/v1x2a7kakkdqqkfp9rner8cne53n)

では、上記の例で、class属性parent-divの直接の子要素pに、子孫以外の要素とは別のスタイルを付与しようと思った場合、どうセレクタ名を指定すると良いでしょうか？

子要素の文字色だけを、緑に変えてみましょう。

直接の子孫である子要素のみ有効化したいスタイルがある場合は、 `>` の記号をセレクタに使用します。

```css
/* 直接の子孫要素ではない */
.parent-div p {
  color: #800080;/* 紫 */
  font-weight: 800;
}

/* 直接の子孫、子要素のみの設定 */
.parent-div > p {
  color: #3ca84e;/* 緑 */
  font-weight: 800;
}
```

![only_direct_child](https://storage.googleapis.com/zenn-user-upload/wyfyqoh450z6fq2qn7rhj7clzsde)

直接の子孫である子要素のみに、特定のスタイルを付与することができましたね。

:::message
CSSは、下に書いてあるスタイルを優先して読み込みます。そのため、今回のような場合、上記CSSの記述の順番を入れ替えると、どちらの文字色も緑になってしまいます。スタイルを書く順番に気をつけましょう。
:::