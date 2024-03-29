---
title: "オブジェクト指向CSSのコツ"
free: true
---

オブジェクト指向CSS（OOCSS）の使い方を具体例を見て学習し、使用する目的についても、学習をしました。

実は、オブジェクト指向CSS（OOCSS）を意識できていなかったとしても、ブラウザの反映でエラーが出ることはほとんどないのも事実です。

それが逆に、オブジェクト指向CSS（OOCSS）でコードを書くことができているのか、自分で見分けるのが難しいところでもあります。

学習中の時には、以下を意識することで、自分でもオブジェクト指向CSS（OOCSS）でコードを実装することができているかどうかをチェックする指標になりますので、参考にしてみましょう。

1. id属性は、なるべく使用しない
2. `!important` は、なるべく使用しない
3. 誰が見てもわかりやすくて、短い名前をつける
4. 一部分のみのスタイリングは、なるべく使用しない

それぞれ理由を解説をしていきます。

# id属性は、なるべく使用しない

オブジェクト指向CSS（OOCSS）では、再利用できるコンポーネントを意識して、スタイリングしていきます。

その点、id属性は、一度しか使用できません。

同じid名を、複数のHTML要素に付与することはできませんので、再利用、つまり何度も利用することを目的としてコンポーネントを生成するオブジェクト指向CSS（OOCSS）には不向きということになります。

### よくない例

```html
<!-- 同じid名は複数付与できない🙅‍♀️ -->
<div id="card">
  <!-- 省略 -->
</div>
<div id="card">
  <!-- 省略 -->
</div>
```

### 正しい例

```html
<!-- class属性はOK🙆‍♀️ -->
<div class="card">
  <!-- 省略 -->
</div>
<div class="card">
  <!-- 省略 -->
</div>
```

# !important は、なるべく使用しない

CSSを書いていて、特定のスタイルが読み込まれないということを、経験したことがある人もいるかもしれません。

その際に、検索して出てくる解決策の1つに、 `!important` というものがあります。

実際に、上記のような状況では、読み込まれなかったスタイルが読み込まれるようにあれば、エラーが解決したように思えます。

しかし、オブジェクト指向CSS（OOCSS）に限らず、モダンなweb開発では、多用を推奨していません。

理由は、 `!important` が、一般的なclass属性の振る舞いを変えてしまう性質を持っているからです。

CSSは、ソースコードファイルの下に書いてある内容ほど、優先して読み込む習性があります。

つまり、特定のスタイルが読み込まれないというのは、読み込んで欲しいスタイルの記述以降に、同じセレクタ名を重複して用意してしまい、そこで上書きされてしまっていることも多いのです。

```css
/* 読み込まれないスタイル */
.card-header {
  color: #ffffff;
}

/* ...その他コードの記述 */

/* 下に書かれており、同じセレクタ名なので、こちらが呼ばれてしまう */
.card-header {
  color: #666666;
}
```

このような場合は、文字検索をVS Codeで行い、同じセレクタ名で重複がないかを確認すると良いでしょう。

文字検索は、[「マークアップ言語シリーズ: Lesson 0 Visual Studio Codeを導入してみよう」](https://zenn.dev/arisa_dev/books/markup-lesson0)の、[「文字検索と置換」](https://zenn.dev/arisa_dev/books/markup-lesson0/viewer/chapter4)に、方法が載っています。

開発の際に、スタイルの予測が難しくなるため、`!important` は、利用を出来る限り避けましょう。

# 誰が見てもわかりやすくて、短い名前をつける

省略されすぎても、長すぎてもわかりづらいので、誰が見てもわかりやすいかどうかを、命名する時には基準にすると良いでしょう。

短くする必要があれば、以下のような範囲であれば、短くしても、誰でも理解ができます。

| 元々の形 | 省略系 |
| ---- | ---- |
| button | btn |
| xx-image | xx-img |

反対に、以下の例はわからない人もいるでしょう。

| 元々の形 | 省略系 |
| ---- | ---- |
| button | bt |
| xx-image | xx-i |

# 一部分のみのスタイリングは、なるべく使用しない

こちらに関しては、実はチャプター8の「構造とスキンの分離」で取り組んでいます。

2種類のボタンを用いて、構造とスキンに分けてセレクタを用意する例を、一緒に見ていきました。

もう一度コードを見直してみましょう。

![oocss-btn](https://storage.googleapis.com/zenn-user-upload/kz0s1rps1x4yyymsistay6j1fjwc)

```html
<button class="btn green hover-green">
  登録する
</button>
<button class="btn pink hover-pink">
  キャンセル
</button>
```

```css
@charset "UTF-8";

/* 構造 */
.btn {
  padding: 10px;
  border-radius: 4px;
  color: #ffffff;
  border: none;
}

/* スキン */
.green {
  background-color: #1caf78;
}

.pink {
  background-color: #E56596;
}

.hover-green:hover {
  background-color: #0e573c;
  cursor: pointer;
}

.hover-pink:hover {
  background-color: #D9256A;
  cursor: pointer;
}
```

文字色に関しては、重複を避けるために上記の形が理想ということでした。

もう1つ、構造に属しそうなポインターが、スキンに属している方が良いというところも、少し判断が難しい問題でしたね。

チャプター8では、まだオブジェクト指向CSS（OOCSS）を書く上でのコツを学習していませんでしたから、CSSでの行数が増えてしまうということで、主には解説をしています。

ここで具体的にもっと踏み込むと、**一部分のみのスタイリングを使用すると、CSS全体のセレクタの数が増えるから**ということになります。

再利用性を重視すればそれで良いというものでもなく、管理のしやすさを考えれば、セレクタの数を減らすことができればそうした方が良いということなのです。

今回のケースが、それに該当する理由としては以下の理由が挙げられます。

1. HTMLに付与するclass名が増える **→ 可読性の低下**
2. CSS全体のセレクタが増える **→ 可読性の低下**
3. ポインター以外の使用目的では再利用するチャンスが少ない **→ 再利用性が低い**

日常的な例で例えるなら、過剰包装しているのと同じような状況です。

| 過剰包装の場合 | ミニマルな包装の場合 |
| ---- | ---- |
| ゴミが増える | ゴミを減らせる |
| 散らかる | 整理整頓しやすい |

| 一部分のみのスタイリング使用 | 一部分のみのスタイリングを使用しない場合 |
| ---- | ---- |
| セレクタが増える | セレクタを減らせる |
| 散らかる | 整理整頓しやすい |