---
title: Windows：Cmder 設定
date: 2021-04-18 12:19:47
categories: Terminal
tags: Cmder
---
在`Windows`環境下，能使用的終端機選擇有限，`Cmder`是目前不錯的一個選項。
<!--more-->
## install
[Cmder 下載連結](https://cmder.net/)
若本機已安裝`Node`，可以下載`Mini`版本即可，下載解壓縮即可使用。

## powerline
我希望`Cmder`預設打開時，路徑可以採用`powerline`形式美化，進入下方連結後，下載`zip`檔案
[cmder-powerline-prompt 下載連結](https://github.com/AmrEldib/cmder-powerline-prompt)

將解壓縮的檔案中，副檔名為`.lua`的檔案，統一放到`Cmder/config`的資料夾中。重新啟動`Cmder`可以看到`powerline`已經出現了。

## background
在右下角中有一個類似`hamburger menu`的`icon`，點開來就可以看到針對`Cmder`進行各種參數調整，這邊我們先改背景，先下載一張你喜歡的圖片(日後可以隨時替換)，點選左側的`General/Background`，並將`Background image`打勾，然後選擇你的圖片路徑，這時候圖片即會替換背景，但這時候圖片的設定沒有置中，解析度也不正確，點選右側`Placement`的下拉選單，選擇`Stretch`，即可讓圖片正常顯示。

## Fonts
點選左側的`General/Fonts`，調整一下字體大小，我是習慣`Size 20`，這點因人而異，另外會勾選`Bold(粗體)`，`Italic(斜體增加一些美感)`。

## Tab
點選左側的`General/Tab bar`，我習慣取消勾選`Tabs on button`，讓`tab`回到上方，至於`UI`則調整到`x20`。