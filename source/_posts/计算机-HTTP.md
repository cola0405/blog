---
title: 计算机-HTTP
date: 2021-06-03 10:29:39
tags:
categories:
---



# Content-Encoding

```
浏览器发送请求时，通过 Accept-Encoding 带上自己支持的内容编码格式列表
服务端从中挑选一种用来对正文进行编码，并通过 Content-Encoding 响应头指明选定的格式
浏览器拿到响应正文后，依据 Content-Encoding 进行解压
内容编码目的是优化传输内容大小，通俗地讲就是进行压缩
```



Cache

```
Web页面设计中，建少HTTP请求可以提高页面响应速度。
浏览器在第一次访问页面时下载的资源会缓存起来
第二次访问时会判断在缓存中是否已有该资源并且有没有更新过
如果已有该资源且没有更新过，则去缓存去取
这样减少了下载资源的时间。
原理上是通过HTTP Rquest Header中的 if-modifaders中的last-modified来实现
```

