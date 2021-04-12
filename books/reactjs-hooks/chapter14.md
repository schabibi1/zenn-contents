---
title: "練習問題3"
---

# オンラインショップアプリをカスタムフックに書き換えよう！（所要時間の目安: 15分〜30分）

練習問題2のチャプターで実装をした、オンラインショップの注文画面アプリを、カスタムフック（独自フック）を使って書き換えてみましょう。

以下のLilac（ライレック）教材ソースコードのリストにあるスターターリポジトリ、[「React Hooks: カスタムフック、オンラインショップの注文画面練習問題3 スターター」](https://github.com/schabibi1/zenn-book-challenges/tree/main/custom-hook-store-starter)をforkして取り組んでください。

> [スターターフォルダ](https://github.com/schabibi1/zenn-book-challenges)

# 要件

以下の要件をヒントに、機能設計、遷移設計を作り、アプリケーション実装に取り組みましょう。

1. State Hookと副作用フックを、カスタムフックとして別の関数コンポーネントに抽出する
2. 必要に応じて、コード分割（Code-Splitting）をする
3. 必要に応じて、情報の受け渡しをフック間で行う

ワイヤーフレーム（画面設計）は、練習問題2と同様です。

![](https://storage.googleapis.com/zenn-user-upload/kwgqw6ej2v0yse5scl0y16z6wh8w)