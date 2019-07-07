---
title: 實作：簡單留言本 (React)
date: 2019-06-16 22:35:11
tags:
  - React
  - Demo
---
初步摸索 `React` 相關的基礎知識，簡單記錄一點實作的過程，方便日後查看。
<!--more-->
## 配置開發環境
### `install` 官方腳手架工具 `create-react-app`
[Github 網址](https://github.com/facebook/create-react-app)
#### 全域安裝
```
yarn add create-react-app -g
```
#### 啟動 demo
```
create-react-app react-textcontent-demo
```
#### 運行
```
cd react-textcontent-demo
```
```
yarn start
```
## 第一個組件
### 建立 `Hello.js`
`mkdir src/Hello.js`
### 寫入 `Hello React` 內容
```
import React from 'react'

class Hello extends React.Component {
  render () {
    return <h1> Hello React </h1>
  }
}

export default Hello
```
### 引入到 `src/index.js`
- 引入
```
import Hello from './Hello'
```
- 掛載，此時可以看到畫面渲染出 `Hello React` 的畫面。
```
ReactDOM.render(<Hello />, document.getElementById('root'));
```
## `JSX` 語法
JSX 語法是一種語法糖，近似於 `JavaScript` 的語法擴充，放棄模板語言的形式，採用更語意化可讀性更強的標籤。並且使用 {} 內嵌任何 `JavaScript` 表達式。
### e.g. 計算屬性
如下，JSX 會計算出 3 這個數字，並渲染到頁面上。
```
import React from 'react'

class Hello extends React.Component {
  render () {
    const todoList = ['Learning React', 'Learning English']
    return (
      <div>
        <h1> Hello React </h1>
        { 1+2 }
      </div>
    )
  }
}

export default Hello
```
### e.g. 使用 `JSX` 遍歷陣列
```
import React from 'react'

class Hello extends React.Component {
  render () {
    const todoList = ['Learning React', 'Learning English']
    return (
      <div>
        <h1> Hello React </h1>
        {/* 使用JSX語法處理陣列 */}
        <ul>
          {
            todoList.map(node =>
              <li>{node}</li>
            )
          }
        </ul>
      </div>
    )
  }
}

export default Hello
```
### e.g. 三元表達式：狀態判斷 (條件返回)
JSX 語法也能使用在表達式
```
import React from 'react'

class Hello extends React.Component {
  render () {
    const isLogin = false
    return (
      <div>
        <h1> Hello React </h1>
        {/* 三元表達式 */}
        { isLogin ? <p>已經登入</p> : <p>尚未登入</p> }
      </div>
    )
  }
}

export default Hello
```
### JSX 特例
因為 `class` & `for` 已經被 `JavaScript` 關鍵字佔用，因此需使用特例
- 使用 `className` 代替 `class`
```
<div className="style"> Hello World </div>
```
- 使用 `htmlFor` 代替 `for`
```
<label for='male'>Male</label>
```
### 組件書寫特性
自定義 `component` 首字需大寫，這樣 JSX 才能識別為自定義還是原始 `HTML` 標籤。
## `Props` 屬性
組件近似於函式，接受特定的輸入 (props)，產出特定的輸出 (React elements)。
### 透過實例理解 `props`
#### e.g. NameCard
安裝 `UI` 框架 `Bootstrap`
```
yarn add bootstrap
```
在 `src/components` 寫好 `NameCard.js` 的組件，並引入到 `src/app.js`。透過 `props` 從 `app.js` 傳值給 `NameCard.js`，而 `NameCard.js` 則負責渲染資料並佈局樣式。

需要注意的是，`props` 接受傳值後具有唯讀的特性，不可更改。
#### 函數式寫法
目前 `React` 除了過往的 `Class` 寫法，也可以改成函數式寫法。
```
import React from 'react'

const NameCard = (props) => {
  const {} = props
  return ()
}

export default NameCard
```
#### 簡單實現一個點讚+1的功能
同樣的，先建立組件 `src/components/likesButton`，並引入到 `app.js`。

下面是已完成的 `code`，透過 `constructor` 建立初始化數據庫 `state`，接著在頁面搭建 `increaseLikes` 函式。

##### 這邊需注意幾個要點：
`React` 中，事件採用駝峰式命名，例如 `onClick`。
`javascript` 的 `class` 中，`this` 是不會自動綁定的，需要手動綁定。
`state` 數據庫不允許直接操作，需要透過 `setState` 方法。
```
import React from 'react'

class LikesButton extends React.Component {
  constructor (props) {
    super(props)
    this.state = {
      likes: 0
    }
    // 在 javascript 的 class 中，this 是不會自動綁定的，需要手動綁定
    this.increaseLikes = this.increaseLikes.bind(this)
  }
  increaseLikes () {
    // state 數據庫不允許直接操作，需要透過 setState 方法
    this.setState((node) => ({
      likes: node.likes += 1
    }))
  }
  render () {
    return (
      <div className="likes-btn">
        <button
          type="button"
          className="btn btn-outline-primary btn-bg"
          onClick={this.increaseLikes}
        >
          {this.state.likes} 👍
        </button>
      </div>
    )
  }
}

export default LikesButton
```