---
title: HTML 5：語意標籤
date: 2019-06-30 14:47:01
tags:
  - HTML 5
---
`HTML 5` 的語意標籤概念。
<!--more-->
## 語意與非語意標籤
常見的 `div` 就是典型的非語意標籤， 過往在 `Layout` 排版時，會透過設定常見的 `class` 名稱，來區分板塊上的位置。
```
<div class="header"></div>
<div class="footer"></div>
```
到了 `HTML 5` 的版本後，原先通用常見的 `class` 命名，被加入到標籤，而這些新增的標籤，透過英文可以直接了解到其對應的區塊，因此也被稱為語意標籤。
```
<header></header>
<footer></footer>
```
## 優點
透過語意標籤，可以精簡化程式碼，不需要特別使用 `div` + `class`，此外對搜尋引擎優化(SEO)有更好的輔助效果，結構如下。
```
<header>標題</header>
<nav>Nav選單</nav>
<main>
  <article>文章內容</article>
  <aside>側邊欄</aside>
</main>
<footer>底部</footer>
```
若需要針對語意標籤處理樣式時，可以在 `CSS` 中使用標籤選擇器。
```
header {
  color: blue;
}
```