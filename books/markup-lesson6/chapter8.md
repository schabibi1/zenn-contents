---
title: "グリッド軸(Grid axis)"
free: true
---

# グリッド軸(Grid axis)とは？

グリッド軸とは、2方向の軸で、それぞれ、 `横(row: 行)` と `縦(column: 列)` があります。

区別については、前回のチャプターで見分けがつくようになったかと思います。

このチャプターでは、いよいよグリッド軸の詳細について解説をしていきます。

本書のチャプター4で先に少しFlexboxとの構造概念の違いをお話しした時に、以下のことに着目をしました。

Flexbox | Gridレイアウト
------------ | -------------
**1つの軸（`flex-direction`）** で、アイテムを縦方向か横方向か**どちらか**を決める構造 |  `横(row: 行)` と `縦(column: 列)` の**2つの軸**で、アイテムを縦方向か横方向か決める構造

Flexboxの学習を[「マークアップ言語シリーズ: Lesson 4 並列、Flexbox」](https://zenn.dev/arisa_dev/books/markup-lesson4)で学習した際に、「**軸** という話が出てこなかったはず」と思われたかもしれません。

そう思われた方は、テキストをよく読み込まれているということです。

# Flexboxの項目で、Flexboxの軸についてふれなかった理由

実は、あえて[「マークアップ言語シリーズ: Lesson 4 並列、Flexbox」](https://zenn.dev/arisa_dev/books/markup-lesson4)のテキストで説明をしなかったのには理由があります。

Flexbox単体だけを理解する時に、軸の話をすると、大事な概念ではあるのですが、CSSグリッドをまだ学習していない段階では、**FlexboxとCSSグリッドの構造概念の比較ができないので、理解が難しくなる**ためです。

CSSグリッドが主要ブラウザでサポートされる前は、Flexbox単体だけを学習する際にも、大事な概念になるので、比較するCSSグリッドのことを学習していない段階でも、取り扱っている教材やソースは非常に多かったです。

（CSSグリッドがなかった時には、CSSグリッドは学習のしようがなかったからですね）

今でもFlexboxの学習段階に入ると、そこでFlexboxの軸について構造概念を説明するソースが多いですが、Flexbox単体だけだと、一度に取り扱うのは1つの軸までなので、具体的に軸として意識をすることが明確にしづらいのです。

ですが、1つの軸だけを取り扱う場合と、2つの軸を同時に扱える場合で比較ができれば、それぞれの違いや、実装できることの違いがはっきり見ることができるので、軸としての認識が、結果的にどちらも明確にできるようになります。

そういう理由で、Lilac(ライレック)では、CSSグリッドに入る段階で、Flexboxの軸についても、グリッド軸について学習をするタイミングで解説を詳しくするようにしています。

# Flexboxの軸と、グリッド軸の比較

MDNでFlexboxを調べると「Flexboxの2つの軸」と説明があるので、「Flexboxにも軸が2つあるのでは？」と思われたかもしれません。

その通りです。

Flexboxにも、CSSグリッドと名前は違っても、軸自体は、行と列の2つ用意されています。

主軸（main axis） | 交差軸(cross zxis)
------------ | -------------
 `flex-direction` プロパティによって定義 | 主軸に垂直に交わる軸

しかし **Flexboxでは、2つの軸を同時に制御できません**。

Flexboxは一次元のレイアウトモデルですから、一つの次元、つまり、**一度に制御できる軸の数は、行か列のどちらか1つのみ**なのです。

CSSグリッドはそれに対して、二次元のレイアウトモデルなので、一度に2つの方向の軸の制御が、同時にできます。

そのため、Flexboxでは、一度に1つの方向の軸しかレイアウトできないことになるので、

- Flexboxは、1つの軸でアイテムを縦方向か横方向か決める構造
- CSSグリッドは、2つの軸でアイテムを縦方向か横方向か決める構造

と、導入部分では表現をしていました。

視覚的にも、Flexboxの軸（一次元）とグリッド軸（二次元）の違いを見ていきます。

[「マークアップ言語シリーズ: Lesson 4 並列、Flexbox」](https://zenn.dev/arisa_dev/books/markup-lesson4)で、 `flex-direction` について学習をした時に使用をした、以下のサンプルを見てみましょう。

![](https://storage.googleapis.com/zenn-user-upload/ewqvqfgkorv09zgrtd8ildh88f9y)

このサンプルを使って学習をした、Flexboxの軸を操作する、 `flex-direction` についても、値で用意されているものを確認します。

flexbox-direction 値 | 役割
------------ | -------------
row | デフォルト。左から右へ要素を並列させる **(横/行)**
row-reverse | 右から左へ要素を並べ替えて並列させる **(横/行)**
column | デフォルト。上から下へ要素が並ぶ。 **(縦/列)**
column-reverse | 上下の順を逆転させる。 **(縦/列)**

では、Flexboxだけを使用して、以下の構造を実装することはできるでしょうか？

![](https://storage.googleapis.com/zenn-user-upload/9f2avwlzn011hhhoyet7m5z4x0mu)

正解は、できますが、2方向の制御が同時にできないので、 `flex-direction` で制御する軸をrowかcolumnかで選ぶ必要があります。

さらに、選べなかった方に関しては、他の微調整を考えるしかなく、クリエイティブに考える必要があり、エンジニアの腕任せになってしまって非効率的です。

CSSグリッドのプロパティや値について、まだ解説をしていませんが、この先のチャプターで順次解説していきます。

値の意味は、今はまだわからなくても良いので、まずは、1方向しか軸の操作ができないのか、2方向の軸の操作ができるかだけ着目し、それぞれのコードの違いを見てみましょう。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/8ps0vzLj/)

### Flexboxの場合

![](https://storage.googleapis.com/zenn-user-upload/2irwlw7d26r87ayccyn2ec1q67lu)

```css
/* その他スタイル省略 */

ul, li {
  /* その他のスタイル */
  list-style-type: none;
  border-radius: 3px;
  background-color: #fdeebc;
  padding: 40px;

  /* ❌ rowアイテムに一括でギャップを与えるスタイルがFlexboxには無いので、marginで対処するしかない */
  margin: 10px 0;
  width: 20%;
}

.container-body {
  /* コンテナーに対する、Flexboxのスタイル */
  display: flex;
  /* flex-direction: row-reverse; ← ❌ rowを同時に書けない */
  flex-direction: column-reverse; /* ← 😢 rowの制御を切り捨て、columnだけ制御 */
  align-items: flex-end;

  /* その他のスタイル */
  background-color: #9fbef8;
  margin: 0 auto;
  width: 80%;
}
```

### CSSグリッドの場合

![](https://storage.googleapis.com/zenn-user-upload/2a4mrxpclxymrtygc2tki5cfdynu)

```css
/* その他スタイル省略 */

.container-body {
  /* コンテナーに対する、CSSグリッドのスタイル */
  display: grid;
  /* ✅ columnとrowの2方向の軸を同時に操作している */
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-row-gap: 1em;

  /* その他のスタイル */
  background-color: #9fbef8;
  margin: 0 auto;
  max-width: 80%;
}

/* アイテムに対する、CSSグリッドのスタイル */
/* ✅ columnとrowの2方向の軸を同時に操作している */
.item-1 {
  grid-row: 3 / 3;
  grid-column: 3 / 4;
}

.item-2 {
  grid-row: 2 / 3;
  grid-column: 3 / 4;
}

.item-3 {
  grid-row: 2 / 1;
  grid-column: 3 / 4;
}
```

いかがでしょうか？

Flexboxで実装をした方は、行のrowか、列のcolumnかを選ぶしか選択肢がなく、1つの軸だけで大まかな制御をした後に、制御できなかった軸は他でカバーしなければならないのに対し、CSSグリッドの場合は、行のrowも、列のcolumnも同時に制御をすることができていますね。

もう少し平たく表現すると、Flexboxには、rowとcolumnを同時に制御する方法が用意されていないのに対し、CSSグリッドでは、**どちらも同時に制御することのできるプロパティと値が豊富**にあります。