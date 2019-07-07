---
title: JavaScript：Hoisting (宣告提升)
date: 2019-06-23 13:35:33
tags:
  - JavaScript
---
記錄關於 `Hoisting (宣告提升)` 的知識點。
<!--more-->
## JavaScript 流程
在一般的理解中，`JavaScript` 的語法運行流程，應該是先宣告變數，並進行賦值，最後印出變數的值。
```
var a = 5
console.log(a)  // 印出 5
```
## 特性
因為 `JavaScript` 本身具有 `Hoisting (宣告提升)` 的特性，即使程式碼順序不正確。
`JavaScript` 在檢視的過程中，會自動將宣告的變數提升至前面，促使程式可以正常執行。
```
item = 10
console.log(item)  // 印出10
var item
```
但是 `Hoisting` 的特性在於宣告提升，而不影響賦值，所以如果把賦值放到後面，則會拿到 `undefined`。
```
console.log(item)
var item = 10
```
`JavaScript` 實際運行時，會拿到下面的結果，自然也就印出 `undefined`。
```
var item
console.log(item)  // 印出 undefined
item = 10
```
## 函式
`JavaScript` 在函式，依然具有 Hoisting(宣告提升)的特性，所以下述的程式碼依然能夠執行。
```
test()
function test () {
  console.log('Hello!')
}
```
但是，如果將函式賦值給變數，同樣會因為只有變數被提升，導致後面函式出現 `is not defined`
```
test()
var a = function test () {
  console.log('Hello!')
}
```