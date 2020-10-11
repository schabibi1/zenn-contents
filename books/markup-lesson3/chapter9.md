---
title: "marginの相殺現象"
---

marginの相殺とは、 **上下隣り合わせの要素では top と bottom のマージンが相殺され、結合されることがある現象のこと** を言います。

具体的にどういうことなのか、実例を視覚的に見てみましょう。

![kill_margin](https://storage.googleapis.com/zenn-user-upload/y8rconfntrcy3rjb4jr8cqupgfd6)

上記の図で、p要素が2つあり、それぞれのp要素の上下に20pxずつmarginが付いています。

本来であれば2つ目のp要素の上部は、

```html
上のp要素 margin-bottom 20px + 下のp要素 margin-top 20px = 40px
```

と考えられるので、上下のp要素の間には、40px分のmarginが存在するはずです。

しかし、Developer Toolで確認をすると、20px分しか存在しません。

これが **marginの相殺** です。

実際のHTML, CSSコードを見ても、p要素の上下には20pxずつ付いているはずということがわかります。

```html
<h2>Main</h2>
<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
<!-- この箇所のmarginのtopとbottomが相殺。20px + 20px = 40pxではなく、20pxになっている -->
<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
```

```css
* {
  margin: 0;
  padding: 0;
}

.main-body p {
  margin: 20px 0;
  /* margin: 上下px 左右px;という意味 */
}
```

marginの相殺は、デフォルトで起こる現象なので、marginの相殺を想定して実装をすることになります。

:::message
以下のソースコードは、こちらのJSFiddleで実際に手を動かしながら反映を見ることができます。
「Edit in JSFiddle」ページで確認してください。
:::

@[jsfiddle](https://jsfiddle.net/arisa_dev/nhtf2wmd/1/)