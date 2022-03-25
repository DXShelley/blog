---
title: nginx 基本使用
tags:
  - ops
  - nginx
  - tool
categories:
  - ops
date: 2022-02-09 10:07:04
---

# nginx 



## 配置

### Nginx 实现 HTTP 自动跳转到 HTTPS 页面

建议在 Nginx 虚拟主机配置文件对应的网站配置段中增加跳转项 `if...`

```nginx
server
{
     listen 80;
     server_name www.websoft9.com;
     index readme.html index.html index.htm;
     root  /data/nas/www.websoft9.com;
     error_log /var/log/nginx/www.websoft9.com-error.log crit;
     access_log  /var/log/nginx/www.websoft9.com-access.log;
     include conf.d/extra/*.conf;  
    
    # HTTP to HTTPS
    if ($scheme = http) {
        return 301 https://$host$request_uri;
    } 

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/www.websoft9.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/www.websoft9.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot  
}
```

## 参考

[Nginx从安装到高可用，一篇搞定！](https://mp.weixin.qq.com/s/8Lmn8I0LDHKJgkNp-mT_nA)



[免费证书](https://certbot.eff.org/)



[nginx实践](https://support.websoft9.com/docs/linux/zh/webs-nginx.html#%E5%AE%89%E8%A3%85)

