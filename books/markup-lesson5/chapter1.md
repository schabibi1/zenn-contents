---
title: "命名規則とは？"
free: true
---

オブジェクト指向CSSの話に入る前に、1つ大切な考え方がありますので、ここで解説をします。

**命名規則**という考え方です。

**命名規則**とは、一言で説明すると「名前の付け方のルール」です。

何の名前の付け方のルールかと言うと、マークアップ言語（HTML, CSS）では、class名とid名の付け方です。

**命名規則**は、他の言語にもある考え方で、**具体的に内容が一瞬でわかるような名前をつけましょう**という考え方です。

コードで具体的に実例をお見せすると、以下のような違いです。

### 命名規則を適応していない場合

```html
<header>
  <div class="item1">
    <h1>ヘッダー</h1>
  </div>
  <div class="item2">
    <ul>
      <li>TOP</li>
      <li>BLOG</li>
    </ul>
  </div>
</header>

<main>
  <div class="item3">
    <h2>タイトル</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis repellat similique qui voluptatum incidunt et, minus, ipsa ad deserunt, voluptates reiciendis quae dolore. Ut eos sit labore sequi aspernatur. Quisquam.
    </p>
  </div>
</main>

<footer>©︎2020</footer>
```

### 命名規則が適応されている場合

```html
<header>
  <div class="header-title">
    <h1>ヘッダー</h1>
  </div>
  <div class="header-menu">
    <ul>
      <li>TOP</li>
      <li>BLOG</li>
    </ul>
  </div>
</header>

<main>
  <div class="article">
    <h2>タイトル</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis repellat similique qui voluptatum incidunt et, minus, ipsa ad deserunt, voluptates reiciendis quae dolore. Ut eos sit labore sequi aspernatur. Quisquam.
    </p>
  </div>
</main>

<footer>©︎2020</footer>
```

上記の命名規則を適応している方は、class名を読むだけで、瞬時に要素の役割が把握できるのに対し、命名規則を適応していない例では、class名を読むだけでは、要素のコンテンツや役割がわからず、コード全体をよく読まなければ把握ができませんね。

命名規則を適応することで、個人開発の場合は、時間が経ってメンテナンスを行う場合に、自分の書いたコードの構成把握がしやすくなります。

チーム開発では、自分以外の人が書いたコードから、メンバー全員が要素の構成と役割が瞬時に把握でき、開発の時間を短く効率的にすることができます。

:::message
命名をする際には、ローマ字読みで命名するのは避けましょう。（悪い例: 🙅‍♀️hako 良い例: 🙆‍♂️box）
長くなる傾向にあるので、スペルミスが生じやすくなり、読みづらくなります。
:::