---
title: "React Hooksとは？"
free: true
---

React Hooksとは、**主にはReactのstateをクラスなしで使えるようにするための技法**です。

# React Hooksが使えるバージョン

React 16.8.0からReact Hooksは使えます。

これ以前の古いReactのバージョンではReact Hooksは使用できません。

React HooksをReact 16.8.0以前のプロジェクトで利用するには、プロジェクトのパッケージのアップグレードが必要になります。

アップグレードは、React DOMを含む全てのパッケージの更新が必要です。

推奨されているReactの安定版バージョンでアップグレードをするようにしましょう。

# React Hooksが使われるようになった背景

[React Conf 2018](https://conf2018.reactjs.org/)というカンファレンスで、初めてReact Hooksは発表されました。

「wrapper地獄(wrapper hell)」という現象を解決するために、React Hooksは開発されました。

wrapper地獄(wrapper hell)とは、[レンダープロップ(render props)](https://ja.reactjs.org/docs/render-props.html)や[Higher Order Component(HOC)](https://ja.reactjs.org/docs/higher-order-components.html)が従来のReactでは主流でしたが、これらを使用する場合、コンポーネントの再構成が必要になるので、何層もの階層ができてしまいます。

Reactで開発しているプロジェクトを[React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)を使って検証してみた時に、階層が深くて、検証したいコンポーネントを探すのに苦労した覚えがある人が多いかと思うのですが、それがwrapper地獄(wrapper hell)です。

では、なぜReact Hooksを使うことで、従来のwrapper地獄(wrapper hell)が解決するのでしょうか？

# React Hooksを使うメリット

React Hooksを使うことで、wrapper地獄(wrapper hell)が解決する理由としては、以下が挙げられます。

- stateを使った処理を、コンポーネントの階層構造を変えずに再利用可能
- 複数のコンポーネントでHooksを共有することができる
- stateを管理、予測しやすくする
- state管理ライブラリを使わなくても良くなる

React公式ドキュメントでは、**クラスを使わず、Reactの機能を使えるようにするためにReact Hooksを開発した**と書かれています。

Reactの基本を学習された方であれば、Reactはクラスがベースでできているように思えるほど、頻繁にクラスが出てきますので、このことを聞いて少し驚かれるかもしれません。

しかし、React自体が**クラスによって複雑化されていた**ことを認めているので、**クラスを使わずstateの管理、予測をしやすくする技法というのがReact Hooksのコンセプト**だということが分かりますね。

ただ、だからと言ってReactからクラスが今後削除されるかというと、そうではないので、ご注意ください。

# React Hooksのデメリット

実践の場でも既に浸透はしていますが、それでもまだ比較的新しい技法なので、デメリットがあるとすれば、以下が挙げられるかと思います。

- リソースが少ない
- 使用した開発者による感想や意見がまだ少ない
- 習得前にReactの基本を理解する必要がある
- 習得までに少し時間がかかる

# React Hooksの既存コードとの互換性

React Hooksは既存のコードと併用が可能です。

つまり、既存コードを全てすぐにReact Hooksに移行する必要はないということです。

これは、React公式ドキュメントでも書かれていることで、既存のコードで複雑なコンポーネントを、わざわざ大幅に書き換えてしまうリスクを取る必要はないということになります。

実際、React開発元のFacebookも、Facebook上の既存クラスコンポーネントは書き換える予定はないと断言しているほどです。

:::details FacebookによるReact公式ドキュメント内での抜粋
At Facebook, we have tens of thousands of components written as classes, and we have absolutely no plans to rewrite them. Instead, we are starting to use Hooks in the new code side by side with classes.

[Gradual Adoption Strategy](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy)
:::

React開発元のFacebookがこのように堂々と宣言しているので、今後新しくReactプロジェクトを開発する場合にReact Hooksを取り入れて実装し、既存コードは併用していくのが推奨されていると認識して良いでしょう。