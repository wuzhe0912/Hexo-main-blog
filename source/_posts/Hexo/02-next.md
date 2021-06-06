---
title: Hexo：Next Theme
date: 2021-04-22 22:10:33
categories: Hexo
tags: Next
---
前一篇筆記中，我的 Hexo Blog 已經啟用 Next 做為基底的 Theme ，這一篇則繼續針對參數的部分進行記錄。
<!--more-->
## codeblock
主要用於設定 code(即程式碼區塊) 樣式，我個人是選擇 mac 風格，另外轉為黑暗風格，參數如下
``` JavaScript
codeblock:
  theme:
    light: atom-one-dark
    dark: atom-one-dark
  copy_button:
    enable: true
    # Available values: default | flat | mac
    style: mac
```

## 回到頂部
打開回到頂部的按鈕顯示百分比的部分，將 scrollpercent 改為 true
``` JavaScript
back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
  scrollpercent: true
```