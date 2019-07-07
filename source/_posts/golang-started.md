---
title: Golang 入門
date: 2019-06-30 09:29:13
tags:
  - Golang
---
記錄 `Golang` 的基礎知識、環境安裝和快速開始。
<!--more-->
## 基本特性
泛用性程式語言，可用於開發各種應用，側重強調效能，有更強的乘載能力。同時相對於傳統的 `C、C++`，學習成本更低。
## 安裝
[Golang 官網](https://golang.org/)
點擊 Download Go，並下載對應的 OS 版本。
## 第一個 `go`
建立一個 `hello.go` 的初始檔案，撰寫以下程式碼。
```
package main  // 封包
import "fmt"
func main () {
  fmt.Println("Hello Golang")
}
```
## 建置 `build`
```
go build hello.go(專案名稱)
```
若 `build` 成功，則 `iterm2` 不會出現其他額外訊息，同時資料夾多出一個 `hello` 的終端機檔案。

把 `hello` 終端機檔案，丟入 `zsh` 的路徑，印出 `Hello Golang`，即代表成功。