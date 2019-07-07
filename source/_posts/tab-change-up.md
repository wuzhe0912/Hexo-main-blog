---
title: tab 選項卡切換內容(上)
date: 2019-06-16 18:07:04
tags:
  - Vue
  - 頁面邏輯
---
使用 tab 切換顯示內容，是常見的功能，記錄一下目前工作用的 tab 選項卡寫法。
<!--more-->
## 準備 tab 列表
這個列表可能是 API 給的值，也可能是前端自己組的靜態陣列，使用 `v-for` 語法渲染整個陣列。
- index.vue
  - template
```
.tabTitle(v-for="(node, index) in itemList")
```
  - 初始化一個用於點擊切換 tab 的參數 filter，並且初始化 tab 陣列
```
data () {
  return {
    filter: 0,
    itemList: []
  }
}
```
  - 當頁面一進入時，就必須呼叫 API 函式，將取得的值傳入 tab 陣列
```
created () {
  this.ListService()
}
```
  - methods 取得 API 的值
```
getItemList () {
  ListService.getItemList()
    .then((res) => {
      this.itemList = res
    }).catch((err) => {
      console.log(err.message)
    })
}
```
  - API 約定格式
```
result: [
    {
        name: "選項一",
        data: [{}]
    },
    {
        name: "選項二",
        data: [{}]
    }
]
```
  - 這時就能從 template 上，渲染出 tab 列表。
  - 這邊多了一個 `filterChange` 的函式，用於執行點擊時，切換下方內容。
```
// 先用長度檢查 res 回傳是否正確
.tabTitle(v-if="itemList.length > 0")
  template(v-for="(node, index) in itemList")
    a.tabLink(@click="filterChange(index)") {{node.name}}
```
  - methods
```
filterChange (index) {
  this.filter = index
  this.subItemList = this.itemList[index].data
}
```
## 此處需修正，待補充
## 名稱轉換
通常 API 取回來的值，不一定符合前端需求，可能是英文或是數字，這時可以透過建立一個 `formatter` 函式來進行轉換。
### 準備轉換用的靜態對照表
建立在 `src/configs/site.js` 中。
```
export const TYPE = [
    { name: '第一個名稱', value: '0'},
    { name: '第二個名稱', value: '1'}
]
```
回到 `index.vue` ，在 `script` 中引入對照表。
```
import { TYPE } from '@/configs/site'
```
並在 `methods` 中準備 `formatter` 函式。
```
nameFormatter (val) {
  let target = TYPE.find(node => node.value === val)
  if (target) return target.name
  else return val
}
```
渲染到 `template` 上。
```
.tabTitle(v-if="itemList.length > 0")
  template(v-for="(node, index) in itemList")
    a.tabLink(@click="filterChange(index)") {{nameFormatter(node.name)}}
```
## tab 點擊切換時，進行樣式變化
幾乎無可避免，tab 切換時會被要求添加樣式來改善使用體驗。
### 透過 v-bind 綁定 class
`data` 中存有初始化的變數 `filter` ，這組參數將作為判斷機制，當點擊事件觸發時，`filter` 也隨之變化。當 `filter` === 陣列中的 `index` ，則觸發綁定 `active` class。
- style.scss
準備 tab 列表本身每個欄位的樣式，並事先給予一個偽元素 `after` 作為切換時變化用的樣式。但是先將 `width` 設為 0 使其不顯示。當 `active` 被觸發時，則將 `after` 偽元素賦予 `width` 的值，此時便可以正常顯示，同時也能做一些樣式的改變，達到點擊切換時樣式變化的效果。
```
.tabLink {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 10px;
  height: 100%;
  font-size: 13px;
  white-space: nowrap;
  color: $base;
  flex-direction: column;
  cursor: pointer;

  &.active {
    font-weight: bold;
    color: $danger;

    &::after {
      width: 100%;
    }
  }

  &::after {
    @include position(absolute, n, 0, 0, 0);

    z-index: index($z-index, base);
    display: flex;
    width: 0;
    height: 2px;
    background-color: $danger;
    transition: .5s ease all;
    content: "";
  }
}
```