---
title: "練習問題2"
free: true
---

# オンラインショップの注文画面を実装しよう！（所要時間の目安: 3分〜5分）

先ほどのカウンターアプリで練習したことを元に、オンラインショップの注文画面を実装してみましょう。

# 要件

以下の要件をヒントに、機能設計、遷移設計を作り、アプリケーション実装に取り組みましょう。

1. +ボタン: 1つずつ商品の個数が加算
2. -ボタン: 1つずつ商品の個数が減算
3. カート内商品の個数を表示: 加算、減算に連動した表示
4. 合計金額の表示: 加算、減算に連動した表示
5. スタイリングにはCSS in JSライブラリ、emotion.jsのStyled Componentsを使用
6. `@emotion/react` `@emotion/styled` `@emotion/babel-plugin` を導入
7. `.babelrc` のコンフィグファイル作成

> [emotion.js公式ドキュメント](https://emotion.sh/docs/install)

:::message
それぞれのバージョンは以下です。
`"@emotion/react": "^11.1.5"`
`"@emotion/styled": "^11.1.5"`
`"@emotion/babel-plugin": "^11.2.0"`
:::

:::message
ロジックの分離、再利用は先のチャプターで学習します。React Hooksの基礎を学習するため、今回はApp.jsに全て記述します。
:::

ワイヤーフレーム（画面設計）は、以下に用意しています。

![](https://storage.googleapis.com/zenn-user-upload/kwgqw6ej2v0yse5scl0y16z6wh8w)

遷移設計も、Adobe XDで作ってみましょう。

機能設計の完成見本は、以下を開くと見ることができます。

:::message alert
まずは取り組んでから機能設計と遷移設計の完成見本を見ましょう。
機能設計に必要な技法も書いておくと、実装しやすくなります。
:::

:::details 機能設計の完成見本
**必要な技法**

1. State Hookを使う
2. 副作用フック（Effect Hook）を使う

| 必要項目 | 機能詳細 |
| ---- | ---- |
| State Hook | 商品の個数カウント |
| 副作用フック（Effect Hook） | 商品個数カウントと連動した、カートコンポーネントDOMのアップデート |
| +ボタン | 1ずつ加算 |
| -ボタン | 1ずつ減算 |
| カート内商品の個数を表示 | 副作用フックで実装 |
| 合計金額の表示 | 副作用フックで実装 |
:::

遷移設計の完成見本は、こちらから見ることができます。

> [Adobe XDで作成した遷移設計プロトタイプ](https://xd.adobe.com/view/9a17c8f2-e2a1-491a-5b29-20671cf0e70e-ec26/)

https://dmitripavlutin.com/react-useeffect-explanation/