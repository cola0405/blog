---
title: cpp 语法
date: 2022-03-03 13:08:52
tags:
categories:
---





# vector



## vector初始化

```cpp
vector<int> Arrs {1,2,3,4,5,6,7,8,9};
```





## vector指定区间

```cpp
vector<int> ans(record.begin(),record.begin()+n);
```







## vector插入元素到最前面的位置

```
record.insert(record.begin(),0);
```



## vector是否包含某元素

```cpp
auto it = find(wordList.begin(), wordList.end(), w1);
if(it == wordList.end()){
	cout << "w1不在wordList中" << endl;
}
else{
	cout << "w1在wordList中" << endl;
}
```

```cpp
if(!count(wordList.begin(), wordList.end(), w1)) { 
	// count(wordList.begin(), wordList.end(), w1) == 0；
	cout <<"w1不在wordList中" << endl;
}
else{
	cout <<"w1在wordList中" << endl;
}
```









# 数学运算

## 平方

```cpp
pow(x,y)
```





# 数据类型



## uint32_t

`unsigned` 32位`int`

 _t 表示这些数据类型是通过typedef定义的，而不是新的数据类型

也就是说，它们其实是我们已知的类型的别名



```cpp
typedef   signed          char int8_t;
typedef   signed short     int int16_t;
typedef   signed           int int32_t;
typedef   signed       __INT64 int64_t;
 
/* exact-width unsigned integer types */
typedef unsigned          char uint8_t;
typedef unsigned short     int uint16_t;
typedef unsigned           int uint32_t;
typedef unsigned       __INT64 uint64_t;
 
/* 7.18.1.2 */
/* smallest type of at least n bits */
/* minimum-width signed integer types */
typedef   signed          char int_least8_t;
typedef   signed short     int int_least16_t;
typedef   signed           int int_least32_t;
typedef   signed       __INT64 int_least64_t;
 
/* minimum-width unsigned integer types */
typedef unsigned          char uint_least8_t;
typedef unsigned short     int uint_least16_t;
typedef unsigned           int uint_least32_t;
typedef unsigned       __INT64 uint_least64_t;
 
/* 7.18.1.3 */
/* fastest minimum-width signed integer types */
typedef   signed           int int_fast8_t;
typedef   signed           int int_fast16_t;
typedef   signed           int int_fast32_t;
typedef   signed       __INT64 int_fast64_t;
 
/* fastest minimum-width unsigned integer types */
typedef unsigned           int uint_fast8_t;
typedef unsigned           int uint_fast16_t;
typedef unsigned           int uint_fast32_t;
typedef unsigned       __INT64 uint_fast64_t;
 
/* 7.18.1.4 integer types capable of holding object pointers */
#if __sizeof_ptr == 8
typedef   signed       __INT64 intptr_t;
typedef unsigned       __INT64 uintptr_t;
#else
typedef   signed           int intptr_t;
typedef unsigned           int uintptr_t;
#endif
 
/* 7.18.1.5 greatest-width integer types */
typedef   signed     __LONGLONG intmax_t;
typedef unsigned     __LONGLONG uintmax_t;
```

