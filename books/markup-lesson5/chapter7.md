---
title: "構造とスキンの分離"
free: true
---

# オブジェクト指向CSS（OOCSS）のルール1: 構造とスキンの分離（Separate structure and skin）

チャプター3から7までは、とてもシンプルなオブジェクト指向CSS（OOCSS）の例を見て、練習問題にも取り組みましたね。

では、もう少しオブジェクト指向CSS（OOCSS）の詳しい構造と、仕組みを見ていきましょう。

オブジェクト指向CSS（OOCSS）では、**構造とスキンの分離**というルールが決まっています。

構造とスキンは、それぞれ以下の意味を持ちます。

- 構造: HTML要素による構造
- スキン: 見た目

それぞれ具体的に、以下のような例が挙げられます。

| 構造 | スキン |
| ---- | ---- |
| テキストや画像 | 影や背景色 |
| コンテンツのパディング| パディングの大きさ |
| ボーダー | 幅や高さ |
| ボタン | ホバー時の色 |

つまり、**上記をそれぞれ分けて、classに指定をするのが、オブジェクト指向CSS（OOCSS）の「構造とスキンの分離」ルール**ということになります。

具体例を視覚的に見ていきましょう。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/ayc14w6d/26/)

以下のような、非常にシンプルな2種類のボタン要素を用意するとしましょう。

![oocss-btn](https://storage.googleapis.com/zenn-user-upload/kz0s1rps1x4yyymsistay6j1fjwc)

これらのボタン要素には、以下のスタイル付与をします。

1. 「登録する」ボタンは緑の背景色
2. 「キャンセル」ボタンはピンクの背景色
3. 2種類とも文字色は白
4. ホバー時には、2種類ともカーソルをポインターに指定
5. ホバー時には、2種類ともそれぞれ背景色を暗くする
6. 2種類ともボーダーは無効化する
7. 2種類とも角に丸みをつける
8. 2種類ともpaddingを10pxで付与

では、1から8までの項目のうち、それぞれ構造に該当するのか、スキンに該当するのかを分けていきましょう。

1. 「登録する」ボタンは緑の背景色 → **スキン**
2. 「キャンセル」ボタンはピンクの背景色 → **スキン**
3. 2種類とも文字色は白　→ **構造**
4. ホバー時には、2種類ともカーソルをポインターに指定　→ **構造**
5. ホバー時には、2種類ともそれぞれ背景色を暗くする　→ **スキン**
6. 2種類ともボーダーは無効化する　→ **構造**
7. 2種類とも角に丸みをつける　→ **構造**
8. 2種類ともpaddingを10pxで付与　→ **構造**

実際にコードに落とし込んで見ていきます。

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

ここで1つ引っかけの回答が、3の文字色です。

視覚的要素になるので、スキンかと思いきや、構造になっています。

なぜでしょうか？

視覚的に違いを見た方が理解しやすいので、上記のコードを、2種類のボタン要素の文字色をスキンとして書いてみます。

```css
@charset "UTF-8";

/* 構造 */
.btn {
  padding: 10px;
  border-radius: 4px;
  /* color: #ffffff; */
  border: none;
}

/* スキン */
.green {
  background-color: #1caf78;
  color: #ffffff;/* 追加 */
}

.pink {
  background-color: #E56596;
  color: #ffffff;/* 追加 */
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

先ほどの例では、一度でよかった文字色の記述が、2回書かなければならず、同じスタイルの記述の重複が起こっています。

これではオブジェクト指向CSS（OOCSS）の目的が達成できていませんね。

オブジェクト指向CSS（OOCSS）の本来の目的は、重複を避け、再利用性の高いパーツを生成することなので、そのことを踏まえると、この場合は、文字色は2種類のボタンとも共通のスタイルなので、構造として組み込むのが良いということになります。

勘の良い方であれば、4のポインター指定のスタイルはどうなのか、と気になったかもしれませんね。

こちらは、再利用性を意識して、新たにポインター指定の構造セレクタを作っても、HTMLのclass名の数が多くなります。

CSSも、hover要素以外には再利用できないセレクタになりますし、ポインタ指定のスタイルは確かに一度だけ書けばよくなりますが、新たにセレクタを生成することで、行数自体は増えることになります。

```html
<!-- .hover-pointerが増えた -->
<button class="btn green hover-green hover-pointer">
  登録する
</button>
<button class="btn pink hover-pink hover-pointer">
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

.hover-pointer {/* 追加: 合計3行が増えている */
  cursor: pointer;
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
  /* cursor: pointer; */
}

.hover-pink:hover {
  background-color: #D9256A;
  /* cursor: pointer; */
}
```

構造か、スキンかで迷った際には、構造とスキンの役割を踏まえた上で、短く、再利用性の高いパーツを生成し、重複を避ける、この3つを満たす条件のものを選ぶと良いでしょう。

# シングルクラスとマルチクラス

ここで気がつかれたかもしれませんが、class名を1つ以上、1つのHTML要素に対して付与をしていますね。

HTML要素に、1つ以上のclass名を付与することは、禁止されていません。

むしろ、オブジェクト指向CSS（OOCSS）を意識してコードを実装するには、禁止されていては困るということでもあります。

1つだけclass名が付与されているものを**シングルクラス**と呼び、複数のclass名が1つのHTML要素に付与されているものを**マルチクラス**と呼ぶので、ここで紹介しておきます。