---
title: "box-sizing: border-box;"
free: true
---

# 要素の面積を思い通りに指定する: box-sizing: border-box;

さて、ここで要素の配置に非常に便利な設定内容を紹介します。

paddingやborderに依存をした要素の配置調整をすると、効率の悪い要素の配置調整になります。

そのため、paddingやborderなどになるべく依存せずwidthやheightを指定して要素の面積を表現しますが、思うように指定できないことがあります。

以下のような要素のズレが生じてしまいます。

![without_box-sizing](https://storage.googleapis.com/zenn-user-upload/4jeq26wvn857m3f3vxnfxw0zr4go)

そのような時には、 `box-sizing: border-box;` を要素に設定します。

`box-sizing: border-box;` は、以下の条件が揃っている要素に実装可能です。

* paddingの設定がある要素
* borderの設定がある要素
* paddingとboraderどちらも設定のある要素

`box-sizing: border-box;` が有効化されることで、以下のメリットがあります。

* 思い通りのwidthやheightで要素が並列してくれる
* 要素の長さが飛び出ることがなくなる
* 意図した通りに要素を配置させることができる

上記の要素がずれてしまっていた例に、 `box-sizing: border-box;` を書き加えてみましょう。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/cm5akqgb/1/)

```html
<div class="wrapper">
  <header class="header">
    <h2>Header</h2>
  </header>

  <main class="main-body">
    <h2>Main</h2>
    <p>I'm a main body.</p>
  </main>

  <aside class="sidebar">
    <h2>Sidebar</h2>
  </aside>
</div>
```

```css
* {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

.wrapper {
  max-width: 80%;
  margin: 0 auto;
}

.header {
  color: #ffffff;
  background-color: #fff1b4;
  width: 100%;
  height: 50px;

  /* box-sizing設定 */
  padding: 13px 10px 10px 10px;
  box-sizing: border-box;
}

.main-body {
  background-color: #f0faf4;
  width: 70%;
  height: 530px;
  float: left;

  /* box-sizing設定 */
  padding: 13px 10px 10px 10px;
  box-sizing: border-box;
}

.sidebar {
  color: #ffffff;
  background-color: #fab87b;
  width: 30%;
  height: 530px;
  float: right;

  /* box-sizing設定 */
  padding: 13px 10px 10px 10px;
  box-sizing: border-box;
}
```

![with_border-box](https://storage.googleapis.com/zenn-user-upload/fcn4r4jdv5pc5d0xi6ppew3okhr9)

先ほどは、要素が思うようにCSSでwidthやheightで設定した通りに反映されていませんでしたが、 `box-sizing: border-box;` を書き加えるだけで、思い通りの要素の縦幅と横幅で表示がされるようになりました。

特に、MainとSidebarは、CSSで「Main 70%、Sidebar 30%」と、双方を合わせると100%に横幅が収まるようにCSSに書いているので、ぴったりの横幅で並列するよう意図してCSSを書いていました。

しかし、widthとheightだけでは、計算通りには並列せず、 `box-sizing: border-box;` があることによって、思い通りの配置を実現することができました。