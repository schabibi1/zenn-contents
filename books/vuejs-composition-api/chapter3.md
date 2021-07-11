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

dataという関数でmsgというstateを返し、template中のtitleに反映されています

これで「HelloWorld」という文字列がViewに反映されたタイトルのコンポーネントを作成することができました

これが分からないという方はもう一度Vue2の内容を復習しておきましょう

# Composition APIでコンポーネントを作成する

それでは従来のVueをComposition APIを利用して書き換えてみるとどうなるでしょうか？

```vue
<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <p>{{ state.message }}</p>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'HelloWorld',
  setup() {
    const title = ref('HelloWorld')

    const state = reactive({
      message: 'message'
    })

    return {
      title,
      state
    }
  }
}
</script>
```

なんかsetupやらref、reactiveのような見慣れない関数が出てきました

また先程のVue2に比べてmessageという内容を付け加えましたが、これはrefとreactiveの違いについて解説するためです

ただ基本は変わっていません

これを順番に解説していきます

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
    },
    message: {
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
    },
    message: {
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