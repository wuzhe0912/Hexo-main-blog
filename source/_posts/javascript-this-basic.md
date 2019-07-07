---
title: JavaScript：this (基礎)
date: 2019-06-30 12:22:56
tags:
  - JavaScript
---
`JavaScript` 中的函式綁定物件 `this` 基礎知識。
<!--more-->
## 基本觀念
`this` 代表函式的綁定物件，通常在函式中使用。但在不同程式碼狀況下，綁定物件會代表不同東西。
### 情境一：獨立的函式
當 `this` 使用在函式時，會指向 `HTML DOM` 中最上層的 `window` 物件。
也就因此能指向 `window` 底下的對象，譬如視窗的寬 `innerWidth`。
```
function demo () {
  console.log(this)
  console.log(innerWidth)
}
demo()
```
### 情境二：物件
在物件中，`this` 會被指向物件本身，因此物件中有的屬性或值，都可以被 `this` 指向，並且進行操作，例如使用 `console` 印出來。
```
let obj = {
  a: 2,
  demo: function () {
    console.log(this)
    console.log(this.a) // 印出 2
  }
}
obj.demo()
```
### 情境三：事件處理函式
在事件中使用 `this`，其本身就是觸發事件的對象，譬如綁定在 `button` 上，就會觸發 `button`。而當現在未綁定時，就會指向 `document`。
```
document.addEventListener('click', function () {
  console.log(this)
  this.body.innerHTML = 'Clicked'
})
```
### 情境四：建構函式
在建構式當中，`this` 會是瀏覽器自動幫我們新建立好的空白物件。因此當我們在其中進行賦值時，相對也就會塞進物件中。
```
function Point () {
  console.log(this)
  this.a = 5
  this.b = 10
}
let test = new Point()
console.log(test)
```