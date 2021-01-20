---
title: "[webpack] Cannot find module 'babel-eslint' が出たら"
emoji: "🕵️‍♂️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["webpack", "javascript", "babel"]
published: true
---

# エラーの概要

以下の環境でエラーが出てました。

webpackがv5にアップデートされてから吐くようになった模様。

```javascript
  "devDependencies": {
    "babel-core": "^6.26.3",
    "babel-jest": "^23.2.0",
    "babel-preset-env": "^1.7.0",
    "css-loader": "^0.28.11",
    "eslint": "^5.0.1",
    "eslint-config-airbnb": "17.0.0",
    "eslint-loader": "^2.0.0",
    "eslint-plugin-import": "^2.12.0",
    "eslint-plugin-jsx-a11y": "^6.0.3",
    "eslint-plugin-react": "^7.9.1",
    "jest": "^23.2.0",
    "jest-localstorage-mock": "^2.2.0",
    "node-sass": "^4.9.0",
    "sass-loader": "^7.0.3",
    "style-loader": "^0.21.0",
    "webpack": "^4.12.1",
    "webpack-cli": "^3.0.8",
    "webpack-dev-server": "^3.1.4"
  },
  "dependencies": {
    "moment": "^2.22.2"
  }
```

```
Error: Cannot find module 'babel-eslint'
```

で、足りないと言われたbabel-eslintをインストールしたら、以下のログが今度は出てきました。

```
gyp ERR! stack Error: `make` failed with exit code: 2
```

ちょっとはまったんですが、単刀直入に言うと、webpackのconfigを合わせないといけなかったようです。

# 事前に理解しておきたいこと / 注釈

webpack v5が2020年終盤頃にリリースされ、そこからconfig設定で、まあまあwebpackの公式リポジトリissueを賑わせていました。

このプロジェクトの場合、webpackのバージョンは現状を維持したかったので、v4系ですが、configを合わせる必要があった感じです。

# 具体的な解決方法

1. `$ rm package-lock.json && rm -rf node_modules && rm -rf ~/.node-gyp` でpackage-lock.json、/node_modules/、 ~/.node-gyp/ フォルダの削除
2. `$ npm install` でパッケージを一括インストールし直す（yarnは `$ yarn upgrade` ）
3. webpack.config.jsファイルのconfigを以下のように変更
4. `$ npm install --save-dev babel-eslint` でbabel-eslintインストール（yarnは `$ yarn add --dev babel-eslint` ）
5. `$ npm run dev-server` 実行（yarnは `$ yarn dev-server` ）
6. 解決✨

### Before

```javascript:webpack.config.js
module.exports = {
  // other configs
  module: {
    {
      test: /\.(js)$/,
      exclude: /node_modules/,
      loader: 'eslint-loader',
      options: {
        // eslint options
      },
    }],
  }
}
```

```javascript:webpack.config.js
module.exports = {
  // other configs
  module: {
    {
      test: /\.(js)$/,
      exclude: /node_modules/,
      // loader: 'eslint-loader',
      use: [
        {
          loader: "eslint-loader",
          query: {
            name: 'bundle.js'
        }
        }
      ]
      // options: {
      //   // eslint options
      // },
    }],
  }
}
```

これでエラーログが消え、無事コンパイルが完了です。

> 参考ソース
- [node.js/node-gypリポジトリ: gyp ERR! stack Error: `make` failed with exit code: 2 #1694](https://github.com/nodejs/node-gyp/issues/1694)
- [babel/babel-eslintリポジトリ](https://github.com/babel/babel-eslint)
- [webpack公式ドキュメント: Rule.use](https://webpack.js.org/configuration/module/#ruleuse)
- [webpack/webpackリポジトリ: Error: options/query provided without loader. Webpack 2.2.0-rc.3 #3645](https://github.com/webpack/webpack/issues/3645)