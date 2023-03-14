---
title: hexo数学公式
date: 2021-07-29 15:28:50
tags:
categories:
---





### 1.更换渲染引擎

```undefined
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```



### 2.配置文件

找到当前主题的 `_config.yml` 

```bash
mathjax:
  enable: true  ## 默认为false
```



### 3.渲染声明

渲染引擎只会渲染带声明的md

```bash
title: md数学公式
date: 2021-07-25 13:46:37
tags:
categories:
mathjax: true
```



