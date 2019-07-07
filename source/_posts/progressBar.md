---
title: 簡單實現 ProgressBar 效果
date: 2019-06-12 00:29:25
tags: 
  - Vue
  - 頁面邏輯
---
記錄工作上，ProgressBar 的實現方式，以及如何結合API，達到推進的效果。
<!--more-->
## 頁面結構
### 準備一條當基底背景的 ProgressBar
- index.vue( 此處使用 Pug )
```
span.graph
```
- style.scss
```
// ProgressBar 的寬高、背景色或 border-radius，依設計需求調整。

.graph {
  display: flex;
  width: 85%;
  height: 6px;
  background-color: #e6f8f9;
  border-radius: $radius;
}
```
### 準備一條產生前進變化的 ProgressBar
- index.vue
  - template
```
span.graph
  i.line(v-if="node.content" :style="{width:lineWidth(node.content.rate)}")
```
  - methods
```
lineWidth (item) {
  return item + '%'
}
```
- style.scss
```
.graph {
  display: flex;
  width: 85%;
  height: 6px;
  background-color: #e6f8f9;
  border-radius: $radius;

  .line {
    display: flex;
    height: 100%;
    background-image: linear-gradient(to right, #ffeafe, #ccc1ff, #9ea9f0);
    border-radius: $radius;
  }
}
```
## 運作邏輯
負責執行前進變化的 ProgressBar，除去 width 之外，height 和 border-radius 必須和第一條 ProgressBar 相同，背景色則必須有所不同，才能出現覆蓋，達到前進的效果。

接著，問題在於，如何讓 width 出現動態變化。透過 API 取得的值，傳參給函式 lineWidth()，在函式中將值進行轉換並 return，如此便達到 ProgressBar 會隨著 API 取回的值產生前進變化。