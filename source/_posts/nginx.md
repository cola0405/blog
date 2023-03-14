---
title: nginx
date: 2022-04-28 13:37:19
tags:
categories:
---



nginx.conf 位置：`/etc/nginx/`

日志位置：`/var/log/nginx/`





简单部署就安装了简易版的

```
apt-get update
```



```
sudo apt install nginx-light
```



```
	  server{
          listen 8080;
          location / {
            root   /var/www/html/dist/;
            try_files $uri $uri/ /index.html;
           }
           location /api {
             proxy_pass http://40.72.185.138:8082/;
           }
        }
```

root 为dis解压后的目录

proxy_pass 是后端api的地址

第二个location的意思是

把/api的请求

转到40.72.185.138:8082/



Ps：8082后加不加斜杠，取决于vue里面怎么拼接



```
!qa # 不保存退出vi
```



```
sudo nginx -s reload
```



卸载nginx

```
sudo apt-get remove nginx nginx-common
sudo apt-get purge nginx nginx-common
sudo apt-get autoremove
sudo apt-get remove nginx-full nginx-common

```

