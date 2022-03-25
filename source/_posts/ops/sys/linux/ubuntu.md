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



## 配置

### Ubuntu20.04防火墙设置

Ubuntu20.04一般都默认安装了UFW（Uncomplicated Firewall），它是一款轻量化的工具，主要用于对输入输出的流量进行监控。如果没有安装，请用下面的命令安装：

```bash
# 查看防火墙状态
sudo ufw status verbose

sudo ufw app list

# 开启或关闭防火墙
sudo ufw enable | disable

# 外来访问默认允许/拒绝
sudo ufw default deny

sudo ufw allow | deny [service]


# 禁止或允许指定ip地址访问
sudo ufw deny from 203.0.113.100
sudo ufw allow from 203.0.113.101
# 禁止子网访问
sudo ufw deny from 203.0.113.0/24
特定ip地址可ssh连接
sudo ufw allow from 203.0.113.103 proto tcp to any port 22

sudo ufw allow https 
# 或
sudo ufw allow 443
# 允许入 http或者https的
sudo ufw allow proto tcp from any to any port 80,443

# 删除规则
sudo ufw delete allow from 203.0.113.101
```

### 更换阿里云软件源

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak    // 备份
sudo vim /etc/apt/sources.list      // 修改
// 进入source.list，更换为阿里云软件源

deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse

// 更新
sudo apt update     
sudo apt upgrade
```

| 命令                          | 描述                                                       |
| ----------------------------- | ---------------------------------------------------------- |
| apt autoclean                 | 将已删除软件包的.deb安装文件从硬盘中删除                   |
| apt clean                     | 同上，但会把已安装的软件包的安装包也删除掉                 |
| apt autoremove                | 删除为了满足其他软件包的依赖而安装，但现在不再需要的软件包 |
| apt remove [软件包名]         | 删除已安装的软件包（保留配置文件）                         |
| apt --purge remove [软件包名] | 删除已安装包（不保留配置文件）                             |
| sudo apt update               | 更新本地包数据库                                           |
| sudo apt upgrade              | 更新所有已安装的包（也可以使用 full-upgrade）              |
| sudo apt install ./<file>.deb | 安装官网已经提供了 Ubuntu 版本 .deb 安装文件               |

### 添加开机启动（服务或脚本）

系统启动时需要加载的配置文件

/etc/profile、/root/.bash_profile
/etc/bashrc、/root/.bashrc
/etc/profile.d/*.sh、/etc/profile.d/lang.sh
/etc/sysconfig/i18n、/etc/rc.local（/etc/rc.d/rc.local）

```bash
#/etc/rc.local 以及自定义脚本中都不能使用系统变量（比如 $HOME，原因在于其执行自定义脚本时并没有继承系统变量）
# 修改rc.local文件，在 exit 0 前面加入以下命令。保存并退出
sudo vi /etc/rc.local
sudo touch /etc/rc.local
sudo chmod 755 /etc/rc.local
sudo systemctl enable rc-local.service
```





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



### 字体缺失

字体缺失：可以去网上下载找资源，因为我是双系统，所以先去 Windows 系统，将 `C:/Windows/Fonts` 下的字体移动过来了

```bash
// Fonts字体包移动到 /usr/share/fonts/ 下

sudo mv Fonts字体包位置 /usr/share/fonts/

// 移动好了之后，通过以下方式安装字体

cd /usr/share/fonts/

sudo mkfontdir

sudo mkfontscale

sudo fc-cache
```



## 日志

```bash
=> /var/log/messages：常规日志消息
=> /var/log/boot：系统启动日志
=> /var/log/debug：调试日志消息
=> /var/log/auth.log：用户登录和身份验证日志
=> /var/log/daemon.log：运行squid，ntpd等其他日志消息到这个文件
=> /var/log/dmesg：Linux内核环缓存日志
=> /var/log/dpkg.log：所有二进制包日志都包括程序包安装和其他信息
=> /var/log/faillog：用户登录日志文件失败
=> /var/log/kern.log：内核日志文件
=> /var/log/lpr.log：打印机日志文件
=> /var/log/mail.*：所有邮件服务器消息日志文件
=> /var/log/mysql.*：MySQL服务器日志文件
=> /var/log/user.log：所有用户级日志
=> /var/log/xorg.0.log：X.org日志文件
=> /var/log/apache2/*：Apache Web服务器日志文件目录
=> /var/log/lighttpd/*：Lighttpd Web服务器日志文件目录
=> /var/log/fsck/*：fsck命令日志
=> /var/log/apport.log：应用程序崩溃报告/日志文件=> /var/log/syslog：系统日志=> /var/log/ufw：ufw防火墙日志=> /var/log/gufw：gufw防火墙日志

#使用tail，more，less和grep命令。
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot
```



## 参考

[安装国内firefox（国内账号必须）](http://www.cache.one/read/12550820)





