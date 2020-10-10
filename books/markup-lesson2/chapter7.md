---
title: "CSSの構文: 擬似クラス（hover）"
free: true
---

# 擬似クラス（hover）

擬似クラスとは、リンクやボタン要素にカーソルを合わせると色が変わるなど、状況に応じたスタイルの変更を行うことを言います。

擬似クラスの代表例として、カーソルをかざす動作を示す **hover** があります。

hoverを有効化すると、カーソルが該当要素に合わさった時に、特定のスタイルを付与することができます。

hoverを使って、button要素に、カーソルがホバーしたら背景色を変える設定を実装してみましょう。

```html
<button>hoverすると変化します</button>
```

```css
button {
  background-color: #800080;/* 背景色 紫 */

  /* その他スタイル */
  color: #ffffff;
  font-weight: 800;
  font-size: 30px;
  width: 500px;
  height: 300px;
  padding: 100px;
  margin: 100px;
}

button:hover {
  background-color: #000000;/* 背景色 黒 */
}
```

@[codepen](https://codepen.io/marissamarissa/pen/PozqNMj)

カーソルをブラウザで文字要素に合わせた時と、合わせなかった時とでは文字色が変化します。

擬似クラスのhoverは、特にリンク、ボタン要素でよく使用します。