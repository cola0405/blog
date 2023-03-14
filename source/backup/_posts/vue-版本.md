---
title: vue 版本
date: 2021-06-19 11:46:20
tags:
categories:
---

安装新的版本前，需要先把之前安装的版本卸载掉。

vue卸载：

```bash
npm uninstall vue-cli -g（3.0以下版本卸载）
npm uninstall -g @vue/cli（3.0以上版本卸载）
```



vue安装：

```bash
npm install -g @vue/cli （安装的是最新版）
npm install vue-cli@2.9.6 （指定版本安装【指定版本为3.0以下版本】，其中2.9.6为版本号）
npm install -g @vue/cli@3.11.0（指定版本安装【指定版本为3.0以上版本】，其中3.11.0为版本号）
```



vue版本查看：vue -V
————————————————
版权声明：本文为CSDN博主「IT_ms」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/IT_moshang/article/details/106470754