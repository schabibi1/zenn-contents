---
title: "副作用フックの詳しい使い方"
---

# 2種類ある副作用

これまでのチャプターでは、副作用フックのカニ的な使い方について学びました。

ここからは、副作用フックのもう少し詳しい性質や使い方を学習していきましょう。

実は、Reactコンポーネントにおける副作用は、2種類に分類されます。

**クリーンアップコードを必要としない副作用**と、**必要とする副作用**です。

具体的にそれぞれ見ていきましょう。

# クリーンアップとは？

**クリーンアップ**とは、イベントリスナの削除や、タイマーのキャンセルのなどのことを示します。

残ると困るものがある場合場合、メモリリークが発生しないようクリーンアップをする必要があります。

タイマーのキャンセルがずっとキャンセルのままでは、タイマーの再生ができないかもしれませんし、イベントリスナが残っていることで、挙動が起こることもあるかもしれません。

そういったことが起こらないように「cleanup = 片付け」ておくので、クリーンアップという名前がついています。

# クリーンアップを必要としない副作用

まずはクリーンアップが必要ない副作用からです。

「手動での何かしらのDOM変更すること」が、クリーンアップを必要としない副作用と認識されます。

そのほかに、以下もクリーアップを必要としない副作用とされています。

- ネットワークリクエストの送信
- 何かのログの記録

要するに、**ReactがDOMを更新後に追加のコードを実行したい場合**に、クリーンアップを必要としない副作用を使います。

実質、クリーンアップ自体の役割は、残るとメモリリークが起こって挙動を起こす内容のcleanupなので、DOMの更新後に追加コードの実行を行うことは、クリーンアップの性質ではありませんね。

もっとわかりやすい日常の例に例えるなら、クリーンアップが必要ない場合というのは、食事を食べに外食した時に食後の片付けをしなくて良いのと同じで、クリーンアップが必要な場合というのは、自炊して後片付けをする必要があるというのと同じです。

## useEffectが呼び出されるタイミング

副作用フックである `useEffect` が呼び出されるタイミングを理解しておくことは、非常に大切なので、ここで説明しておきます。

 `useEffect` は、毎回のレンダー後に呼び出されます。

今までのReactのイベントサイクルベースで考えると、「マウント」と「更新」という観点で考えてしまいがちになるのですが、 `useEffect` の場合、 **「レンダーの後」** に副作用が起こります。

そのため、副作用関数は、初回のレンダーの時と、更新するたび呼び出されます。

:::message
これはデフォルトでの仕様ですが、カスタマイズもできます。カスタマイズする方法は、後述します。
:::

# クリーンアップを必要とする副作用

チャプター9で、副作用フックの簡易的な使い方を学習した際に実装した、カウンターアプリを使って、視覚的に反映も一緒に見ていきます。

副作用フックで、クリーンアップを必要とする場合を見ていきたいので、少しだけ検証を見やすくするために手を加えています。

```jsx:src/App.js
const [count, setCount] = useState(0);

useEffect(() => {
  console.log('3. 副作用フックの中直下の範囲');
  document.title = `${count} times clicked!`;
  return () => {
    console.log('2. HTMLドキュメントタイトル変更後の範囲 👈 re-render後に実行される');
  };
}, [count]);

console.log('1. render直前の範囲');
return (
  <div className="App">
    <h1>Counter App 🧮</h1>
    <button onClick={() => setCount(count + 1)}>
      +
    </button>
    <button onClick={() => setCount(count - 1)}>
      -
    </button>
    <h3>{count} times clicked!🖱</h3>
  </div>
);
```

アプリケーションが読み込まれただけの状態での反映は、以下です。

![](https://storage.googleapis.com/zenn-user-upload/yi2l44v27j5n1e6qynxj8azjea4m)

1. render直前の範囲
3. 副作用フックの中直下の範囲

3つ `console.log` で出力したい文字列を書き加えていますが、上記の2つだけがアプリケーション読み込み直後では呼び出されていることに着目してください。

では、クリックイベントを実行するとどうなるか見てみます。

![](https://storage.googleapis.com/zenn-user-upload/hl0ttp11na5cacakncth82sf3m1d)

1. render直前の範囲
2. HTMLドキュメントタイトル変更後の範囲 👈 re-render後に実行される
3. 副作用フックの中直下の範囲

「副作用フックの中直下の範囲」が2番目にくるかと思いきや、最も深い `useEffect` スコープ内の「HTMLドキュメントタイトル変更後の範囲 👈 re-render後に実行される」が2番目にきていますね。

これはなぜでしょうか？

まず、 `useEffect` は、レンダーの後に副作用として起こるのでしたね。

なので、アプリケーションが読み込まれた直後も、「レンダー → 副作用」の順で読み込まれます。

ではクリックイベントが発生した時は、なぜ少し変わった読み込まれ方の順になるのでしょうか？

これは、 **フックがJavaScriptのクロージャを活用しているため** です。

## クリーンアップが呼び出されるタイミング