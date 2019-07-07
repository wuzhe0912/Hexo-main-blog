---
title: 面試問題整理：CSS
date: 2019-06-29 23:51:10
tags:
  - 面試
  - CSS
---
`CSS` 基礎知識問題整理。
<!--more-->
## 什麼是選擇器?
`CSS` 選擇器常見分為四種，同時根據權重差異，決定彼此的優先級。
1. 行內樣式(inline)，直接在 `HTML` 添加樣式，權重最重(1000)
```
<p style="color:red">Hello</p>
```
2. ID 選擇器，權重次之(100)
```
#header
```
3. 最常用的 `class`，包含偽類、屬性，權重(10)
```
.wrap、:hover、[attribute]
```
4. 元素選擇器(即 `HTML` 元素本身)、偽元素，權重(1)
```
p、h1、em、::after
```
## 請解釋 * { box-sizing: border-box; }？並且說明使用它的好處？
`box-sizing`：意指，當元素計算寬度和高度時，`border` & `padding` 會內含還是外加。

`content-box`：預設的屬性，會使 `border` & `padding` 添加額外的寬高(外加)。
`border-box`：為了改善前面這種不友好的設計，將 `border` & `padding` 塞進元素本身(內含)。

因此我們通常建議在初始化樣式時，加入到 `*`。
```
* {
  box-sizing: border-box;
}
```
## `margin` 垂直覆蓋屬性
`margin` 的特性中，當兩個元素為垂直時，會產生覆蓋重疊的問題。例如兩個 `p` 標籤，設定 `margin` 為 `5px`，理論上應該是 `5px + 5px = 10px`，但因為重疊的關係，實際上只有 `5px`，另外，如果兩個 `tag` 大小不一的話，大的一方會蓋掉小的一方。
## 請列出您記憶中 `display` 屬性的全部值。
```
display: block
display: inline
display: inline-block
display: none
```
## 請說明 `inline` 和 `inline-block` 的差異性？
```
inline：兩個 `inline` 元素不會換行顯示，只能使用 margin、padding 調整，例如 <a>、<span> 標籤。
inline-block：排列方式採 inline，但擁有 block 屬性，CSS 的樣式皆可設定，例如 <img>
```
## 請說明 `relative`、`fixed`、`absolute` 和 `static` 元件差異性？
```
static：預設值，按照瀏覽器預設的配置排版
fixed：相對於瀏覽器視窗來定位，即使畫面捲動也會出現在固定的位置
relative：可以設定top、left、right、bottom，使元素相對調整原本該出現的位置，此調整不影響其他元素的位置，提供 absolute 作為定位基準。
absolute：依據父元素進行定位，即在父元素設定 relative，在子元素設定 absolute。
```
## 在寫高效的 CSS 時，有什麼要注意的？
1. 良好的語意化命名
2. 減少重複性的 `Code`
3. 適當的註釋
4. 保持可讀性和排列整齊，避免縮徑不一致
5. 減少佔用記憶體，能使用 `none` 屬性，就不要使用 `0`，如下：
```
使用 -> border: none，而不要使用 border: 0
雖然頁面呈現效果相同，但 none 屬性不做渲染動作，不會消耗記憶體。
```
## 描述 `resetting` 和 `normalizing` 的差異性？
`resetting`
```
因為不同瀏覽器對於標籤預設樣式都不同，因此定義出一套可以覆蓋所有HTML標籤的CSS樣式表，使所有瀏覽器標準一致。
```
`normalizing`
```
相對於resetting將所有標籤的預設樣式都歸零，這類的樣式僅針對不同瀏覽器和版本不相容的標籤進行微調。
```
## 請說明 `z-index` ？
簡單說，遵守兩個原則。
1. `z-index` 給的數字越大者，權重越重，可覆蓋權重低的元素。
2. 當兩者權重相同時，後面的元素覆蓋前面。
