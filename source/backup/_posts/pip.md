---
title: pip
date: 2021-03-27 19:34:20
tags:
categories:
---



```
pip install -r requirements.txt
```



update pip

```
python -m pip install --upgrade pip
```

use mirror

```
pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

```
pip install -r ./requirements.txt -i https://pypi.douban.com/simple/
```



```
报错
The repository located at pypi.douban.com is not a trusted or secure host and is being ignored. If this repository is available via HTTPS it is recommended to use HTTPS instead, otherwise you may silence this warning and allow it anyways with '--trusted-host pypi.douban.com'.
```

```
解决
将url中的http修改为https
```

```
Linux 下pip无法安装的，pip3支持
```



