---
title: "floatのデメリット: 回り込み"
free: true
---

さて、floatで要素を浮動させることにより、並列させることを学習しましたが、floatにはデメリットもあります。

floatは、要素を「浮かせた」状態にすることを、本書のはじめに学習をしましたね。

しかし、浮いた要素と、浮いていない要素が混在すると、以下の現象が起こります。

* 要素の一部が隠れて表示される
* 浮いていない要素が消えてしまう

これらの2つの現象を、実際に視覚的に見てみましょう。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/rx3mfs0n/3/)

### 要素の一部が隠れて表示される現象

```html
<div class="left-element">Left</div>
<div class="middle-element">Middle</div>
<div class="right-element">Right</div>
```

```css
* {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: #ffffff;
  font-size: 25px;
  text-align: center;
}

.left-element {
  background-color: #fac8c7;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.middle-element {
  background-color: #7c0e20;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.right-element {
  background-color: #64a08e;
  width: 550px;
  height: 40px;
  padding: 60px;
  /* floatなし */
}
```

floatがどの要素にもついていない、もともとの表示は以下ですが、

![no_float](https://storage.googleapis.com/zenn-user-upload/dfaf1kqfdjomrf7o6snb84ci1y20)

floatをLeftとMiddleにだけつけて、Rightにつけない場合、このようになってしまいます。

![no_float_only_right](https://storage.googleapis.com/zenn-user-upload/vejzyjy12fjrm3sky3t0d0uwsoqk)

もともと横長のRight要素の左部分が、見えていませんね。

### 浮いていない要素が消える現象

```css
* {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: #ffffff;
  font-size: 25px;
  text-align: center;
}

.left-element {
  background-color: #fac8c7;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.middle-element {
  background-color: #7c0e20;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.right-element {
  background-color: #64a08e;
  width: 150px;/* 横幅を他の要素と同様にした */
  height: 40px;
  padding: 60px;
  /* floatなし */
}
```

先ほどの例で、Rightの要素が横長ではなく、他の要素と同じくらいの横幅の要素だとします。

![same_width_default](https://storage.googleapis.com/zenn-user-upload/xtu6kzl0yzn5n4n2zwrw108bvjmh)

そうすると、まるでRight要素がなくなってしまったように、消えてしまう現象が起こります。

![right_element_dissapears](https://storage.googleapis.com/zenn-user-upload/0tsb7ehfkdcvywe0ay0kz4mshz3p)

これらの現象を **回り込み** と呼びます。

では、floatによる回り込みを防ぐにはどうしたら良いのでしょうか？

次の項目で、対処方法を見ていきましょう。

# 回り込みの対処方法1: clearプロパティ

floatによる回り込みを防ぐには、 **clearプロパティ** というものを使います。

使い方は非常に簡単です。

floatプロパティのついていない要素で、回り込みによって隠れてしまう要素に、以下の設定をCSSで行うだけです。

```css
clear: both;
```

つまり、先ほどの例で言うと、floatの設定のない、Right要素にclearプロパティを書けば良いと言うことになりますね。

実際に実装して、反映結果を見てみます。
Right要素の横幅を、他のLeftやMiddleの要素より少し長くした反映で見てみます。

```css
* {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: #ffffff;
  font-size: 25px;
  text-align: center;
}

.left-element {
  background-color: #fac8c7;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.middle-element {
  background-color: #7c0e20;
  width: 150px;
  height: 40px;
  padding: 60px;
  float: left;/* floatあり */
}

.right-element {
  background-color: #64a08e;
  width: 550px;
  height: 40px;
  padding: 60px;
  clear: both;/* clearプロパティ追加 */
}
```

![clearboth](https://storage.googleapis.com/zenn-user-upload/ceprwtrcdwzavrbbzwv57uod1r6e)

clearプロパティのおかげで、要素の一部が隠れてしまっていたRight要素が、回り込みをしなくなりましたね。

# 回り込みの対処方法2: clearfix

floatの回り込みの解決方法は、1つだけではありません。

clearプロパティの他に、 **clearfix** と言う方法もあります。

floatを使う場合、回り込みの対処をするには、clearfixで対処をする方法が、今では主流になっています。

理由としては、 **clearプロパティの設定がある要素は、margin-topの設定が無効になってしまう** ので、clearfixを使うことで、そのような懸念が必要なくなるからです。

では、clearfixの使い方を見ていきましょう。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで、反映結果部分の表示を大きく調整して確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/9etc25mx/3/)

clearfixを有効化させる設定は、HTMLファイルとCSSファイルに、それぞれ以下の記述をするだけです。

```html
<div class="clearfix"></div>
```

```css
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

HTMLファイルには、cleafixの設定をかける要素にclass名「clearfix」を追加したのみですね。

CSSファイルには、セレクタ名clearfixに、clearプロパティの設定と、ブロック（縦並び）表示の設定をしています。

contentプロパティには、テキスト文字などを入れることができますが、通常は非推奨のため入れません。

書き方を確認できたので、今度は、一般的なwebページの構成で実例を見てみます。

先ほど、clearプロパティで対処した場合と、clearfixで対処した場合では、clearプロパティの設定がある要素にmargin-topが効かなくなってしまうと、解説をしました。

視覚的に、実際にどう反映結果に差が出るのか、見ていきましょう。

```html
<div class="wrapper">
  <header class="header">Header</header>

  <div id="body-wrapper" class="clearfix">
    <main class="main-body">Main</main>
    <aside class="sidebar">Sidebar</aside>
  </div>

  <footer class="footer">Footer</footer>
</div>
```

```css
* {
  margin: 0;
  padding: 0;
  color: #ffffff;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: 600;
  font-size: 25px;
  text-align: center;
}

.wrapper {
  max-width: 80%;
  margin: 0 auto;
}

.header {
  background-color: #fbefff;
  width: 100%;
  height: 70px;
  padding: 30px 0 0 0;
}

.main-body {
  background-color: #add8e6;
  width: 70%;
  height: 150px;
  float: left;/* float */
  padding: 50px 0;
}

.sidebar {
  background-color: #639;
  width: 30%;
  height: 150px;
  float: left;/* float */
  padding: 50px 0;
}

.footer {
  background-color: #999;
  width: 100%;
  height: 70px;
  padding: 30px 0 0 0;
  margin-top: 50px;/* clearプロパティでは効かないmargin-top */
}

/* clearfixの設定 */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

### clearプロパティで対処した場合の反映結果

![clear_property](https://storage.googleapis.com/zenn-user-upload/jc2muf1j1lqkgbe0f29h0wfk6fzr)

### clearfixで対処した場合の反映結果

![clearfix](https://storage.googleapis.com/zenn-user-upload/dadh4ykd8vj1czdaevgs8sksa06m)

Footer要素の上部に、margin-topで少しスペースを開けようと設定をしていますが、clearプロパティで対処した場合と、clearfixで対処した場合とで、ブラウザの反映結果に変化がありますね。

clearプロパティで対処した場合は、margin-topが無効化されています。

一方でclearfixで対処した場合は、きちんとmargin-topの設定が反映されています。

clearfixでfloatの回り込みを対処することで、思わぬ反映結果の違いのリスクを回避できることが、実例で視覚的に確認できましたね。
