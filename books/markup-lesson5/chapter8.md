---
title: "コンテナーとコンテンツの分離"
free: true
---

# オブジェクト指向CSS（OOCSS）のルール2: コンテナーとコンテンツの分離（Separate container and content）

オブジェクト指向CSS（OOCSS）には、もう1つ大切なルールがあります。

それは、**コンテナーとコンテンツの分離**です。

こちらも、それぞれのキーワードの意味を見ていきましょう。

- コンテナー: パーツを収納している大きな箱
- コンテンツ: 再利用するパーツそのもの

それぞれ具体的に、以下のような例が挙げられます。

| コンテナー | コンテンツ |
| ---- | ---- |
| ヘッダー要素 | ヘッダー要素内のパーツ（ヘッダーメニュー etc） |
| フッター要素| フッター要素内のパーツ（コピーライト etc） |

つまり、以下のような親子関係の構造だということになります。

![contents-container](https://storage.googleapis.com/zenn-user-upload/5hr3bj9y3dgv4yyacos79gmaxu7x)

この構造がわかったところで、「コンテナーとコンテンツの分離」をしなければならないことに着目をすると、この親子関係の構造を分離しなければならないということになります。

HTMLの構造を崩すわけではないので、少し難しく考えがちなのですが、一言で表現すると、以下になります。

- セレクタ名指定を、1つの要素に対して親子で書かないこと

まだ少し説明がぼんやりしていますので、実際のコードを見ていきましょう。

まずは、コンテナーとコンテンツを分離せずに書いた例を見ましょう。

### コンテナーとコンテンツが分離されていない例

```css
.card .card-image {
  /* スタイル省略 */
}
```

 `.card` 要素の中にある `.card-image` パーツ要素と、親（コンテナー）である `.card` と子（コンテンツ）である `.card-image` を一緒に切り分けずに書いています。

こうすると何がいけないのでしょうか？

オブジェクト指向CSS（OOCSS）で最も意識をしたいことの1つである、「再利用性の高いclass」を利用していないことになるのが、ここでは問題です。

上記はそこまで問題があるように見えませんが、取り扱う要素が以下のようになると、どうでしょうか？

```css
.card {...}
.card .header {...}
.card .body {...}
.card .image {...}
.card .footer {...}
```

同じ構造のカード要素で、ヘッダーなどのコンテンツなどを再利用をしようと思うと、少しこれでは難しそうですね。

では、コンテナーとコンテンツを分離するとどうでしょうか？

### コンテナーとコンテンツが分離されている例

```css
/* コンテナー */
.card {...}

/* コンテンツ */
.card-header {...}
.card-body {...}
.card-image {...}
.card-footer {...}
```

こちらの構造であれば、ヘッダーなどのコンテンツなどを再利用しようと思ったときにも、 `.card-header` とだけHTMLに呼び出せば済みますので、再利用がしやすいですね。

短く、再利用性の高いパーツを生成し、重複を避ける、が、コンテナーとコンテンツを分けるルールにも意識されていることがわかるかと思います。