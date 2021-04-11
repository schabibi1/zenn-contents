---
title: "React Hooksのルール"
---

# React Hooksのルール

さて、これまでReact Hooksで頻出するメインの技法について習得をしてきました。

State Hookと副作用フック（Effect Hook）を学習したときには、React Hooksの細かいルールについてはあまり触れていません。

ここでは、State Hookと副作用フック（Effect Hook）を十分理解した上で、React Hooksのルールを解説していきます。

# React Hooksを呼び出すのは、トップレベルだけ

React Hooksは、条件分岐やループ内に呼び出すことはできない決まりになっています。

ネストされた関数内でも呼び出せません。

これは、React Hooksがトップレベルでのみ呼び出されるように決まっているからです。