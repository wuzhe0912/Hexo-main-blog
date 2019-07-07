---
title: Hexo 踩坑記
date: 2019-01-03 22:43:30
tags: Hexo
---
動手安裝 Hexo 過程中踩了一些坑，順手記錄自己 google 到的解法。
<!--more-->
## hexo g 生成路徑錯誤導致樣式跑版
```
hexo g 是 hexo 打包的指令，但若未調整生成路徑，則會出現打包後檔案路徑錯誤，

導致開啟時，整個樣式跑版。

要解決這個問題，需打開 _config.yml

檢查 url 和 root 兩個項目

以部署到 github-page 為例：

url 為專案所在位置：
https://wuzhe0912.github.io/PittWu-Hexo/

root 則填上專案名稱：
/PittWu-Hexo/

完成修改後，重整 github-page，即可修正樣式錯誤問題。
```
## Next 主題背景動畫配置無效果
```
Next 在5.x版本時，設定背景動畫效果，僅需在 _config.yml 調整 true or false 即有效果。

但在6.X版本，不知道因為何種原因，這種設置方式完全失效。
因此改採用下述三個步驟設置動畫效果。

e.g. 選擇 canvas_nest 這個效果

1. cd themes/next
2. git clone https://github.com/theme-next/theme-next-canvas-nest source / lib / canvas-nest
3. next/_config.yml 設定 enable: true

其他三種動畫效果，同前述。
```