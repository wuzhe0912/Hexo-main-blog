---
title: 面試問題整理：JavaScript
date: 2019-06-22 00:40:54
tags:
  - 面試
  - JavaScript
---
`JavaScript` 基礎知識問題整理。
<!--more-->
#### Q1：直接輸入 `console.log(a)` 會印出什麼？ 
```
Uncaught ReferenceError: a is not defined
```
`JavaScript` 是一種弱型別語言，宣告變數時，不需要先聲明類型。但如果沒有先建立變數的情況下，自然也會出現 `ReferenceError`。

---
#### Q2：`JavaScript` 目前有幾種型別？
javascript 目前定義了七種型別，包含如下：
```
number - 數字，譬如 123
string - 字符串，譬如：'Hello'
boolean - 布林，true、false
null
undefined
object - 物件，{name: pitt}、[12, 34, 56]、function
symbol(ES6 新增的型別)
```
這七種型別可以區分為兩大類，分別是基本型別和物件型別，除了 object 外，其他都是基本型別。

---
#### Q3：`let a = "5" * "4"`，`console.log(a)` 會印出什麼？
```
20
```
`JavaScript` 在 `number` 型別中，可以很好理解一般數學的四則運算，但是在 `string` 中，則會有些特別。
`string` 相加時，會印出兩個字符串。
```
let a = '2' + '2'
console.log(a) // 印出 '22'
```
但是 `string` 進行減法、乘法、除法時，則會進行一般數學計算。
```
let b = '3' * '3'
console.log(b) // 印出 9
```
```
let c = '10' - '5'
console.log(c) // 印出 5
```
```
let d = '20' / '2'
console.log(d) // 印出 10
```

---
#### Q4：`let item = '1' == '10' || '2' == '2'`，`console.log(item)` 印出什麼？
```
true
```
其實這題沒什麼懸念，只是某次看到時，不知道大腦哪根神經接錯，竟然填 `false`，因此順手紀錄下來，避免下次再次犯錯。`||` 即指滿足一邊條件即可，反之 `&&` 則須滿足所有條件。

因此，`let item = '1' == '10' && '2' == '2'` 則印出 `false`。

---
#### Q5：第一行 `function` 是否能夠順利執行？
```
numChange()
function numChange() {
  let num = 10
}
```
```
基於 JavaScript 的 Hoisting(宣告提升) 特性，能夠執行。
```
{% post_link javascript-hoisting JavaScript：Hoisting(宣告提升) %}

---
#### Q6：下面 `splice` 方法會得出什麼結果？
```
var colorLength = [
  'yellow',
  'blue',
  'red'
]
colorLength.splice(1, 1)
console.log(colorLength)
```
```
// 印出
['yellow', 'red']
```
在 `splice` 方法中，第一個參數為起始位置，從哪一個位置開始刪除。
第二個參數則為結束位置，如果不填，則從起始位置後面全部刪除。
```
colorLength.splice(1)

// 印出
['yellow']
```
如果第二個參數填0，則不刪除任何值。
```
colorLength.splice(1, 0)

// 印出
["yellow", "blue", "red"]
```
第三個參數為可選，若有填值，則會加入原陣列中。
```
colorLength.splice(2, 2, white)

// 印出
["yellow", "blue", "white"]
```
#### Q7：如何用 `JavaScript` 原生方法實作回上頁的功能？
```
可以調用兩種方法：
1. window.history.back // 回到上一頁
2. window.history.go(-1) // 指定回到上一頁，若傳入參數為 -2，則指定回到上二頁
```
