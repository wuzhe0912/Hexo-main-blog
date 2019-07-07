---
title: Vue-Cli 3.0 Demo
date: 2019-01-08 00:13:54
tags:
  - Vue
  - vue-cli
---
vue-cli 3.0 版本已經釋出一段時間，考慮到後續工作專案會開始採用，也必須著手實作了解一下。
<!--more-->
[Vue-Cli 官網](https://cli.vuejs.org/zh/)
## 與 2.0 版本差異
```
1. 新增GUI介面，可以不需使用指令。
2. 更好的兼容支援TypeScript。
3. 傳統在2.0版本的webpack配置，在GUI介面除了可使用下拉選擇方式，也多了更多的說明介紹。
```
## 安裝流程
```
// 安裝方式(須移除舊版本Vue-Cli 1.x or 2.x)

npm uninstall vue-cli -g
# or
yarn global remove vue-cli
```
```
// 前置要求：Node版本最低需8.9或更高(官方推薦8.11.0以上)
// 安裝指令

npm install -g @vue/cli
# or
yarn global add @vue/cli
```
```
// 確認是否install成功，檢查版本號

vue --version
# or
vue -V

# 2019/1/8 v3.3.0
```
#### 測試兩種專案結果
```
A專案是以vue-cli 2.x版本時建立

移除vue-cli 2.x 並安裝vue-cli 3.0後

create B專案，再回頭重新以3.0環境啟動A專案，可正常運行
差別在於2.x版本的啟動指令仍是yarn run dev
而3.0則改用yarn serve
```
## 兩種創建專案方式(command-line || GUI)
### command-line
```
vue create 專案名稱
```
#### 選擇預設套件或是手動選擇
```
// 第一次在3.0環境建立專案時，僅有上述兩種選項
// 當建立過一次模板環境後，可以選擇save，在第二次建立時，可以選用
```
{% asset_img select.png %}
#### 依需求選擇安裝項目
```
按 space 選擇需安裝的項目
```
{% asset_img space-select.png %}
#### ESlint選規範版本
![](https://i.imgur.com/KdPyhMA.png)
#### 每次儲存時檢查代碼規範或commit時檢查
![](https://i.imgur.com/98UuQvU.png)
#### 安裝在package.json內或獨立安裝
![](https://i.imgur.com/VwVIwNo.png)
#### 是否保存這次建立的選項(提供下次專案直接套用)
![](https://i.imgur.com/XVfShLK.png)

### GUI 創建(建議暫時擱置不使用，尚未穩定)
```
// 安裝完成vue-cli 3.0環境後，輸入指令vue ui

// 家中 mac 測試，GUI 工具會有持續 loading 的 error 問題
// 查官方 issues 這一類的問題相當多，3.0.0 版本時全域安裝core.js可解
```
## 資料夾結構

```
vue-cli 3.0 版本對應的是 webpack4.0 以上版本。

因為官方不希望開發者花費過多精力調整webpack設定，

因此統一移入node_modules
```
### 路徑如下：

```
node_modules/@vue/cli-service/webpack.config.js

// Service.js

node_modules/@vue/cli-service/lib/Service.js
```
### 引入路徑名稱
```
// 在 3.0 版本需注意引入路徑名稱和2.x有所差異

e.g.
import HelloWorld from '@/components/HelloWorld.vue'

副檔名中.vue 在 3.0 版本不可被省略。
```
### index.html
```
過往會被放在根目錄下，3.0 版本改至 public 下
```
### 測試打包
```
yarn build
```