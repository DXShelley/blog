---
title: Ubuntu 基本使用
tags:
  - linux
  - ubuntu
categories:
  - 未分类
date: 2022-02-24 10:26:23
---



# Ubuntu



## 软件

### ping 和 ifconfig

```bash
apt-get install inetutils-ping
apt-get install net-tools
```



### Installing Apache2 / Nginx & Aria2



```bash
sudo apt install apache2 -y
sudo apt install nginx -y
sudo apt install aria2 -y


sudo rm -f /var/www/html/index.html; sudo mkdir /var/www/html/aria2

# 下载aria2WebUI
wget https://github.com/mayswind/AriaNg/releases/download/1.1.6/AriaNg-1.1.6-AllInOne.zip; sudo unzip AriaNg*.zip -d /var/www/html/aria2

sudo mkdir $HOME/.aria2; sudo touch $HOME/.aria2/aria2.conf

# It also require to start Aria2 as RPC-server as a background task, to do that you can use “screen” and “crontab“. You can install “screen” by executing:

sudo apt install screen -y

# 配置随系统启动aria2
crontab -e

# 追加
@reboot screen -d -m -S AriaRPC bash -c 'aria2c --enable-rpc --rpc-listen-all --rpc-allow-origin-all=true'

# 访问
192.168.1.105/aria2

```





## 参考

[安装国内firefox（国内账号必须）](http://www.cache.one/read/12550820)





