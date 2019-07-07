---
title: Node 環境搭建(新電腦)
date: 2019-06-16 16:48:58
tags:
  - node
  - nvm
  - 環境搭建
---
環境搭建是件挺麻煩的事情，很常踩到各種坑，記錄一下近期安裝流程。方便下次快速排查問題。
<!--more-->
## 安裝 Homebrew
Homebrew 是 mac 套件管理工具，透過它來安裝 nvm
- [Homebrew 官網](https://brew.sh/index_zh-tw)
- 安裝指令
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
## 安裝 nvm
Node.js 的版本更迭速度很快，為了有效率管理 Node 版本，使用 nvm 工具進行 Node 版本切換與安裝。
- [nvm github](https://github.com/nvm-sh/nvm)
- curl 安裝 nvm
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
- Homebrew 安裝 nvm
```
brew install nvm
```
### 測試 nvm 是否安裝成功
```
nvm --version
```
但這時 iterm 另開分頁，測試`nvm --version`，有極大機率會`nvm: command not found`，所以為了解決這個問題，需要修改`.bash_profile`文件。
#### 編輯 .bash_profile 文件
```
vi .bash_profile
```
#### 複製下列代碼
進入文件後，按 `i` 切換到修改模式，將複製的代碼貼上。
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
```
按 `esc` 退出修改模式，接著按 `:wq` 保存修改後的結果。
#### 生效
```
source .bash_profile
```
## 安裝 Node
使用 nvm 指令查詢並安裝 node
### 查詢遠端 node 版本
```
nvm ls-remote
```
### 安裝需要的 node 版本
```
nvm install v11.15.0
```
### 切換需要使用的 node 版本
```
nvm use v11.15.0
```
### 設定預設使用的 node 版本
```
nvm alias default v11.15.0
```