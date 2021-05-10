---
title: "カスタムフック"
---

# カスタムフック（独自フック）とは？

 **カスタムフック（独自フック）** とは、その名前の通り、自分で独自のカスタマイズをしたフックを作成したものです。

コンポーネントからフックの構造自体を切り取り、再利用可能な関数を作ることができます。

チャプター10の練習問題2で実装した、ショッピングカートアプリをここで振り返ってみたいと思います。

Reactの基本をマスターしている方であれば、このアプリケーションがコンポーネントごとにコード分割（Code-Splitting）をしていないことに、疑問を持たれたかもしれません。

あるいは、実装中に

「State Hookや副作用フック（Effect Hook）は、コード分割する時に、どうしたらフックを共有できるのだろう？」

と、悩まれたかもしれません。

まさにその疑問に答えるのが、カスタムフック（独自フック）です。

# これまでの方法

React Hooksが普及する前は、以下の方法がありました。

- レンダープロップ（Render Prop）
- 高階コンポーネント（Higher-Order Component, HOC）

これらの方法を使い、stateを持っている構造を、コンポーネント間で共有することができました。

これをReact Hooksで、カスタムフック（独自フック）を使って実現していきます。

# カスタムフック（独自フック）の抽出

コンポーネントとReact Hooksは、どちらも元を辿れば関数です。

JavaScriptの関数間では、あるロジック/構造を共有したい場合、別の関数に抽出します。

この性質を利用して、カスタムフック（独自フック）の抽出をしていきたいと思います。

カスタムフックの基本の構造は、以下です。

- 名称が `use` で始まる
- 他のフックを呼び出せるJavaScriptの関数である
- トップレベルで呼び出している

つまり、ものすごくシンプルに言うと、 `use何々` と命名することで、それはカスタムフックになるということです。

その上で他のフックを呼び出せるJavaScriptの関数であれば、カスタムフックである条件は揃います。

例えば、チャットアプリで以下の機能があるとしましょう。

- 機能1: 友達がオンラインか、オフラインかを示すステータスの表示をする（FriendStatus）
- 機能2: 連絡先リストに、オンラインのユーザーを緑で示す表示をする（FriendListItem）

それぞれの機能でコンポーネントを分けているとします。

```jsx:src/FriendStatus.js
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [online, setOnline] = useState(null);

  useEffect(() => {
    // 副作用
    function changeStatus(status) {
      setOnline(status.online);
    }

    ChatAPI.subscribeStatus(props.friend.id, changeStatus);

    // クリーンアップ関数
    return () => {
      ChatAPI.unsbscribeStatus(props.friend.id, changeStatus);
    };
  });

  if (online === null) return 'Loading...';

  return online ? 'online' : 'offline';
}
```

カスタムフック（独自フック）を使わない場合、 `FriendListItem` コンポーネントに上記のState Hookと副作用フックをコピー&ペーストしても実現できないことはないですが、以下のように重複を招いてしまいます。

```diff jsx:src/FriendListItem.js
import React, { useState, useEffect } from 'react';

function FriendListItem(props) {
+  const [online, setOnline] = useState(null);

+  useEffect(() => {
+    // 副作用
+    function changeStatus(status) {
+      setOnline(status.online);
+    }
+
+    ChatAPI.subscribeStatus(props.friend.id, changeStatus);
+
+    // クリーンアップ関数
+    return () => {
+      ChatAPI.unsbscribeStatus(props.friend.id, changeStatus);
+    };
+  });

  return (
    <ul>
      <li style={{ color: online ? 'green' : 'gray' }}>
        {props.friend.name}
      </li>
    </ul>
  );
}
```

プログラミングをする上で、以下の3つの項目は、常に意識をしたいところです。

1. 重複を避ける
2. 再利用性の高さを意識する
3. 可読性の高さを意識する

そのことを踏まえると、上記の書き方では非効率ということになりますので、その代わりに、 `FriendStatus` と `FriendListItem` コンポーネントの双方で、State Hookと副作用フックを共有していきます。

まずは `use何々` と命名することからカスタムフック（独自フック）を抽出することができますので、 `FriendStatus` 関数コンポーネントからState Hookと副作用フック（Effect Hook）部分をカットします。

そして `useFriendStatus` と命名したコンポーネントファイルを生成し、 `useFriendStatus` と関数も命名します。

```jsx:src/useFriendStatus.js
// 👇 関数名にuseを追加
// 👇 引数idの追加: 友達がオンラインかどうかを返すための引数
function useFriendStatus(userId) {
  const [online, setOnline] = useState(null);

  useEffect(() => {
    // 副作用

    // クリーンアップ関数
    return () => {
      // 処理内容
    }
  });

  // レンダー
  return online;
}
```

新しく加えられたことは2つです。

1. useを先頭につけて、`useFriendStatus` と命名
2. 友達がオンラインかどうかを返すための引数 `userId` を `props` の代わりに格納

引数ですが、カスタムフック（独自フック）は、 **何を引数として受け取り、何を返すのかということを、独自に決める** ことができます。

これはReactのコンポーネントと少し違う点です。

逆に、この点はJavaScriptの通常の関数と共通する部分です。

JavaScriptの関数も、何を引数として持つか、そして何を返すのかということは、関数で独自に決めて良い構造でしたね。

それに基づいて、引数を `userId` としたということです。

さて、ここまでがカスタムフック（独自フック）の抽出です。

いよいよここからカスタムフック（独自フック）を使っていきましょう。

# カスタムフック（独自フック）を使う

抽出の作業は、さほど難しいものではなかったと思います。

実はカスタムフックを使う作業も、そこまで難しくはありません。

```jsx:src/FriendStatus.js
function FriendStatus(props) {
  // 👇 カスタムフック useFriendStatusを呼び出す
  const online = useFriendStatus(props.friend.id);

  if (online === null) return 'Loading...';

  return online ? 'online' : 'offline';
}
```

```jsx:src/FriendListItem.js
function FriendListItem(props) {
  // 👇 カスタムフック useFriendStatusを呼び出す
  const online = useFriendStatus(props.friend.id);

  if (online === null) return 'Loading...';

  return (
    <ul>
      <li style={{ color: online ? 'green' : 'gray' }}>
        {props.friend.name}
      </li>
    </ul>
  );
}
```

いかがでしょうか？

重複を避けることができた上に、2つのコンポーネント間でState Hookと副作用フック（Effect Hook）が、非常に簡単に共有できました。

先のチャプターで、カスタムフック（独自フック）の書き換えをする練習問題を用意していますので、いますぐに書ける気がしなくても、何をどうすれば良いのかが今は理解できれば問題ありません。

:::message
カスタムフックは、stateの共有ではなく、stateを含む構造を共有するためのものです。
stateを共有しているように見えるのですが、厳密にはコンポーネントごとにstateや副作用フックは分離しています。
:::

# フック間での情報の受け渡し方

さて、カスタムフックの抽出方法と使い方についてここまで学習してきました。

今度は、フック間で情報を受け渡す方法を学習します。

先ほどの簡易的なチャットアプリを使って説明していきます。

チャット受信者選択画面のコンポーネントを、今回は新しく追加します。

機能としては以下です。

- 機能3: 選択している友達が、オンラインかどうかを表示する

```jsx:src/RecipientPicker.js
const friends = [
  { id: 1, name: 'Ayaka' },
  { id: 2, name: 'Jen' },
  { id: 3, name: 'Perry' }
];

function RecipientPicker() {
  // 👇 recipientIDに、選択中の友達IDを格納
  const [recipientID, setRecipientID] = useState(1);
  // 👇 select要素内で、選択される友達が変わるごとに、選択される友達IDを更新
  const recipientOnline = userFriendStatus(recipientID);

  return (
    <>
      <Status color={ recipientOnline ? 'green' : 'gray' } />
      <select
        value={ recipientID }
        onChange={ e => setRecipientID(Number(e.target.value)) }>
        {friends.map(friend => {
          <option
            key={ friend.id }
            value={ friend.id }>
            { friend.name }
          </option>
        })}
      </select>
    </>
  );
}
```

選択中の友達のIDを、 `recipientID` というstateに格納をします。

そうすると、select要素内で別の友達IDが選択された場合、選択中の友達IDを随時更新してくれます。

State Hookは、 `recipientID` state（変数）の最新の値を返すので、カスタムフックの `useFriendStatus` に引数として渡します。

そうすることにより、選択中の友達がオンラインかどうかが、リアルタイムで更新され、把握できます。