---
title: 树莓派
tags:
  - linux
  - pi
categories:
  - 未分类
date: 2022-02-28 09:55:53
---

# 树莓派



## 无网线无显示器环境下配置树莓派连接Wi-Fi开启ssh

### 连接wifi

在电脑中打开sd卡根目录创建名字为wpa_supplicant.conf 的文件。

```bash
country=CN
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
    ssid="12345678"
    psk="88888888"
    key_mgmt=WPA-PSK
    priority=1
}
```

### 开启ssh

在`boot`分区里新建一个名字为`ssh`的空文件，这样系统在启动的时候就可以识别出来，从而在开机的时候就开启`ssh`.



## 配置

```bash
raspi-config
```

