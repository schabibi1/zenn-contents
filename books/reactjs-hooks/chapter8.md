---
title: "副作用フックの簡易的な使い方"
free: true
---

# カウンターアプリの、HTMLドキュメントタイトルを変化させよう！

副作用フック（Effect Hook）の基本構文と概念が理解できたところで、前のチャプターで途中まで取り組んでいた、カウンターアプリHTMLドキュメントタイトルを、変化させていきたいと思います。

# 副作用フック（Effect Hook）の読み込み

まず、State Hookで行ったように、副作用フック（Effect Hook）でも `useEffect` をインポートしましょう。

```diff jsx:src/App.js
+ import React, { useState, useEffect } from 'react';
import './App.css';

function App() {
  const [count, setCount] = useState(0);

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
}

export default App;
```

 `useEffect` のインポートができたら、 `useEffect` を呼びましょう。

ここで意識したいことがあります。

 `useEffect` は `componentDidMount` や `componentDidUpdate` と似ていることを意識して呼び出します。

```diff jsx:src/App.js
import React, { useState, useEffect } from 'react';
import './App.css';

function App() {
  const [count, setCount] = useState(0);

+  useEffect(() => {
+    // DOMをブラウザAPIを使ってアップデート
+    document.title = `${count} times clicked!`;
+  }, [count]);

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
}

export default App;
```

 `document.title` は、HTMLドキュメントのタイトル要素にアクセスをするDOMの記述です。

 `useEffect` の第1引数に `callback` を格納し、第2引数にState Hookで用意をしたcount stateを用意します。

 `useEffect` を呼ぶことで、DOMに更新を反映させた後、私たちが定義する副作用関数を実行するようReactに指示をします。

3つあった副作用フックの基本構文パターンで、パターン1と2、どちらが良いか迷う場合もあるかと思いますが、前のチャプターのカフェ常連客の例を考えてみると、パターン2が適していることがわかるかと思います。

反映結果をブラウザで確認すると、HTMLドキュメントのタイトル部分も、クリックイベントと連動して加算されたり、減算されたりするようになりました。

![](https://storage.googleapis.com/zenn-user-upload/aacz0cm7hkxgosh0484cbw0ujagp)

これでカウンターアプリのHTMLドキュメントタイトルを、クリックイベントと連動させる処理が完成しました。

:::message
副作用は、コンポーネント内で宣言されるため、propsやstateにアクセスすることができます。
そのため第2引数にstateやpropを用いることができます。
:::