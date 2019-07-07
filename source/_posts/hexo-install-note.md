---
title: Hexo 安裝筆記
date: 2019-01-02 10:28:37
tags: Hexo
---
記錄一下，自己安裝 Hexo 作為 Blog 的流程步驟。
<!--more-->
## 選擇主題
- [挑選 Hexo 主題網址](https://hexo.io/themes/)

選擇 Next 主題

```
cd 資料夾
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

修改網站設定_config.yml

```
theme: next
```

重新啟動 server

```
hexo s
```

## Scheme 設定
Next 有四種 Scheme 可以選擇，預設主題風格是 Muse。

在`themes/next/_config.yml`中找到 scheme 設定，再將想選擇的註釋去除即可。

個人選擇 Pisces。

```
# Schemes
# scheme: Muse
# scheme: Mist
scheme: Pisces
# scheme: Gemini
```

## 關於作者
新增大頭貼

建立存放圖片用的資料夾
```
mkdir source/image
```

將大頭貼的照片丟入資料夾`source/images`

接著在主題設定`themes/next/_config.yml`中，設定大頭貼路徑。

```
avatar:
  url: /images/avatar.jpeg
```

修改作者名稱

在`_config.yml`中設定姓名、標題和副標題
```
# Site
title: 無哲的隨手筆記
subtitle:
description:
keywords:
author: Pitt Wu
language: zh-tw
timezone:
```

## 動畫效果
Next 主題提供數種背景動畫效果，`themes/next/_config.yml`供使用者選擇。

```
e.g. 選擇 canvas_nest 這個效果

1. cd themes/next
2. git clone https://github.com/theme-next/theme-next-canvas-nest source / lib / canvas-nest
3. next/_config.yml 設定 enable: true
```

## Tags 分類
- 透過標籤將文章進行分類

新建一個頁面，用於保存所有 tag
```
hexo new page "tags"
```

接著將 type 設定為 "tags"
```
---
title: All tags
date: 2019-01-03 22:48:09
type: "tags"
---
```

之後，所有的文章皆能加入對應的標籤
e.g.
```
---
title: Hexo 安裝筆記
date: 2019-01-02 10:28:37
tags: Hexo
---
```

## 關於我
既然是 Blog 自然需要一頁 about 用於自我介紹。
```
hexo new page "about"
```
在`themes/next/_config.yml`中預設有 menu 欄位，將需要的欄位前方註解去除。
```
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  #categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```

## 開啟社群帳號連結
在`themes/next/_config.yml`中可以新增個人社群網站連結。
```
social:
  GitHub: https://github.com/wuzhe0912 || github
  E-Mail: mailto:kgb00128@gmail.com || Gmail
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
```

## 文章預覽
在`themes/next/_config.yml`中，可以透過字數設定來才切預覽。
```
auto_excerpt:
  enable: false
  length: 150
```
也可以透過`<!--more-->`來裁切，在`<!--more-->`以上的文字，會出現在預覽。

## 文章搜索
安裝插件
```
yarn add hexo-generator-searchdb
```
在根目錄的`_config.yml`中，添加下述內容
```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```
再到主題`themes/next/_config.yml`中設定為 true
```
local_search:
  enable: true
```
## 嵌入圖片
因為已經在根目錄中，將`post_asset_folder`設為 true，因此每次 new post 都會有對應的料夾。
為了便於管理，我們文章的圖片自然會放在對應的資料夾。

圖片嵌入的格式
```
{% asset_img space-select.png %}
```
## Google SEO (待添加)
獲取 Google Site Verification Code
登入[Google Search Console](https://search.google.com/search-console/about?hl=zh-TW&utm_source=wmx&utm_medium=wmx-welcome)，並輸入 Github-Page 網址。

在`themes/next/_config.yml`中填入驗證碼
```
google_site_verification: ooxx
```

安裝 sitemap 插件
安裝`hexo-sitemap-generator-sitemap`
```
yarn add hexo-generator-sitemap
# or
npm install hexo-generator-sitemap --save
```
在`_config.yml`中調整設定

## 右上角添加 Github Fork 圖片
在`themes/next/layout/_layout.swig`中，找到下述代碼：
```
<header id="header" class="header" itemscope itemtype="http://schema.org/WPHeader">
  <div class="header-inner">{% include '_partials/header/index.swig' %}</div>
</header>
```
並在 header 標籤下方添加 Github Corner 超連結樣式
```
<header id="header" class="header" itemscope itemtype="http://schema.org/WPHeader">
  <div class="header-inner">{% include '_partials/header/index.swig' %}</div>
  <a href="https://github.com/wuzhe0912" class="github-corner" target="_blank" title="Follow me on GitHub" aria-label="Follow me on GitHub">
    <svg width="80" height="80" viewBox="0 0 250 250" style="fill:#42b983; color:#fff; position: absolute; top: 0; border: 0; right: 0;" aria-hidden="true">
      <path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path>
      <path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path>
    </svg>
  </a>
</header>
```
再到`themes/next/source/css/_custom.styl`添加樣式代碼
```
/* GitHub Cornor */
.github-corner :hover .octo-arm {
    animation: octocat-wave 560ms ease-in-out;
}
@media (max-width: 991px) {
  .github-corner >svg {
    fill: #42b983 !important;
    color: #fff !important;
  }
  .github-corner .github-corner:hover .octo-arm {
    animation: none;
  }
  .github-corner .github-corner .octo-arm {
    animation: octocat-wave 560ms ease-in-out;
  }
}
@-moz-keyframes octocat-wave {
  0%, 100% {
    -webkit-transform: rotate(0);
    -moz-transform: rotate(0);
    -ms-transform: rotate(0);
    -o-transform: rotate(0);
    transform: rotate(0);
  }
  20%, 60% {
    -webkit-transform: rotate(-25deg);
    -moz-transform: rotate(-25deg);
    -ms-transform: rotate(-25deg);
    -o-transform: rotate(-25deg);
    transform: rotate(-25deg);
  }
  40%, 80% {
    -webkit-transform: rotate(10deg);
    -moz-transform: rotate(10deg);
    -ms-transform: rotate(10deg);
    -o-transform: rotate(10deg);
    transform: rotate(10deg);
  }
}
@-webkit-keyframes octocat-wave {
  0%, 100% {
    -webkit-transform: rotate(0);
    -moz-transform: rotate(0);
    -ms-transform: rotate(0);
    -o-transform: rotate(0);
    transform: rotate(0);
  }
  20%, 60% {
    -webkit-transform: rotate(-25deg);
    -moz-transform: rotate(-25deg);
    -ms-transform: rotate(-25deg);
    -o-transform: rotate(-25deg);
    transform: rotate(-25deg);
  }
  40%, 80% {
    -webkit-transform: rotate(10deg);
    -moz-transform: rotate(10deg);
    -ms-transform: rotate(10deg);
    -o-transform: rotate(10deg);
    transform: rotate(10deg);
  }
}
@-o-keyframes octocat-wave {
  0%, 100% {
    -webkit-transform: rotate(0);
    -moz-transform: rotate(0);
    -ms-transform: rotate(0);
    -o-transform: rotate(0);
    transform: rotate(0);
  }
  20%, 60% {
    -webkit-transform: rotate(-25deg);
    -moz-transform: rotate(-25deg);
    -ms-transform: rotate(-25deg);
    -o-transform: rotate(-25deg);
    transform: rotate(-25deg);
  }
  40%, 80% {
    -webkit-transform: rotate(10deg);
    -moz-transform: rotate(10deg);
    -ms-transform: rotate(10deg);
    -o-transform: rotate(10deg);
    transform: rotate(10deg);
  }
}
@keyframes octocat-wave {
  0%, 100% {
    -webkit-transform: rotate(0);
    -moz-transform: rotate(0);
    -ms-transform: rotate(0);
    -o-transform: rotate(0);
    transform: rotate(0);
  }
  20%, 60% {
    -webkit-transform: rotate(-25deg);
    -moz-transform: rotate(-25deg);
    -ms-transform: rotate(-25deg);
    -o-transform: rotate(-25deg);
    transform: rotate(-25deg);
  }
  40%, 80% {
    -webkit-transform: rotate(10deg);
    -moz-transform: rotate(10deg);
    -ms-transform: rotate(10deg);
    -o-transform: rotate(10deg);
    transform: rotate(10deg);
  }
}
```
重新啟動服務
```
hexo s
```

## 文章閱讀人數統計
參考諸多前輩的做法後，採用 LeanCloud 的服務。

[ LeanCloud ](https://leancloud.cn/)

建立一個新帳號後，進入控制台，創建一個新的應用。

點擊已創建的應用，會進入應用的控制頁面。

接著點選創建`Class`，選擇限制寫入

點選左側設置，進入應用 Key，複製 App ID 和 App Key，

並貼到`themes/next/_config.yml`
```
leancloud_visitors:
  enable: false
  app_id: #<app_id>
  app_key: #<app_key>
```


## 參考資源
[小蛇蛇的筆記](https://yogapan.github.io/)
[hoxis' blog](https://hoxis.github.io/)
[John Wu's Blog](https://blog.johnwu.cc/article/how-to-add-visitors-counter-on-hexo.html)