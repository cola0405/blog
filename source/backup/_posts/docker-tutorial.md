---
title: docker tutorial
date: 2021-06-19 08:55:16
tags:
categories:
---

#### docker install

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
DRY_RUN=1 sh ./get-docker.sh
sudo sh get-docker.sh
```



---

#### docker 导入文件

```bash
docker cp 你的文件路径 容器长ID:docker容器路径
```

```bash
docker cp /var/backup/nginx.zip 68b99:/cert
```

---

Docker 部署使用localhost时，一定要注意容器与容器，容器与主机之间的关系