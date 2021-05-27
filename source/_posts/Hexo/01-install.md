---
title: Hexo(01)：基本安裝
date: 2021-04-22 19:10:33
categories: Hexo
tags: Hexo
---
安裝`Hexo`在全域環境，並使用`next`，此處使用的裝置以`Windows`環境為主。
<!--more-->
## install(全域安裝 Hexo)
```
npm install hexo-cli -g

# or

yarn add global hexo-cli
```

## init project & install next theme
```
hexo init project-name
<!-- 或是切到對應資料夾再進行 hexo init -->

cd project-name

yarn add hexo-theme-next
```
切到根目錄的`_config.yml`進行調整
```
theme: next
```
最後將`Next`預設的設定檔進行複製到根目錄，方便進行參數調整
```
cp node_modules/hexo-theme-next/_config.yml _config.next.yml
```

## 頁面載入速度改善
`Next`在`8`版之後，因為有載入時非同步的問題，所以需要調整一下
```
motion:
  async: true
```

## hot reload(熱更新)
每次我們改動`Hexo`文件時，我希望本地也能同步重新渲染，所以使用這一插件
```
yarn add hexo-browsersync
```


## scheme
打開自身所需的排版樣式，後續調整參數路徑皆在`themes/next`
```
# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini
```

## change favicon
在`source`底下建立`images`資料夾，並存放本地靜態圖片，同時調整參數
```
favicon:
  small: /images/favicon-pitt.png
  medium: /images/favicon-pitt.png
```

## avatar
```
avatar:
  # Replace the default image and set the url here.
  url: /images/avatar.jpg
```

## social
```
social:
  GitHub: https://github.com/wuzhe0912 || fab fa-github
```