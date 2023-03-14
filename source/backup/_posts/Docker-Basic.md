---
title: Docker Basic
date: 2021-03-28 12:49:35
tags:
categories:
---

start docker daemon

```
sudo service docker start
```

images list

```
docker images
```

delete images

```
docker rmi id
```

container status

```
docker ps -a
```

---

Container

run container

1.check images

```
docker images
```

2.run images and attach it

```
docker run -i -t rastasheep/ubuntu-sshd:18.04 /bin/bash
```

```
-t: 在新容器内指定一个伪终端或终端。

-i: 允许你对容器内的标准输入 (STDIN) 进行交互。
```

3.exit

```
exit
```

4.daemon model

```
docker run -itd --name ubuntu-test ubuntu /bin/bash
```

```
-d daemon
```

---



container operation 

```
docker start (container id)
docker stop (container id)
docker restart (container id)
```

---

Image

Reuse

1.export container

```
docker export 1e560fca3906 > ubuntu.tar
```

2.import 

```
cat ./ubuntu.tar | docker import - test/ubuntu:v1
```

```
docker import http://example.com/exampleimage.tgz example/imagerepo
```



---

