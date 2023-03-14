---
title: JPA error
date: 2021-06-16 15:54:46
tags:
categories:
---



#### could not extract ResultSet

原因：

```
@Entity和数据库中的表字段对应不上
```

我的话是“温度”的字段英文拼错了

一边是temperature，一边是temperture，差了个a

一定要仔细对照一下

下划线是没有影响的，对应好就行

---

#### could not execute statement

原因：

```
字段定义的类型和@Entity有悖
```

---

#### 执行updte/delete

```java
    @Modifying
    @Query(value = "update tb_user set role = 'USER' where name = ?1")
    int unLockUser(String username);
```



---

#### Executing an update/delete query] with root cause

添加@Transactional注解