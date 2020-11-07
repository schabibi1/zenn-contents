---
title: "グリッドアイテム"
free: true
---

アイテムという考え方も、Flexboxでコンテナーとアイテムについては、親子関係にある要素だということを学習していますので、そこまで難しくはないかと思います。

コンテナーがアイテムを収納する箱の役割をするのに対して、アイテム、はその箱の中身1つ1つです。

![](https://storage.googleapis.com/zenn-user-upload/380pa6mt7gflcrslebu55dpamzcp)

```html
<div class="container"><!-- グリッドコンテナー 親要素 -->
  <div class="item item-1">1</div><!-- グリッドアイテム 子要素 -->
  <div class="item item-2">2</div><!-- グリッドアイテム 子要素 -->
  <div class="item item-3">3</div><!-- グリッドアイテム 子要素 -->
</div>
```