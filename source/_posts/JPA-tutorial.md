---
title: JPA tutorial
date: 2021-06-17 09:44:20
tags:
categories:
---

#### @Query

```java
@Query("SELECT u FROM User u WHERE u.status = ?1")
User findUserByStatus(Integer status);

@Query("SELECT u FROM User u WHERE u.status = ?1 and u.name = ?2")
User findUserByStatusAndName(Integer status, String name);
```

For the above queries, the *status* method parameter will be assigned to the query parameter with index *1,* and the *name* method parameter will be assigned to the query parameter with index *2*.

---

#### JPA 批量查询id

```java
    @Query(value = "select * from info where userid in ?1",nativeQuery = true)
    List<Info> getInfoByIds(List<Integer> userids);
```

