---
title: js 请求
date: 2021-06-18 21:00:14
tags:
categories:
---



#### POST 请求

```js
		   let username = document.getElementById('username').value
            let password = document.getElementById('password').value
            var httpRequest = new XMLHttpRequest();
            httpRequest.open('POST', 'http://localhost:8080/user/login_frontend', true)
            var formData = new FormData()
            formData.append("username",username)
            formData.append("password",password)
            httpRequest.send(formData);
```



#### 重定向和转发

重定向：服务器向浏览器发送一个302状态码以及一个location消息头，浏览器收到请求后会向重定向地址发出请求。

转发：一个web组件将未完成的处理通过容器转交给另一个web组件继续完成

---

#### Preflight

跨域请求可以正常发起，但是返回的结果被浏览器拦截了

为了防止这种情况的发生，规范要求，对这种可能对服务器数据产生副作用的HTTP请求方法，浏览器必须先使用`OPTIONS`方法发起一个预检请求，从而获知服务器是否允许该跨域请求：如果允许，就发送带数据的真实请求；如果不允许，则阻止发送带数据的真实请求。



---

####　jsonp

```js
	function addScriptTag(src) {
        var script = document.createElement('script');
        script.setAttribute("type","text/javascript");
        script.src = src;
        document.body.appendChild(script);
    }
```



通过插入script标签实现GET请求（不可POST）

src为请求地址，可携带params