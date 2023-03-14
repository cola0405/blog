---
title: Hexo Theme
date: 2021-03-08 21:32:10
tags:
- Hexo
categories:
- [Hexo]
---



Next主题

```
npm install hexo-generator-searchdb --save
```



_config.yml新增

```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```



在Next主题的配置文件

```
local_search:
  enable: true
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # unescape html strings to the readable one
  unescape: false
```

把local_search enable 置true就好了

```
hexo clean
hexo s
```



