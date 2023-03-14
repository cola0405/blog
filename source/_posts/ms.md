---
title: ms
date: 2023-01-28 09:59:33
tags:
categories:
---



















# 网络



## CDN

Content Delivery Network

内容分发网络





## 反向代理

用户不关心目标内部服务器的组成

只与反向代理的服务器交互

![](https://bkimg.cdn.bcebos.com/pic/3812b31bb051f81993dddee7d4b44aed2f73e7a7?x-bce-process=image/resize,m_lfit,w_440,limit_1)












## GET/POST

本质上都是`TCP`链接，并无差别

GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。



## HTTP

http明文

端口：80





https密文

端口：443







## 浏览器访问

URL解析 -- 协议、域名、端口、参数

DNS解析

TCP连接

页面渲染







## 三次握手和四次握手

建立连接需要三次

- 第一次握手：客户端发送网络包，服务端收到了
  这样服务端就能得出结论：客户端的发送能力、服务端的接收能力是正常的。
- 第二次握手：服务端发包，客户端收到了
  这样客户端就能得出结论：服务端的接收、发送能力，客户端的接收、发送能力是正常的。不过此时服务器并不能确认客户端的接收能力是否正常
- 第三次握手：客户端发包，服务端收到了。
  这样服务端就能得出结论：客户端的接收、发送能力正常，服务器自己的发送、接收能力也正常

通过三次握手，就能确定双方的接收和发送能力是正常的。之后就可以正常通信了





断开连接需要四次

- 第一次挥手：客户端发送一个 FIN 报文，报文中会指定一个序列号。此时客户端处于 FIN_WAIT1 状态，停止发送数据，等待服务端的确认
- 第二次挥手：服务端收到 FIN 之后，会发送 ACK 报文，且把客户端的序列号值 +1 作为 ACK 报文的序列号值，表明已经收到客户端的报文了，此时服务端处于 CLOSE_WAIT状态
- 第三次挥手：如果服务端也想断开连接了，和客户端的第一次挥手一样，发给 FIN 报文，且指定一个序列号。此时服务端处于 `LAST_ACK` 的状态
- 第四次挥手：客户端收到 FIN 之后，一样发送一个 ACK 报文作为应答，且把服务端的序列号值 +1 作为自己 ACK 报文的序列号值，此时客户端处于 TIME_WAIT状态。需要过一阵子以确保服务端收到自己的 ACK 报文之后才会进入 CLOSED 状态，服务端收到 ACK 报文之后，就处于关闭连接了，处于 CLOSED 状态





## TCP/IP

Transmission Control Protocol

Internet Protocol





![image-20230105151136518](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230105151136518.png)





TCP首部

![image-20230105151423008](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230105151423008.png)

https://blog.csdn.net/weixin_45160969/article/details/99240740



IP首部

![](https://img-blog.csdnimg.cn/img_convert/f857f25c39d64989330f76d9f9ab2096.png)





## WebSocket

实时通信

全双工

通信允许数据在两个方向上同时传输

```
ws://www.chrono.com
ws://www.chrono.com:8080/srv
wss://www.chrono.com:445/im?user_id=xxx
```



- 较少的控制开销：数据包头部协议较小，不同于http每次请求需要携带完整的头部
- 更强的实时性：相对于HTTP请求需要等待客户端发起请求服务端才能响应，延迟明显更少
- 保持创连接状态：创建通信后，可省略状态信息，不同于HTTP每次请求需要携带身份验证







# 工具

## Git

### git pull 和 git fetch

`git fetch`是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中

`git pull` 则是将远程主机的最新内容拉下来后直接合并

![image-20230105154407229](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230105154407229.png)







### branch 和 fork

- fork 只能对代码仓进行操作，且 fork 不属于 git 的命令，通常用于代码仓托管平台的一种“操作”（复制到自己的仓库）
- branch 得到的是一个代码仓的一个新分支，从开发主线上分离开来，以免影响开发主线







# Java







## 集合

主要是有四大块：List、Set、Queue、Map

![image-20230106102026894](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230106102026894.png)





### 为什么要有集合

数组的缺点是一旦声明之后，长度就不可变了；同时，声明数组时的数据类型也决定了该数组存储的数据的类型；

而且，数组存储的数据是有序的、可重复的，特点单一。 

但是集合提高了数据存储的灵活性，Java 集合不仅可以用来存储不同类型不同数量的对象，还可以保存具有映射关系的数据。







### ArrayList

底层是 object 数组

ArrayList会比Vector快，他是非同步的，如果设计涉及到多线程，还是用Vector比较好一些

线程不安全（非同步）



ArrayList基于数组的查询虽然高效，但增删数据的时候却很耗性能

因为每增删一个元素就要移动对应index后面的所有元素，数据量少点还无所谓

但如果存储上千上万的数据就很吃力了，所以，如果是频繁增删的情况，不建议用ArrayList



ArrayList扩容的时候，它会默认把数组的容量扩大到原来的1.5倍的

源码：

```java
private void grow(int minCapacity) {
        int oldCapacity = elementData.length;
        // 整句运算式的结果就是将新容量更新为旧容量的1.5倍，
        int newCapacity = oldCapacity + (oldCapacity >> 1);
        if (newCapacity - minCapacity < 0)
            newCapacity = minCapacity;
        if (newCapacity - MAX_ARRAY_SIZE > 0)
            newCapacity = hugeCapacity(minCapacity);
        // minCapacity is usually close to size, so this is a win:
        elementData = Arrays.copyOf(elementData, newCapacity);
    }
```







### ArrayList 和 LinkedList

- **是否保证线程安全：** `ArrayList` 和 `LinkedList` 都是不同步的，也就是不保证线程安全；
- **底层数据结构：** `ArrayList` 底层使用的是 **`Object` 数组**；`LinkedList` 底层使用的是 **双向链表** 数据结构（JDK1.6 之前为循环链表，JDK1.7 取消了循环。注意双向链表和双向循环链表的区别，下面有介绍到！）

- **插入和删除是否受元素位置的影响：**ArrayList基于数组的查询虽然高效，但增删数据的时候却很耗性能

​		因为每增删一个元素就要移动对应index后面的所有元素，数据量少点还无所谓

​		但如果存储上千上万的数据就很吃力了，所以，如果是频繁增删的情况，不建议用ArrayList

- **是否支持快速随机访问：** `LinkedList` 不支持高效的随机元素访问，而 `ArrayList` 支持。快速随机访问就是通过元素的序号快速获取元素对象(对应于`get(int index)`方法)。
- **内存空间占用：** `ArrayList` 的空 间浪费主要体现在在 list 列表的结尾会预留一定的容量空间，而 LinkedList 的空间花费则体现在它的每一个元素都需要消耗比 ArrayList 更多的空间（因为要存放直接后继和直接前驱以及数据）。







删除效率对比

```java
	// ArrayList:10
	// LinkedList:82
	// 数量到10,0000都是ArrayList删除速度快

	static void al(ArrayList<Integer> a){
        for(int i=50000; i<51000; i++){
            a.remove(i);
        }
    }

    static void ll(LinkedList<Integer> l){
        for(int i=50000; i<51000; i++){
            l.remove(i);
        }
    }

    public static void main(String[] args) {
        ArrayList<Integer> a = new ArrayList<>();
        for(int i=0; i<100000; i++){
            a.add(new Integer(i));
        }

        LinkedList<Integer> l = new LinkedList<>();
        for(int i=0; i<100000; i++){
            l.add(new Integer(i));
        }

        long startTime = System.currentTimeMillis();
        al(a);
        long endTime = System.currentTimeMillis();

        System.out.println("ArrayList:" + (endTime-startTime));

        startTime = System.currentTimeMillis();
        ll(l);
        endTime = System.currentTimeMillis();
        System.out.println("LinkedList:" + (endTime-startTime));
    }
```









```java
	// ArrayList:171
	// LinkedList:141
	// 数量上去100,0000之后LinkedList是比ArrayList快的

	static void al(ArrayList<Integer> a){
        for(int i=50000; i<51000; i++){
            a.remove(i);
        }
    }

    static void ll(LinkedList<Integer> l){
        for(int i=50000; i<51000; i++){
            l.remove(i);
        }
    }

    public static void main(String[] args) {
        ArrayList<Integer> a = new ArrayList<>();
        for(int i=0; i<1000000; i++){
            a.add(new Integer(i));
        }

        LinkedList<Integer> l = new LinkedList<>();
        for(int i=0; i<1000000; i++){
            l.add(new Integer(i));
        }

        long startTime = System.currentTimeMillis();
        al(a);
        long endTime = System.currentTimeMillis();

        System.out.println("ArrayList:" + (endTime-startTime));

        startTime = System.currentTimeMillis();
        ll(l);
        endTime = System.currentTimeMillis();
        System.out.println("LinkedList:" + (endTime-startTime));
    }
```





### LinkedList

ArrayList基于数组的查询虽然高效，但增删数据的时候却很耗性能

因为每增删一个元素就要移动对应index后面的所有元素，数据量少点还无所谓

但如果存储上千上万的数据就很吃力了，所以，如果是频繁增删的情况，不建议用ArrayList。

所以，一般建议LinkedList使用于增删多，查询少的情景。



![image-20230106113511020](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230106113511020.png)







### Vector

ArrayList会比Vector快，他是非同步的，如果设计涉及到多线程，还是用Vector比较好一些

可增长数组

```java
    public static void main(String[] args) {
        Vector v = new Vector();

        // 默认capacity是10
        // 但size是0
        System.out.println("default capacity: " + v.capacity());
        System.out.println("init size: " + v.size());

        // 允许重复，允许各种不同类型
        v.add(1);
        v.add(1);
        v.add(2);
        v.add(new Integer(2));
        v.add(new Integer(2));
        v.add(new Integer(2));

        // 遍历
        for(int i=0; i<v.size(); i++){
            System.out.println(v.get(i));
        }
        System.out.println("end");

        // 通过值或者index删除
        // Returns the element that was removed from the Vector
        // int类型时，java会认为是index
        // Integer时，java会认为是删除值
        v.remove(2);

        // 从左往右只删除一个
        v.remove(new Integer(2));

        for(int i=0; i<v.size(); i++){
            System.out.println(v.get(i));
        }
        System.out.println("end");

    }
```











## Kafka

这就好比BBC的记者，在知道皇马拿到欧冠冠军之后，拿起手机，翻开皇马球迷通讯录，给球迷一个一个打电话，告诉他们，皇马夺冠了。

事实上，BBC的记者只需要在他们官网发布这条消息，然后球迷自行访问BBC，去上面获取这条新闻；又或者球迷订阅了BBC，那么订阅系统会主动把发布在官网的消息推送给球迷。

同样，createOrder也需要一个像BBC官网那样的载体，也就是消息中间件，在订单创建完成之后，把一条主题为“orderCreated”的消息，放到消息中间件去就ok了，不必关心需要把这条消息发给谁。这就完成了消息的生产。





### demo

https://kafka.apache.org/downloads

找到2.1.0的版本

![image-20230116160611900](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230116160611900.png)

windows下修改配置文件：

config\zookeeper.properties

16行，自己新建一个文件夹、重写路径

```
dataDir=D:\\data\\kafka_data
```



config\server.properties

60行

```
log.dirs=D:\\data\\kafka_log
```





**启动zookeeper**

```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```



**启动kafka**

```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```



**创建名为 test1 的主题**

```
.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test1
```



**producer 发送信息**

```
.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic test1
```



consumer 接收信息

```
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test1 --from-beginning
```



然后在producer中发消息，完成demo







### Java的demo

首先是配置文件

```xml
	<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.7</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

	<properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
        <commons.version>5.0.7</commons.version>
        <junit.version>4.12</junit.version>
    </properties>



    <dependencies>
        <dependency>
            <groupId>org.springframework.kafka</groupId>
            <artifactId>spring-kafka</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.11</version>
        </dependency>

        <!-- 使用lombok打印日志 -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.24</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>


        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>${junit.version}</version>
        </dependency>

    </dependencies>
```





application.yml

```yaml
server:
  port: 8080

spring:
  application:
    name: kafkademo
  kafka:
    bootstrap-servers: localhost:9092
    producer:
      key-serializer: org.apache.kafka.common.serialization.StringSerializer
      value-serializer: org.apache.kafka.common.serialization.StringSerializer
    consumer:
      group-id: test
      enable-auto-commit: true
      auto-commit-interval: 1000
      key-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      value-deserializer: org.apache.kafka.common.serialization.StringDeserializer
```



这里要注意的是bootstrap-servers

应该在kafka服务器的 `config/producer.properties` 中找

```properties
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# see org.apache.kafka.clients.producer.ProducerConfig for more details

############################# Producer Basics #############################

# list of brokers used for bootstrapping knowledge about the rest of the cluster
# format: host1:port1,host2:port2 ...
bootstrap.servers=localhost:9092

# specify the compression codec for all data generated: none, gzip, snappy, lz4, zstd
compression.type=none

# name of the partitioner class for partitioning events; default partition spreads data randomly
#partitioner.class=

# the maximum amount of time the client will wait for the response of a request
#request.timeout.ms=

# how long `KafkaProducer.send` and `KafkaProducer.partitionsFor` will block for
#max.block.ms=

# the producer will wait for up to the given delay to allow other records to be sent so that the sends can be batched together
#linger.ms=

# the maximum size of a request in bytes
#max.request.size=

# the default batch size in bytes when batching multiple records sent to a partition
#batch.size=

# the total bytes of memory the producer can use to buffer records waiting to be sent to the server
#buffer.memory=

```



而不是 `server.properties` 中的2181



下面是具体的代码实现：

![image-20230116175159526](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230116175159526.png)



**producer**

```java
@RestController
@RequestMapping("/kafka")
public class PController {

    @Resource
    private KafkaTemplate<String, String> kafkaTemplate;
    
    @RequestMapping("/send")
    public String send(String msg) {
        // 消息的主题 test
        kafkaTemplate.send("test", msg);
        return "success";
    }

}
```





**consumer**

```java
@Component
@Slf4j
public class CController {
	// 一直监听着，一旦有produce，则会调用
    @KafkaListener(topics = "test")
    public void listen(ConsumerRecord<?,?> record) {
        Optional<?> kafkaMessage = Optional.ofNullable(record.value());
        log.info(">>>>>>>> record = " + kafkaMessage);
        if(kafkaMessage.isPresent()) {
            String topic = record.topic();
            long offset = record.offset();
            Object value = record.value();
            System.out.printf("topic = %s, offset = %d, value = %s \n", topic, offset, value);
        }
    }
}
```



main

```java
@SpringBootApplication
@RestController
public class KafkaDemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(KafkaDemoApplication.class, args);
    }


    //通过页面测试
    @RequestMapping(value = "/helloKafka",method = RequestMethod.GET)
    public String helloKafka(){
        return "helloKafka";
    }

    //也可模拟消息的发送，在启动项目时会发送消息
    @Resource
    private PController kafkaProducerController;
    @PostConstruct
    public void init() {
        for (int i = 0; i < 10; i++) {
            // 循环调用消息生产者的发送方法
            kafkaProducerController.send("i see kafka No." + String.valueOf(i));
        }
    }

}
```





测试，访问

```
http://localhost:8080/kafka/send?msg=hello
```









## 开放封闭原则

有新业务尽量能统一扩展（复用、调整）、不逐一修改





## 语法糖





### 变长参数

```java
public static void main(String[] args)
    {
        print("Holis", "公众号:Hollis", "博客：www.hollischuang.com", "QQ：907607222");
    }

public static void print(String... strs)
{
    for (int i = 0; i < strs.length; i++)
    {
        System.out.println(strs[i]);
    }
}
```



```java
// 反编译
public static void main(String args[])
{
    print(new String[] {
        "Holis", "\u516C\u4F17\u53F7:Hollis", "\u535A\u5BA2\uFF1Awww.hollischuang.com", "QQ\uFF1A907607222"
    });
}

public static transient void print(String strs[])
{
    for(int i = 0; i < strs.length; i++)
        System.out.println(strs[i]);

}
```





### 断言

```java
public class Test
{
  public static void main(String[] args)
  {
    int i = 10000;
    System.out.println(i);
  }
}
```

```java
//反编译
public class AssertTest {
   public AssertTest()
    {
    }
    public static void main(String args[])
{
    int a = 1;
    int b = 1;
    if(!$assertionsDisabled && a != b)
        throw new AssertionError();
    System.out.println("\u516C\u4F17\u53F7\uFF1AHollis");
    if(!$assertionsDisabled && a == b)
    {
        throw new AssertionError("Hollis");
    } else
    {
        System.out.println("\u535A\u5BA2\uFF1Awww.hollischuang.com");
        return;
    }
}

static final boolean $assertionsDisabled = !com/hollis/suguar/AssertTest.desiredAssertionStatus();
}
```



其实断言的底层实现就是 if 语言，如果断言结果为 true，则什么都不做，程序继续执行，如果断言结果为 false，则程序抛出 AssertError 来打断程序的执行







### for-each

```java
public static void main(String... args) {
    String[] strs = {"Hollis", "公众号：Hollis", "博客：www.hollischuang.com"};
    for (String s : strs) {
        System.out.println(s);
    }
    List<String> strList = ImmutableList.of("Hollis", "公众号：Hollis", "博客：www.hollischuang.com");
    for (String s : strList) {
        System.out.println(s);
    }
}
```



```java
//反编译
public static transient void main(String args[])
{
    String strs[] = {
        "Hollis", "\u516C\u4F17\u53F7\uFF1AHollis", "\u535A\u5BA2\uFF1Awww.hollischuang.com"
    };
    String args1[] = strs;
    int i = args1.length;
    for(int j = 0; j < i; j++)
    {
        String s = args1[j];
        System.out.println(s);
    }

    List strList = ImmutableList.of("Hollis", "\u516C\u4F17\u53F7\uFF1AHollis", "\u535A\u5BA2\uFF1Awww.hollischuang.com");
    String s;
    for(Iterator iterator = strList.iterator(); iterator.hasNext(); System.out.println(s))
        s = (String)iterator.next();

}
```







### lambda

```java
public static void main(String... args) {
    List<String> strList = ImmutableList.of("Hollis", "公众号：Hollis", "博客：www.hollischuang.com");

    strList.forEach( s -> { System.out.println(s); } );
}
```

```java
//反编译
public static /* varargs */ void main(String ... args) {
    ImmutableList strList = ImmutableList.of((Object)"Hollis", (Object)"\u516c\u4f17\u53f7\uff1aHollis", (Object)"\u535a\u5ba2\uff1awww.hollischuang.com");
    strList.forEach((Consumer<String>)LambdaMetafactory.metafactory(null, null, null, (Ljava/lang/Object;)V, lambda$main$0(java.lang.String ), (Ljava/lang/String;)V)());
}

private static /* synthetic */ void lambda$main$0(String s) {
    System.out.println(s);
}
```







### 自动装箱和拆箱

int转化为Integer叫做装箱

反过来则是拆箱



```java
 public static void main(String[] args) {
    int i = 10;
    Integer n = i;
}
```

```java
// 反编译
public static void main(String args[])
{
    int i = 10;
    Integer n = Integer.valueOf(i);
}
```





```java
public static void main(String[] args) {
    Integer i = 10;
    int n = i;
}
```

```java
// 反编译
public static void main(String args[])
{
    Integer i = Integer.valueOf(10);
    int n = i.intValue();
}
```







### 字面量

```java
public class Test {
    public static void main(String... args) {
        int i = 10_000;
        System.out.println(i);
    }
}
```





```java
public class Test
{
  public static void main(String[] args)
  {
    int i = 10000;
    System.out.println(i);
  }
}
```







## 设计模式

### 工厂模式

不暴露创建对象的具体逻辑，而是将将逻辑封装在一个函数中，那么这个函数就可以被视为一个工厂



```java
function Factory(career) {
    function User(career, work) {
        this.career = career 
        this.work = work
    }
    let work
    switch(career) {
        case 'coder':
            work =  ['写代码', '修Bug'] 
            return new User(career, work)
            break
        case 'hr':
            work = ['招聘', '员工信息管理']
            return new User(career, work)
            break
        case 'driver':
            work = ['开车']
            return new User(career, work)
            break
        case 'boss':
            work = ['喝茶', '开会', '审批文件']
            return new User(career, work)
            break
    }
}
let coder = new Factory('coder')
console.log(coder)
let boss = new Factory('boss')
console.log(boss)
```



当我们调用工厂函数时，只需要传递career就可以获取到包含用户工作内容的实例对象





### 抽象工厂

抽象工厂模式的工作就是生产工厂的

抽象工厂是接口类，写好接口，然后子类再具体对其进行实现





### 策略模式

说白了就是方法复用

不重复写同一功能的代码











## zookeeper

分布式协调服务

![image-20230116150903697](https://picgo-freejim.oss-cn-beijing.aliyuncs.com/image-20230116150903697.png)



