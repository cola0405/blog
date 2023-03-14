---
title: Vue Tutorial
date: 2021-06-01 10:56:08
tags:
categories:
---



[官方介绍](https://blog.jetbrains.com/webstorm/2019/03/get-started-building-apps-with-vue-js-in-webstorm/)

# Vue目录结构

```bash
├── build                      // 构建相关  
├── config                     // 配置相关
├── src                        // 源代码
│   ├── api                    // 所有请求
│   ├── assets                 // 主题 字体等静态资源
│   ├── components             // 全局公用组件
│   ├── directive              // 全局指令
│   ├── filtres                // 全局 filter
│   ├── icons                  // 项目所有 svg icons
│   ├── lang                   // 国际化 language
│   ├── mock                   // 项目mock 模拟数据
│   ├── router                 // 路由
│   ├── store                  // 全局 store管理
│   ├── styles                 // 全局样式
│   ├── utils                  // 全局公用方法
│   ├── vendor                 // 公用vendor
│   ├── views                   // view
│   ├── App.vue                // 入口页面
│   ├── main.js                // 入口 加载组件 初始化等
│   └── permission.js          // 权限管理
├── static                     // 第三方不打包资源
│   └── Tinymce                // 富文本
├── .babelrc                   // babel-loader 配置
├── eslintrc.js                // eslint 配置项
├── .gitignore                 // git 忽略项
├── favicon.ico                // favicon图标
├── index.html                 // html模板
└── package.json               // package.json

```







![img](https://www.runoob.com/wp-content/uploads/2017/01/B6E593E3-F284-4C58-A610-94C6ACDAD485.jpg)

| build        | 项目构建(webpack)相关代码                                    |
| ------------ | ------------------------------------------------------------ |
| config       | 配置目录，包括端口号等。我们初学可以使用默认的。             |
| node_modules | npm 加载的项目依赖模块                                       |
| src          | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：assets: 放置一些图片，如logo等。components: 目录里面放了一个组件文件，可以不用。App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。main.js: 项目的核心文件。 |
| static       | 静态资源目录，如图片、字体等。                               |
| test         | 初始测试目录，可删除                                         |
| .xxxx文件    | 这些是一些配置文件，包括语法配置，git配置等。                |
| index.html   | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。       |
| package.json | 项目配置文件。                                               |

Webstorm项目构建工具

> By default, all the apps generated with the Vue CLI use the webpack dev server

Components

> Vue is a framework for building modularized front-end apps, so it considers files with the .vue extension as components.

> Components contain three sections for code: template (HTML), script (JavaScript or TypeScript), and styles (CSS or any stylesheet language).

App.vue

>The project template creates a file called *App.vue* which is the primary component that is attached to the root element defined in the Vue instance.

```vue
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld/>  // 创建好的组件可以当作自定义标签使用
  </div>
</template>

<script>  // 导入Helloworld组件，下面两步都不可少
import HelloWorld from './components/HelloWorld.vue' 

export default {
  name: 'App',
  components: {  
    HelloWorld
  }
}
</script>
```



# 数据传递

Helloworld.vue

```vue
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
```

> reveals the `msg` variable as a property (called `props`) of the component, and that is how the message data is passed into the HelloWorld component.

How to pass data

```vue
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Jim"/>
  </div>
</template>
```



访问assert内的文件

```html
<template>
  <div id="app">
    <img src="./assets/logo.png">
  </div>
</template>
```



---

export

```js
export default {
  name: 'App',  // 其他文件import当前vue时用的名字
}
```



main.js

```js
import Vue from 'vue'
import App from './App.vue'  // 从文件中导入App组件

Vue.config.productionTip = false  // 关闭生产模式

new Vue({  // 创建了vue实例
  render: h => h(App),
}).$mount('#app')

```

> The call to $mount('#app'); attaches the Vue instance to the root DOM element, which is an element with an id of “app”. You can find the root element inside of public\index.html

```html
  <body>
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
```

---

method

```vue
<script>
export default {
  name: 'HelloWorld',
  props: {
    // msg: String
  },
  data: function () {
    return {msg:"Welcome!"};  // msg is like variable name
  },
  methods:{
    changeMessage:function () {  // changeMessage is like method name, which is used for invoke
      this.msg="Welcome man";
    }
  }
}
</script>
```

```vue
<button v-on:click="changeMessage">Change Message</button>
```







localhost显示的首页



# 默认首页

其实就是 public 文件夹中的index.html

然后其用

```vue
<div id="app"></div>
```



# WebStorm与Vue

虽然最新版的前端开发利器WebStorm支持了Vue，但是大部分人的WebStorm依然是默认不支持Vue的老版本（比如之前的我），所以需要手动添加WebStorm对Vue的支持。要想让WebStorm支持Vue主要分两步，第一步是安装Vue.js插件，使得WebStorm能够对Vue语法进行提示；第二步是配置Vue模板，即快速创建Vue文件





# Vuex-Store

vuex的store 统一管理多个模块的数据，如：token，用户信息

如果没有必要，页面本身存储数据就行，不用存在Store里



# Typescript

![image-20220103200927673](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/to_upload/image-20220103200927673.png)





# Token

```js
LoginByUsername({ commit }, userInfo) {
  const username = userInfo.username.trim()
  return new Promise((resolve, reject) => {
    loginByUsername(username, userInfo.password).then(response => {
      const data = response.data
      Cookies.set('Token', response.data.token) //登录成功后将token存储在cookie之中
      commit('SET_TOKEN', data.token)
      resolve()
    }).catch(error => {
      reject(error)
    });
  });
}
```

cookie 储存服务器返回的token

则完成了保存用户的登录状态的功能

再设置Token有效期（Expires/Max-Age）为Session，即浏览器关闭即丢失

（也可以设置成1周）





# 钩子

与生命周期相关的被调函数

如：

```js
router.beforeEach((to, from, next) => {
  ...
})
```





# 权限验证

前端验证还是后端验证？

若后端验证，则每增加一个页面，后端就要动一下

若前端验证，则只在前端动就行

![image-20220103203722855](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/to_upload/image-20220103203722855.png)



# next()

放行，中断当前导航，执行新的导航







