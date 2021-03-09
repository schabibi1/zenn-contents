---
title: "React.jsシリーズ: React Hooksへようこそ！"
free: true
---

本書を手に取ってくださり、ありがとうございます。

この本は、これから新しくReact Hooksの学習を始められる方に向けて、実践レベルのReactを習得することを目標に、React Hooksの基本から導入、応用までを習得することを目的として、作成しています。

この教材は、私が現在開発を手掛けていて、近日中にリリース予定の「オーダーメイド感覚プログラミング学習サービス | [Lilac(ライレック)](https://note.com/frontendlifeinde/m/m9b8feda1d547)」で提供をする教材の、先行販売版です。

[Lilac(ライレック)](https://note.com/frontendlifeinde/m/m9b8feda1d547)では、以下の2つの方法から、それぞれお好きなプランでご利用いただくことのできる、学習方法のパーソナライズに特化した、オンラインプログラミング学習サービスです。

1. **Textbook プラン:** 必要なトピックの教材のみの購入利用
2. **Tutoring プラン:** 全教材アクセス権 + 個別メンターArisaによる学習サポート + 案件受注&納品やポートフォリオ作成などのサポート

この本は、ReactシリーズのReact Hooks編です。
本書の前半半分のチャプターは、無料でお読みいただけます。

マークアップ言語シリーズの本や、そのほかのシリーズの本は、私の[Zennプロフィール](https://zenn.dev/arisa_dev)よりご覧いただけます。

# 本書の特徴

- 動画ソースでは難しい、特定の内容のリーチがしやすい
- 独学向けソースでは省略されがちな、細かい設定や説明が読める
- 専門用語には、わかりやすい例を用いた解説がついている
- 視覚的資料と、わかりやすい文章で、MDNなどの公式ドキュメントでは理解がしづらい内容もカバー
- 1冊のボリュームが軽いので、読み切りやすい
- 動画ソースでは難しい、最新の内容も随時アップデート
- 全て公式ドキュメントに忠実に基づいた内容

# 本書の対象者

- Reactの学習をしたことのある方
- 新しくReact Hooksを学習したい人
- JavaScriptを習得し終え、Reactの基本を習得し終えた人
- 実践的なReactを習得したい人
- Reactの公式ドキュメントだけでは理解が難しいと感じた方

# 本書を読むために必要な環境

- テキストエディタの導入（Visual Studio Code推奨）

Visual Studio Codeの導入方法は、こちらの[「マークアップ言語シリーズ: Lesson 0 Visual Studio Codeを導入してみよう」](https://zenn.dev/arisa_dev/books/markup-lesson0)で無料で読むことができます。
15分-30分前後で設定できる内容ですので、ぜひ、本書に取り組む前に導入が必要であれば活用してください。

- 本書のテキスト内、ソースコード

以下のリンクより、ダウンロードすることができます。

「Code」という緑のボタンをクリックすると、「Download zip」という選択肢があり、ダウンロードできます。

![github-download-zip](https://storage.googleapis.com/zenn-user-upload/ka8fydr34z9opq7lh7ismgsacnaf)

該当チャプターに、該当のソースコードが入っているフォルダ名の指定があります。

実際に皆さんの環境でも、手を動かしながら反映を見る必要があるものを、このソースコードフォルダ内にまとめています。

> [本書のテキスト内ソースコード](https://github.com/schabibi1/zenn-book-challenges)

# 本書の環境

- OS: macOS
- テキストエディタ: Visual Studio Code
- ブラウザ: Google Chrome Canary

# 作者プロフィール

### 著者

Arisa Fukuzaki

![profile_img](https://storage.googleapis.com/zenn-user-upload/u7ka3507985si7cc9s047g7rt4gx)

- Twitter: [@arisa_dev](https://twitter.com/arisa_dev)
- ブログ: [Aiki x Developer](https://aiki-developer.com)
- note: [https://note.com/frontendlifeinde](https://note.com/frontendlifeinde)
- Podcast（毎週水曜日更新）: [アノニマスですけど何か](https://note.com/frontendlifeinde/m/m14ff18669c56)

### 職業
- フリーランス フルスタックエンジニア
- フロントエンド開発個人講師（マンツーマン学習サポートをご希望の方は[こちら](https://aiki-developer.com/contact)まで）
- Lilac 運営&開発中

### 得意分野
- JavaScript
- React.js
- Gatsby.js
- React Native

### 経歴
ドイツに2017年から移住したフリーランスのフルスタックエンジニア。
新卒でエミレーツ航空で客室乗務員として勤め、在籍中に独学でプログラミングを学習し、2017年よりエンジニアとして活動を始める。

フロントエンドから入り、web開発、webアプリケーション開発、モバイルアプリ開発を行っている。

2018年より、現在も個人でフロントエンド開発をマンツーマンで教える講師活動をしている。
40人以上マンツーマンで教え、国内企業就職者、海外企業就職者、フリーランスのエンジニアを輩出した実績あり。

講師の活動の傍ら、テキスト教材販売と、マンツーマンプログラミング学習サポート提供のLilac(ライレック)を開発中。

[Gatsby.js](https://www.gatsbyjs.com/)公式オンラインイベント、[GatsbyConf 2021](https://gatsbyconf.com/)で登壇経験あり。

- [GatsbyConf 2021: 登壇内容](https://gatsbyconf.com/event/finding-my-developer-happy-path-with-gatsby-x-contentful/)
- [Gatsby.js: 登壇前インタビュー記事](https://www.gatsbyjs.com/blog/gatsbyconf-qa-arisa-fukuzaki/)
- [登壇動画（日本語字幕版）](https://youtu.be/Xtrqm4zZGQY)
- [登壇動画（Gatsby.js公式YouTube、英語字幕版）](https://www.youtube.com/watch?v=dzJqVf6qFFg&list=PLCU2qJekvcN3DuWHUhdF4fhLpg2RyXDBB&index=12)

https://youtu.be/Xtrqm4zZGQY

https://www.youtube.com/watch?v=dzJqVf6qFFg&list=PLCU2qJekvcN3DuWHUhdF4fhLpg2RyXDBB&index=12

新しい技術のキャッチアップと合気道、スノボ、旅行が好き。