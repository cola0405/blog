---
title: pip_problem
date: 2021-07-23 22:21:18
tags:
categories:
---



##### pyinstaller不是内部或外部命令，也不是可运行的程序或批处理文件

原因：

环境变量没有配置相关pyinstaller的路径

解决办法：

根据自己的python版本

把下面的路径添加到环境变量

```bash
../python39/Scripts
```

