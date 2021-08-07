---
title: "副作用フック: computed, watch, watchEffect"
free: true
---

# 副作用フック（Effect Hook）: computed, watch, watchEffect

副作用フック（Effect Hook）とは、その名の通り、副作用のためのフックです。

とはいえ、副作用と言われても、ピンと来づらいかと思います。

英語のVue公式ドキュメントでは「side effect」と名前がついています。

「side effect」はそのまま直訳すると「副作用」ですので、このことを知っておくといいかもしれません

# 何が副作用なのか？

ここでは一体何のことを副作用とみなしているのかについて見ていきましょう。

ここで言う副作用とは、以下の例が挙げられます。

- Vueコンポーネント内から、外部データの取得をすることによって起こる他のコンポーネントへの影響
- レンダーの最中に実行できない操作（Vueコンポーネント内から、外部データの取得をする操作）

ほかにも例はありますが、まずはこの例をもとに解説します。

例えばですが、チャットアプリがあったとしましょう。

とてもシンプルな構成をイメージするとすれば、以下のようになるかと思います。

| アプリ概要 | 着目する機能 |
| ---- | ---- |
| チャットアプリ | アプリケーションが読み込まれた時に、チャットデータを表示する |

この時に意識をしたいのが、チャットデータの存在場所です。

チャットのようなユーザーの入力によって追加されるデータは、サーバーにあることが多いです。

![](https://storage.googleapis.com/zenn-user-upload/owx8pvmf4dupxgypw86tixppz16l)

つまり、ここで言うチャットデータは「外部データ」という認識ができます。

チャットアプリ自体の、チャット欄を表示するフロントエンド部分は、Vueによって実装され、出力されます。

![](https://storage.googleapis.com/zenn-user-upload/1fyk6euf84kicnntjbhllyqpaf1q)

| アプリの状態 | 処理のフロー |
| ---- | ---- |
| ① ローディング画像表示 | Vueコンポーネント内から外部データ（チャットデータ）取得中 |
| ② 取得した外部データ（チャットデータ）表示 | 表示が変わり、他のコンポーネントに影響 |

この例を見ると、勘の良い方は気がつかれたかもしれません。

Vue Composition APIではwatcher(computed, watch, watchEffect)を、Vue2までの従来のコンポーネントでいう、以下の技法をAPIとして提供しています

- computed
- watch

:::message
名称は同じですが違いがあるので、それについては先の項目に解説があります。
:::

# watcherの簡単な実用例

説明を聞くだけでは、まだ深く理解をするには難しいと思うので、先ほどのカウンターアプリにwatcherを追加して、実際にソースコードを書いてみましょう。

ここでは、先ほどの練習問題で取り組んだ、簡易版カウンターアプリに `useEffect` を使って、HTMLドキュメントのタイトルにも、クリックされたカウント数を表示させるようにします。

つまり、クリックが発生した回数を、HTMLドキュメントのタイトルにも反映させるというものです。

イメージしやすくするために、簡潔なワイヤーフレーム、遷移設計を以下にお見せしましょう。

![](https://storage.googleapis.com/zenn-user-upload/3zcz2clntvwuef1ikq0k80gm1ogf)

# watcherの基本構文

まずは基本構文の確認をします。

## computed

 `computed` は、基本的には以下の構造を持ちます。

```js
const value = computed(callback)
```

例を見てみましょう

以下のように`fullName`をComposition APIのcomputedを使って算出するようにしました

```js
export default {
  setup() {
    const state = reactive({
      firstName: '太郎',
      lastName: '佐藤',
    })
    const fullName = computed(() => {
      return `${state.lastName} ${state.firstName}` // 「佐藤 太郎」
    })
    return {
      state,
      fullName
    }
  }
}
```

**「firstNameかlastNameのstateが変化する度に、fullNameを算出する」** ということを指示しています。

## watchとwatchEffect

この2つの処理はよく似ています。しかしいくつか動きが異なる点や細かいカスタムができる点で両者は違います

今回両方を紹介しますが、慣れないうちは`watchだけ使う`のが無難です

理由としては後ほど紹介します

それでは先に`watchEffect`から紹介します

 `watchEffect` は、基本的には以下の構造を持ちます。

```js
watchEffect(callback, options)
```

第1引数にcallback、第2引数にoptionsを指定することができます。ただしoptionsに関しては細かく、利用するケースも少ないため今回は説明を省略します

興味のある方は公式ドキュメントを読んでみてください

https://v3.vuejs.org/guide/reactivity-computed-watchers.html#effect-flush-timing

```js
export default {
  setup() {
    const state = reactive({
      firstName: '太郎',
      lastName: '佐藤',
      fullName: ''
    })
    watchEffect(() => {
      state.fullName = `${state.lastName} ${state.firstName}`
    })
    return {
      state
    }
  }
}
```

先程の`computed`で実装したものを`watchEffect`を使ったものに書き換えてみました。

fullNameはstateとして持ち、firstNameかlastNameのstateが変化したときにfullNameのstateを変更するといった処理です。

さらにこれを`watch`を使った実装方法へ書き換えてみましょう

```js
export default {
  setup() {
    const state = reactive({
      firstName: '太郎',
      lastName: '佐藤',
      fullName: ''
    })
    watch(() => [state.firstName, state.lastName], () => {
      state.fullName = `${state.lastName} ${state.firstName}`
    })
    return {
      state
    }
  }
}
```

先程に比べて少々コードが複雑になりました。watchに引数が増えましたね。

watchだと第一引数にどのstateが変更されたとき、callback処理が実行されるかどうか制御することができます

逆を言えば、 **「firstNameとlastNameが変化していない場合は、この処理はスキップ」** と指示しているということにもなります。

わかりやすい例えにするとすれば、行きつけのお気に入りのカフェがあるとしましょう。

毎日欠かさず1年以上通っているお気に入りのカフェで、注文する飲み物もいつも定番のドライカプチーノだとしましょう。

スタッフは、全員あなたのことを常連客だと認識して、名前も覚えてくれています。

でも、1年以上通って、毎日同じ定番の飲み物を注文しているのに、一向にいつも注文する飲み物を覚えてもらえないとどうでしょうか？

毎回レジで注文する際に、飲み物の名前を言う手間が生じます。

常連客だと認識されているのに、飲み物だけは毎回同じものを注文しなければ利用できないのは嫌ですよね。

これが`watchEffect`です。

しかし、 `watch` の第1引数を使うと、一度入店して注文しただけで、同じ飲み物のオーダーが入れば、スタッフが「今日はドライカプチーノですか？」と向こうから聞いてくれるのです。

1年も通えば、入店するだけでお気に入りのドライカプチーノを既に準備してくれるようになります。

![](https://storage.googleapis.com/zenn-user-upload/ldw2f33ks2qtffalnb67zp7yjj27)

最初に

> 慣れないうちは`watchだけ使う`のが無難

と述べたのは、明示的にwatch(監視)するstateを指定できるためです

これにより無駄な再計算や再レンダリングを防ぐことができるようになります。stateが増えるほどアプリケーションのパフォーマンスに影響するため原則監視したいstateを指定するようにしましょう

実は他にも細かい違いがあるのですが、最初の知識としてはこれで十分です

もし興味のある方は公式ドキュメントを読んでみて下さい

https://v3.vuejs.org/guide/reactivity-computed-watchers.html#computed-and-watch