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

