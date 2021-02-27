---
title: "State Hook"
free: true
---

# Hook（フック）とは？

Hook（フック）とは、関数コンポーネントに対して、Reactの機能を「つなげる」ための関数です。

Reactの機能とは、具体的には、stateやライフサイクルなどがありますね。

英語で、「つなげる、接続する」という時に、hook intoと表現するので、その「hook」から名称が来ています。

つまり、**関数コンポーネントと、Reactの既存機能のつなぎ役をする関数がHook**ということになります。

Reactでは、既存（built-in、組み込み）のHookを提供してくれています。

React側で用意をしてくれているHookを、私たちは、ほとんどそのまま使うことができるということですね。

でも、実は、自分で新しくHookを作成することも可能です。

JavaScriptを習得されている方であれば、関数とメソッドの違いに似ていると、気がつかれたかもしれません。

関数は私たちが作成できるのに対し、メソッドはJSに既存で存在する関数で、呼び出すだけで使うことができましたね。

Hookも、もとを辿れば関数ですから、その点がとてもよく似ています。

# useState(State Hook)

さて、Hookには、**useState** という、既存の、いわゆる関数があります。

Hookが関数であることは、先ほど学習をしましたね。

そのことを踏まえると、useStateが既存のbuilt-inの関数であることは、理解がしやすいと思います。

では、どんな関数かというと、**JSのブロックで、React独特の機能、特にstateを使えるようにする役割を持った関数**です。

Reactの基本を学習された方であれば、**Reactは、関数コンポーネントとクラスコンポーネントで構成**されていたことが、記憶に残っているかと思います。

関数コンポーネントのままだと、stateが使えないので、その場合はクラスコンポーネントに書き換えをしていましたね。

ここでHookを使うと、その必要がなくなります。

理由は、そもそも**Hook自体、クラス内では使えないようにできている**ので、**特に深く考える必要なく、関数コンポーネントベースで構成する**ことができます。

関数コンポーネントに構成しておけば、

「これはクラスコンポーネントだからstateで...🌀」

「これは関数コンポーネントだからstateが使えない...💦」

ということを、考えなくても良くなるのです。

そして、**useState**のことを、 **ステートフック（State Hook）** とも言います。

Reactの公式ドキュメントでは、どちらの表現も使われていますので、どちらも**useState**のことを示すと、インプットしておきましょう。

# useState(State Hook)の基本構文

まずは、最もシンプルな構文から見ていきましょう。

```javascript
// useStateをインポート
import React, { useState } from 'react';

// 関数コンポーネントで用意
function 関数名() {
  const [stateValue, setStateValue] = useState(引数);

  return (
    <div>
      <JSX要素 イベント={() => setStateValue(stateValue)}></JSX要素>
    </div>
  );
}
```

少し見慣れない部分があるといえば、以下の部分かと思います。

```javascript
const [stateValue, setStateValue] = useState(引数);
```

まず、 `stateValue` ですが、これは値に応じて私たちが命名することができます。

クラスコンポーネントの時で言う、state内で定義をした、クラスコンポーネント自体が保持するデータ（値）部分とほぼ同じ役割です。

以下の例でいう、 `name` と `id` が該当します。

```javascript
// 省略
constructor() {
  super();
  this.state = {
    // 👇
    name: '',
    id: 0
  }
}

render() {
  // 👇
  const {
    name,
    id
  } = this.state;

  return (
    {/* 省略 */}
  )
}
```

つまり、 `useState` を使った場合は、以下のように書き換えられると言うことになりますね。

```javascript
// useStateをインポート
import React, { useState } from 'react';

// 関数コンポーネントで用意
function 関数名() {
  const [name, setName] = useState(引数);
  const [id, setId] = useState(引数);

  return (
    <div>
      <JSX要素 イベント={() => setName(name)}></JSX要素>
      <JSX要素 イベント={() => setId(id)}></JSX要素>
    </div>
  );
}
```

ここで勘の良い方は気がついたかもしれません。

 `setStateValue` という構造は、クラスコンポーネントの時の、 `this.setState` に非常に似ていますね.

クラスコンポーネント内の `this.setState` は、簡潔に言うと、propsの上書きを行うものでしたが、State Hookの場合、 **新しいstateが、元のものと統合されない** という違いがあるので、全く同じものではないので、注意しましょう。

 `useState` と `this.state` の違いについては、この先のチャプターで解説をします。

# Hookの後方互換性