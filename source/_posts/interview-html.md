---
title: 面試問題整理：HTML
date: 2019-07-05 07:29:22
tags:
  - 面試
  - HTML
---
`HTML` 基礎知識問題整理。
<!--more-->
## `doctype` 做什麼用的？
```
用來定義網頁編寫的HTML採用什麼版本。
```
## 請描述 `cookies` ， `sessionStorage` 和 `localStorage` 的不同？
```
cookies：每個HTTP request都會送到伺服器端，會拖累載入速度和頻寬。

sessionStorage、localStorage 為 HTML5 所新增的功能，僅保存在本地。

sessionStorage：保存的生命週期較短，當瀏覽器或葉面關閉時，即清空消失。

localStorage：生命週期較長，會等 JavaScript 清空，或用戶清除瀏覽器 cache。
```
## 你怎麼做一個需要支持多國語言的網頁？
```
使用知名的 i18n 套件。
```
## `standards mode` 和 `quirks mode` 有什麼不同？
standards mode：有宣告 `doctype`。
quirks mode：沒有宣告 `doctype`，使用較舊的瀏覽器模式。
## 有用過 HTML 樣板語言（template languages）嗎？
使用過 `pug`，減少<>的撰寫，可以加速開發流程。
## 使用 XHTML 有什麼限制？
1. 元素必須正確插入，並且有閉合標籤。
```
<b><i>test</i></b>
```
2. 統一元素使用小寫。
3. 所有元素需放在 `html` 標籤內。
