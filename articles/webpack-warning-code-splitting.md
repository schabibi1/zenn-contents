---
title: "[webpack] WARNING in asset size limit、と出たときの対処法"
emoji: "🎍"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["webpack", "javascript"]
published: true
---

# エラーの概要

webpack 5で、こんなエラーが出たことがあります。

```javascript
WARNING in asset size limit: The following asset(s) exceed the recommended size limit (97.7 KiB).
This can impact web performance.
```

2つか3つくらいwarningのログが出るのですが、コンパイルすると、こんな感じで全体のログが出ます。

![](https://storage.googleapis.com/zenn-user-upload/trop6ffot2jpqvonvy23xdtu7b8g)

このプロジェクトでは、lodashのパッケージをインポートしているのだけど、パッケージで不必要なものも丸ごと読み込んでしまっているらしい。

言われている通り、web全体の動き（イベント発火時の処理など）はもっさりする。

うまく規定サイズ内に納めてコンパイルさせる方法が、公式ドキュメントにあったので、まとめます。

# 事前に理解しておきたいこと

> [webpack公式ドキュメント: https://webpack.js.org/guides/code-splitting/](https://webpack.js.org/guides/code-splitting/)

ここにある[「Dynamic Imports」](https://webpack.js.org/guides/code-splitting/#dynamic-imports)の項目へ直行。

まず、書いてあることとしては、

> Two similar techniques are supported by webpack when it comes to dynamic code splitting. The first and recommended approach is to use the import() syntax that conforms to the ECMAScript proposal for dynamic imports. The legacy, webpack-specific approach is to use require.ensure. Let's try using the first of these two approaches...

2つ方法があって、オススメは `import()` を使用する方法とあるので、素直に従います。

[webpackのimport()](https://webpack.js.org/api/module-methods/#import-1)についてはこちら。

:::message
webpackの `import()` はPromiseを呼び出すため、IE11などの古いブラウザでは、es6-promiseか、promise-polyfillなどを使って対処してくださいとのこと
:::

# 具体的な解決方法

公式ドキュメントにあるように、以下のソースコードファイルを編集します。

パスなどは適宜変更します。

```javascript
your-project
|- package.json
|- webpack.config.js
|- /dist
|- /src
  |- index.js
|- /node_modules
```

```javascript:webpack.config.js
const path = require('path');
 
module.exports = {
  mode: 'development',
  entry: {
    index: './src/index.js',
  },
  output: {
    filename: '[name].bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

```javascript:src/index.js
// import _ from 'lodash';

function getComponent() {
 return import('lodash')
   .then(({ default: _ }) => {
     const element = document.createElement('div');

     element.innerHTML = _.join(['Hello', 'webpack'], ' ');

    return element;
   })
   .catch((error) => 'An error occurred while loading the component');
}

getComponent().then((component) => {
  document.body.appendChild(component);
});
```

これでlodashのパッケージが別のバンドルに分離できたので、上記の2, 3個出ていたwarningとはおさらばです。

Promiseを呼び出すため、 Async/awaitにも書き換えできます。