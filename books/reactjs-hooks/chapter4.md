---
title: "State Hookの簡易的な使い方"
free: true
---

# State Hookを使って、カウンターアプリを実装しよう！

では、いよいよカウンターアプリを実装していきます。

機能設計と、画面、遷移設計（ワイヤーフレーム）をチャプター3で作成していますので、そちらを以下で再度ざっと見直しながら取り組んでみましょう。

### 機能設計（機能仕様）

| アプリ概要 | 必要な機能(機能設計) |
| ---- | ---- |
| 数値カウントアプリ | クリックイベントが発生するたび、1ずつ数値が加算されて増える |

この簡易的な機能設計から考えられる、使用する可能性が高い技法は以下でしたね。

### 使用が予測される技法

1. イベント
2. React Hooks

# 開発環境のセットアップ

まずは `create-react-app` を使用し、開発環境を整えます。

> React公式ドキュメント: [「Create React App」](https://ja.reactjs.org/docs/create-a-new-react-app.html#create-react-app)

```shell
$ npx create-react-app state-hook-counter-app
```

:::message
Nodeバージョンは、v10.16以上、npmバージョンは v5.6以上の環境が必要です。
バージョンがこれより低い場合は、推奨版をNode公式ドキュメントで確認し、Nodeバージョン管理ツール（nなど）でアップグレードをしましょう。
:::

![](https://storage.googleapis.com/zenn-user-upload/4r8zs019fjh7wm90os61y9rw5uo8)

> [Node公式ドキュメント、インストール](https://nodejs.org/en/)

> [Node バージョンマネージャー、n](https://github.com/tj/n)

:::message
本教材では、以下のNodeバージョンとnpmバージョンです。
:::

```js
{
  node: "14.16.0",
  npm: "6.4.11"
}
```

 `create-react-app` を使って開発環境が整ったら、プロジェクトをローカル環境で立ち上げましょう。

```shell
$ cd state-hook-counter-app
$ yarn start
```

![](https://storage.googleapis.com/zenn-user-upload/hrv6cfic6t3zmq454v3tbyhlibd5)

上記の画面が表示され、立ち上がったら、プロジェクトディレクトリの `src/App.js` ファイルを開きます。

以下のデフォルトソースコードの記述があることを確認します。

```jsx:src/App.js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

カウンターアプリを開発するため、不要な記述は以下のように削除、もしくは編集します。

```diff jsx:src/App.js
- import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
-      <header className="App-header">
-        <img src={logo} className="App-logo" alt="logo" />
-        <p>
-          Edit <code>src/App.js</code> and save to reload.
-        </p>
-        <a
-          className="App-link"
-          href="https://reactjs.org"
-          target="_blank"
-          rel="noopener noreferrer"
-        >
-          Learn React
-        </a>
-      </header>
+     HEY👋
    </div>
  );
}

export default App;
```

仮に入れた「HEY👋」という文字列がアウトプットされていることが確認できるかと思います。

![hey](https://storage.googleapis.com/zenn-user-upload/7yd5miy51eoul2ydupejgcsl6mt1)

# State Hookの読み込み

では、State Hookを使用するために、 `useState` をインポートしましょう。

```diff jsx:src/App.js
+ import React, { useState } from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
      HEY👋
    </div>
  );
}

export default App;
```

Hookを使い、stateを用意します。

カウントを0から始めたいので、useStateの引数には、0を格納します。

```diff jsx:src/App.js
import React, { useState } from 'react';
import './App.css';

function App() {
+  const [count, setCount] = useState(0);

  return (
    <div className="App">
      HEY👋
    </div>
  );
}

export default App;
```

クリックイベントによって、数値の加算を1ずつ行いたいので、ボタン要素をJSX内に用意します。

クリックイベントの結果、要するに1ずつ加算された結果をブラウザに表示したいので、文字列で出力させる記述も書き加えます。

```diff jsx:src/App.js
import React, { useState } from 'react';
import './App.css';

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="App">
-      HEY👋
+      <h1>Counter App 🧮</h1>
+      <button>+</button>
+      <h3>{count} times clicked!🖱</h3>
    </div>
  );
}

export default App;
```

この時点でブラウザの反映を確認してみると、stateのcount初期値0が、既に返り値として返されていることが確認できます。

![](https://storage.googleapis.com/zenn-user-upload/vzx3bi16k3vdbf3hx4gzzvlr5faz)

# クリックイベントとState Hookを紐付ける

今の状態だと、ボタン要素をクリックしてもクリックイベントの反応がないので、イベントとState Hookの紐付けを行います。

まずは、クリックイベント発生時に、イベントがトリガーされているかどうかの検証を行います。

:::message
**検証のコツ:**
構造がシンプルなうちにイベントがトリガーされているかを検証すると、構造が複雑化する前に、イベントトリガーにエラーの原因が潜んでいないことが断言できます。要因を絞り込みやすくするコツです。
:::

```diff jsx:src/App.js
import React, { useState } from 'react';
import './App.css';

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="App">
      <h1>Counter App 🧮</h1>
+     <button onClick={() => console.log('clicked!🖱')}>+</button>
     <h3>{count} times clicked!🖱</h3>
    </div>
  );
}

export default App;
```

![](https://storage.googleapis.com/zenn-user-upload/b5b6ozgy600r9nyy8fi4dttqhszn)

ブラウザdev toolのコンソールに、クリックした回数だけイベントが発生して、「clicked!🖱」の文字列が出力されていることが確認できますね。

では、1ずつstateのcountに、加算をしていく記述をしていきたいと思います。

チャプター4のState Hookの基本構文を確認しながら書いていきましょう。

```diff jsx:src/App.js
import React, { useState } from 'react';
import './App.css';

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="App">
      <h1>Counter App 🧮</h1>
+     <button onClick={() => setCount(count + 1)}>+</button>
      <h3>{count} times clicked!🖱</h3>
    </div>
  );
}

export default App;
```

![](https://storage.googleapis.com/zenn-user-upload/rrsveqqxo9m8pp3p2m5400pss6d1)

クリックイベントが発生した回数分、1ずつstateのcountが加算されていることが確認できます。

カウンターアプリが、とても簡単にできましたね。