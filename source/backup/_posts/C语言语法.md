---
title: C语言语法
date: 2021-07-09 20:23:17
tags:
categories:
---

#### #define

> 以“#”开头的均为预处理指令

定义的标识符不占内存，只是一个临时的符号，预处理后这个符号就不存在了。



#### C程序编译运行的流程

![image-20210709202536371](https://gitee.com/simple_one1/pic/raw/master/image-20210709202536371.png)



#### Typeof

标识符

```c
typedef struct Books {
   char title[50];
   char author[50];
   char subject[100];
   int book_id;
} Book;
```

之后，把这个结构体命名成Book，以便之后直接使用

原结构体使用语法

```c
struct Books bookA = {"C 语言", "RUNOOB", "编程语言", 123456};
```

而后

```c
Book bookA = {"C 语言", "RUNOOB", "编程语言", 123456};
```

#### 初始化语句

```c
int a,b=1;
```

只是给b赋值了，a的还是声明，其值是随机的



