---
title: NVM 環境設定與指令
date: 2021-05-01
tags: NVM
---
記錄常用`NVM`指令與不同環境下的安裝方式。
<!--more-->
## install

### Mac
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

### Winodws
[下載 nvm-setup.zip 進行解壓縮安裝](https://github.com/coreybutler/nvm-windows/releases/tag/1.1.7)

### check version
```
nvm --version
```

## command
```
nvm ls-remote # 查看遠端 Node 版本列表(Windows 環境不可用)

nvm list # 查看本地 Node 已安裝版本列表

nvm install 12.22.1 # 安裝指定 Node 版本

nvm use 12.22.1 # 切換到使用的 Node 版本

nvm alias default 12.22.1 # 設定預設使用的 Node 版本
```

## Error Fixed(Mac)
> 此前進行硬體設備調整時，造成環境跑掉，記錄自己遇到的概況與解法。
打開終端機出現下述`error`:
```
nvm is not compatible with the npm config “prefix” option: currently set to “/Users/xxx/.nvm/versions/node/v8.12.0"
Run `npm config delete prefix` or `nvm use --delete-prefix v8.12.0 --silent` to unset it.
```
從字面上來看，應該是`npm`和`nvm`管理的`node`版本沒有對上，按照終端機提供的訊息，敲入對應指令。再檢查`node`版本似乎是正常了，但事實上，若另開終端機分頁，依然會跳相同的提示錯誤。雖然不影響操作，但看到總是不順眼，`google`了一下解法，最終測試成功方案如下：
```
npm config delete prefix
npm config set prefix $NVM_DIR/versions/node/v8.12.0
```
先刪除`npm`中設定的`prefix`，再重新設定當前`nvm`使用的版本。