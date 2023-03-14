---
title: Junit
date: 2022-04-29 17:38:22
tags:
categories:
---

# 为什么

代码迭代，一键测试









# Test时启动Spring Boot 应用

![image-20220429174147972](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20220429174147972.png)



```java
@RunWith(SpringRunner.class)
@SpringBootTest(classes = LpcsApplication.class)
public class AccountManageTest {

    @Resource
    AccountManageController accountManageController;

    MockMvc mockMvc;

    @Before
    public void setup() {
        mockMvc = MockMvcBuilders.standaloneSetup(accountManageController).build();
    }

    @Test
    @Transactional
    void addSubAccount() throws Exception {
        setup();
        MvcResult mvcResult = mockMvc.perform(MockMvcRequestBuilders.get("/account/manage/add/sub/account"))
                .andExpect(MockMvcResultMatchers.status().isOk())
                .andDo(MockMvcResultHandlers.print())
                .andReturn();
        System.out.println(mvcResult.getResponse().getContentAsString());
    }
}
```











