---
title: "Setup Component: refとreactive"
free: true
---

# 従来までのVueのおさらい

これまでVue2では以下のような書き方をしていました

```vue
<template>
  <div class="hello">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => {
    return {
      title: 'HelloWorld'
    }
  }
}
</script>
```

dataという関数でtitleというstateを返し、template中のtitleに「HelloWorld」という文字列が反映されています

ここまでが分からないという方はもう一度Vue2でのstate管理を復習しておきましょう

# Composition APIでコンポーネントを作成する

それでは従来のVueをComposition APIを利用して書き換えてみるとどうなるでしょうか？

```vue
<template>
  <div class="hello">
    <h1>{{ props.title }}</h1>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'HelloWorld',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup() {
    const message = ref('HelloWorld')

    return {
      title
    }
  }
}
</script>
```

setupやらrefのような見慣れない関数が出てきました。しかし基本は変わっていません。これを順番に解説していきます

# setup

composition APIを利用するにあたって必ず使用しなければならないのが、このsetupというプロパティになります

このsetup関数内で返したstateや値、関数がtemplate内で利用できるようになります

また従来まで、propsを関数で利用する際には以下のような書き方をしていました

```js
export default {
  name: 'HelloWorld',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  methods: {
    callTitle() {
      console.log(this.title)
    }
  }
}
</script>
```

しかしComposition APIを利用するにあたってthisを使用する必要はありません

以下のような内容に書き換えることができます

```js
export default {
  name: 'HelloWorld',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const callTitle = () => {
      console.log(props.title)
    }

    return {
      callTitle
    }
  }
}
</script>
```

setup関数の引数からpropsを呼び出せるようになりましたね

簡単なsetupについて解説は以上です

このsetupはコンポーネントを作るたびに、ほぼ毎回書きますので実際に使いながら慣れていきましょう

## stateを扱うAPI

従来のVueの書き方だとオブジェクトのdataでstateを返すようにしていました。これでコンポーネントのstateとして扱うことができるようになります

しかしComposition APIにおいてstateはsetup内に定義することになります

stateを扱うAPIは主に2つ、「ref」と「reactive」です

これら2つのAPIについて見てみましょう

### ref

refは[プリミティブ](https://developer.mozilla.org/ja/docs/Glossary/Primitive)な値をリアクティブにするためのAPIです

プリミティブとはひとまず、オブジェクト型でない値と捉えていただければ問題ないです。例えば文字列や数値のような値ですね

実際の使い方を見てみましょう

```vue
<template>
  <div>
    <h1>{{ title }}</h1>
    <button type="button" @click="changeTitle">change</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'HelloWorld',
  setup() {
    const title = ref('')

    const changeTitle = () => {
      title.value = 'Hello'
    }

　  return {
      title,
      changeTitle
    }
  }
}
</script>
```

「change」ボタンを押すとタイトルへ「Hello」と表示される関数を作成しました

ポイントとしては以下の3点です

- refでは文字列をstateとして扱っている
- scriptタグ内ではvalueを使って値を読み書きすることができる
- template内ではvalueでなくrefそのものが値として反映される

refではプリミティブな値をstateとして扱うのが基本でしたね。
今回の場合は空文字を初期値にしました

続いて「changeTitle」という関数を見てみましょう

titleに直接「Hello」を代入するのではなく、valueを使用しているのがわかると思います。これはrefのstateをscript内で読み書きする際のルールなので注意です

最後のtemplate内ではvalueでなくrefそのものが値として出力されるという点に関してです。script内ではvalueを使って読み書きしましたが、template内ではvalueを使わずとも値を出力することができます

script内とtemplate内で書き方が変わるのは間際らしいかもしれません。使いながら慣れていきましょう

### reactive

reactiveはオブジェクトをリアクティブにするためのAPIです

オブジェクトのプロパティをそれぞれリアクティブな値として管理ができるようになります

実際の使い方を見てみましょう

```vue
<template>
  <div>
    <h1>{{ state.title }}</h1>
    <button type="button" @click="changeTitle">change</button>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'HelloWorld',
  setup() {
    const state = reactive({
      title: ''
    })

    const changeTitle = () => {
      state.title = 'Hello'
    }

　  return {
      state,
      changeTitle
    }
  }
}
</script>
```

refと全く同じことができるコンポーネントを作ってみました。「change」ボタンを押すとタイトルへ「Hello」と表示される関数を作成してあります

ポイントとしては以下の3点です

- stateオブジェクト内でtitleというstateを管理している
- stateオブジェクトのtitleに直接値を代入できる
- template内でもstate.titleで値をViewに反映させることができる

今回もtitleの初期値は空文字列にしてあります

続いて「changeTitle」という関数を見てみましょう

refと違ってvalueを使わずとも、state.titleへ直接値を代入することができます。ただし以下のような書き方はできないので注意してください

```js
const changeTitle = () => {
  state = {
    title: 'Hello'
  }
}
```

この書き方だと値が変わらなくなるバグが発生します。なぜならreactiveな状態を保つことができなるからです

## まとめ

今回はsetup、ref、reactiveのといった関数に関して解説しました

これらのAPIはComposition APIを利用した実装をするにあたって、非常に重要な関数となります

次の章ではComposition APIを利用したカウンターアプリを作りますのでrefやreactiveを利用しながら実践的に練習をしてみましょう
