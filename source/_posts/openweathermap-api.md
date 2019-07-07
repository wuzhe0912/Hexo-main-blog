---
title: 實作：串接 OpenWeather API
date: 2019-06-26 23:00:17
tags:
  - JavaScript
  - API
---
實作串接 `OpenWeather API`。
<!--more-->
## 申請帳號
[OpenWeatherMap 官網](https://openweathermap.org/)
## 準備 `icon`
### `font awesome icon 4.7 cdn`
```
https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css
```
### `search icon`
```
<i class="fa fa-search" aria-hidden="true"></i>
```
### 寫入 `HTML`
```
<div class="center">
  <div class="container">
    <header>
      <div class="search">
        <input type="text" placeholder="Enter City Name" id="search-txt">
        <a href="#" id="search-btn"><i class="fa fa-search" aria-hidden="true"></i></i></a>
      </div>
    </header>
  </div>
</div>
```