---
title: JavaScript：this (進階)
date: 2019-06-30 12:23:10
tags:
  - JavaScript
---
`JavaScript` 中的函式綁定物件 `this` 進階知識。
<!--more-->
## 使用 `bind` 重新綁定物件
在預設的函式中，`this` 會指向 `window` 物件，但當預設函式使用 `bind` 時，會被重新綁定新物件 `{a:2}`。
```
function demo () {
  console.log(this)
}
demo()
let demo1 = demo.bind({a:2})
demo1()
```
## 綁定物件進階用法
使用 `apply` 綁定物件。
```
function.apply(綁定物件, [參數, ...])
```
使用 `call` 綁定物件。
```
function.call(綁定物件, 參數)
```
