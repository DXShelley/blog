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

### 配置国内源

**注：对于系统版本不一样的，只需要将版本buster 改为相应的版本即可**

```bash
# 查看树莓派版本
pi@raspberrypi:~/downloads $ lsb_release -a
No LSB modules are available.
Distributor ID: Raspbian
Description:    Raspbian GNU/Linux 10 (buster)
Release:        10
Codename:       buster
pi@raspberrypi:~/downloads $ 
pi@raspberrypi:~/downloads $ vi /etc/apt/sources.list
pi@raspberrypi:~/downloads $ cat /etc/apt/sources.list
#deb http://raspbian.raspberrypi.org/raspbian/ buster main contrib non-free rpi
# Uncomment line below then 'apt-get update' to enable 'apt-get source'
#deb-src http://raspbian.raspberrypi.org/raspbian/ buster main contrib non-free rpi


deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi
# Uncomment line below then 'apt-get update' to enable 'apt-get source'
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi

pi@raspberrypi:~/downloads $ 
pi@raspberrypi:~/downloads $ vi /etc/apt/sources.list.d/raspi.list 
pi@raspberrypi:~/downloads $ cat /etc/apt/sources.list.d/raspi.list 
#deb http://archive.raspberrypi.org/debian/ buster main
deb http://mirrors.ustc.edu.cn/archive.raspberrypi.org/debian/ buster main ui
# Uncomment line below then 'apt-get update' to enable 'apt-get source'
#deb-src http://archive.raspberrypi.org/debian/ buster main
pi@raspberrypi:~/downloads $ 
pi@raspberrypi:~/downloads $ sudo apt-get update
Hit:1 http://mirrors.ustc.edu.cn/archive.raspberrypi.org/debian buster InRelease
Hit:2 http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian buster InRelease                                                                   
Hit:3 https://download.docker.com/linux/raspbian buster InRelease                                                                              
Reading package lists... Done                        
pi@raspberrypi:~/downloads $ 

```



```bash
# 各种国内源，配置一个就可以
/etc/apt/sources.list
#清华大学
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi

#中国科学技术大学
deb http://mirrors.ustc.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi
deb-src http://mirrors.ustc.edu.cn/raspbian/raspbian/ buster main contribnon-free rpi

#阿里云
deb http://mirrors.aliyun.com/raspbian/raspbian/ buster main contrib non-free rpi
deb-src http://mirrors.aliyun.com/raspbian/raspbian/ buster main contrib non-free rpi

#华中科技大学
deb http://mirrors.hustunique.com/raspbian/raspbian/ buster main contrib non-free rpi
deb-src http://mirrors.hustunique.com/raspbian/raspbian/ buster main contrib non-free rpi

/etc/apt/sources.list.d/raspi.list
#清华大学
deb http://mirrors.tuna.tsinghua.edu.cn/archive.raspberrypi.org/debian/ buster main ui

#中国科学技术大学
deb http://mirrors.ustc.edu.cn/archive.raspberrypi.org/debian/ buster main ui

#阿里云
deb http://mirrors.aliyun.com/archive.raspberrypi.org/debian/ buster main ui

#华中科技大学
deb http://mirrors.hustunique.com/archive.raspberrypi.org/debian/ buster main ui
```

## 使用

### 安装docker

1. 先配置好国内源-树莓派版的，其他的不好使
2. 

## 问题

1. 无法正常停止docker进程 原创

https://blog.51cto.com/wutengfei/2946943

## 参考

