---
title: "Vue.jsシリーズ: Vue Composition APIへようこそ！"
free: true
---

本書を手に取ってくださり、ありがとうございます。

この本は、これから新しくVue Composition APIの学習を始められる方に向けて、実践レベルのVueを習得することを目標に、React Hooksの基本から導入、応用までを習得することを目的として、作成しています。

この教材はテックスキル、知見、経験シェアの無料オンラインコミュニティ | [Lilac(ライレック)](https://note.com/frontendlifeinde/m/m9b8feda1d547)」の無料教材です。

この本は、VueシリーズのVue Composition API編です。
本書の前半半分のチャプターは、無料でお読みいただけます。

マークアップ言語シリーズの本や、そのほかのシリーズの本は、[こちら](https://zenn.dev/arisa_dev)よりご覧いただけます。

# 本書の特徴

- 動画ソースでは難しい、特定の内容のリーチがしやすい
- 独学向けソースでは省略されがちな、細かい設定や説明が読める
- 専門用語には、わかりやすい例を用いた解説がついている
- 視覚的資料と、わかりやすい文章で、MDNなどの公式ドキュメントでは理解がしづらい内容もカバー
- 1冊のボリュームが軽いので、読み切りやすい
- 動画ソースでは難しい、最新の内容も随時アップデート
- 全て公式ドキュメントに忠実に基づいた内容

# 本書の対象者

- Vueの学習をしたことのある方
- 新しくVue Composition APIを学習したい人
- JavaScriptを習得し終え、Vueの基本を習得し終えた人
- 実践的なVueを習得したい人
- Vueの公式ドキュメントだけでは理解が難しいと感じた方

# 本書を読むために必要な環境

- テキストエディタの導入（Visual Studio Code推奨）

Visual Studio Codeの導入方法は、こちらの[「マークアップ言語シリーズ: Lesson 0 Visual Studio Codeを導入してみよう」](https://zenn.dev/arisa_dev/books/markup-lesson0)で無料で読むことができます。
15分-30分前後で設定できる内容ですので、ぜひ、本書に取り組む前に導入が必要であれば活用してください。

- 本書のテキスト内、ソースコード

// TODO: 以下最後に置き換え

~~以下のリンクより、ダウンロードすることができます。~~

~~「Code」という緑のボタンをクリックすると、「Download zip」という選択肢があり、ダウンロードできます。~~

![github-download-zip](https://storage.googleapis.com/zenn-user-upload/ka8fydr34z9opq7lh7ismgsacnaf)

~~該当チャプターに、該当のソースコードが入っているフォルダ名の指定があります。~~

~~実際に皆さんの環境でも、手を動かしながら反映を見る必要があるものを、このソースコードフォルダ内にまとめています。~~

> [本書のテキスト内ソースコード](https://github.com/schabibi1/zenn-book-challenges)

# 本書の環境

- OS: Linux(Windows WSL)
- テキストエディタ: Jetbrains WebStorm
- ブラウザ: Google Chrome

# 作者プロフィール

### 著者

Mikihiro Saito

![profile_img](https://lh3.googleusercontent.com/a-/AOh14GhSwePIlBZTw0_8xl4WAXVJ4dBFMN6tQuc4r60Vhw=s96-c)

- Twitter: [@bohol_engineer](https://twitter.com/bohol_engineer)
- Github: [@mikinovation](https://github.com/mikinovation)

### 職業
- Web Front Developer

### 得意分野
- JavaScript(Typescript)
- React
- Angular
- Vue

### 経歴
フィリピンのセブ島、ボホール島在住エンジニア
2017年大学2年の時代にプログラミングを勉強し始め、エンジニアとして現在4年目
2社のインターンを経て、フリーランスとしては3年目

web開発、デスクトップアプリケーション開発を業務委託で受託開発を行っている

今まで作ってきたものは

- 電子カルテ
- BtoBの部品や資材の発注システム
- BtoCの人材紹介システム
- BtoBの人材育成システム
- リモートワーク支援のデスクトップアプリケーション開発

等のプロジェクトに携わってきました

### 趣味

- ゲーム
- 自然の中でぶらぶら

家の庭にはバナナやマンゴーが生えていたり、歩いて5分で海やマングローブが生えているような自然豊かな場所に住んでいます