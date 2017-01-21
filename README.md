---
title: 面试问题收藏
date: 2016-09-19 23:58:35
tags:
---
[TOC]

# 面试问题收藏
这些是我最近想到的一些问题，比较基础。回答的不一定完全准确，一些自己还不是很明白，需要思考学习。

# 计算机基础方面
## 网络
### TCP/IP协议是什么
TCP/IP是指由TCP、UDP、IP、ICMP等协议组成的协议簇
### TCP握手过程、关闭和状态变化，对应到程序中是哪些函数调用
常说的三次握手，四次挥手。还是用图来表示最清楚了。

### TCP是怎么保证可靠性的
超时重连
### TCP和UDP的区别
TCP: 面向连接，提供可靠性机制
UDP: 不保证可靠性
### IP层的作用
IP层负责主机路由
TCP层负责端到端的传输，主机上的每个程序都可以是一个端。用一个端口号表示
### tcpdump、wireshark使用
tcpdump -i eth1 tcp port 2222 and src 122.222.22
wireshark界面和命令行 

### ping命令使用了哪些协议
ICMP UDP
### ARP和RARP
ip和网卡地址的互相解析
### Connection reset by peer的原因, RST包发生的时机。
表示连接错误，一般发生的原因有

* 对方设置SO_LINGER为启用且到时了，对方会发送一个RST包，表示连接已经被重置，对方的端口不会表示成TIME_WAIT状态
* 中间如果有代理服务，代理服务可能会判断连接会话超时，同时向双方发送RST
* RST包: 在向一个没有监听的端口发送SYN时，也会返回 


### TCP 连接参数  TCP_NO_DELAY, TCP_KEEPALIVE, TCP_SO_LINGER
NO_DELAY是是否启用Nagle，TODO
### TCP延迟确认 200ms问题
TODO
### HTTP协议
文本传输协议
### HTTP请求过程。
DNS解析域名到ip映射
获得ip后通过ip和端口号请求
依次通过TCP、IP层
链路层传输到下一个主机，MAC地址是下一站的MAC地址
### DNS是什么
domain naming service
解析域名到ip地址
### HTTPS是什么，HTTPS握手过程，对称加密、非对称加密是什么，有哪些加密算法。
http over SSL/TLS

### NGINX是什么，负载均衡原理，负载均衡算法
反向代理、负载均衡

## 操作系统

### 操作系统的作用
### 进程作用，进程切换需要保存哪些内容
### 线程和协程
### 内核空间
### IO


## 数据结构
### 链表
### 树
### 倒排索引

## 算法
### 排序算法



## Java方面

### HashMap的内部实现
HashMap是Map的一个实现，内部数据结构通常是数组，数组的元素通常是链表，链表的元素是key-value的键值对。通过hash函数将key映射到一个hash值，这个hash值可以用来路由到具体的数组上。JDK8后会在链表长度达到一定长度后转换成一个红黑树。当HashMap存储的元素较多时，会造成链表比较长，这样get和put等操作的时间会增加，所以HashMap需要动态扩容，规则是HashMap中有一个capacity值和loadFactor值，现版本默认分别是16和0.75，capacity就是内部数组的大小，当Map的数据也就是键值对的数量超过capacity * loadFactor时就会进行resize或叫rehash，会创建一个2*capacity的数组，并将旧数组的内容转移到新数组上。

### HashMap、HashTable、ConcurrentHashMap
通常意义上讲HashMap不是线程安全的，HashTable是线程安全的，原因是HashMap中的并发resize()操作可能导致Node数据引用错误，甚至出现死循环，并且Node中的value和next没有使用volatile声明也没有其他加锁等可见性保证，所以在并发使用HashMap时必须要在外层加锁。HashTable解决了这个问题是通过将其对外方法上都加上了synchronized关键字在实例对象上加锁来维护数据一致性、可见性来实现线程安全的。但是即使是这样在putIfAbsent等操作还是需要外部加锁。由于HashTable将方法都加锁，导致操作都是串行执行的，性能不佳。ConcurrentHashMap是java.util.concurrent包中的一种并发集合，用来替代HashTable成为线程安全的HashMap，替代的是HashTable的线程安全语义而不是它的synchronize同步语义。ConcurrentHashMap中读不加锁，写入时采取分段锁，将锁的粒度拆小到每个数组上，这样大大减少了锁冲突，并且有Node中使用volatile等其他可见性保证。

### 常用的linux命令
#### 日常操作
* cp
* mv
* ls ll 
* grep
* |
* cat less head tail 
* vim 操作
* scp
* awk
* sort uniq
* nc


#### 监控类
* top
* uptime
* sar
* ps
* dstat
* vmstat
* iostat
* df
* du
* ss
* netstat
* lsof

### java的命令
jdk bin目录下的工具


## Java字节码、jvm相关

### jvm是什么，作用是什么 
java virtual machine
Java运行bytecode的地方，通过JVM抽象，可以实现平台无关性，一次编写到处运行(write once, run everywhere or write one, debug everywhere)
字节码这一层抽象也实现了语言无关性，只要能够编译出符合JVM规范的字节码，无论是scala、groovy等语言的代码都能在JVM上运行

### 收集器和垃圾收集算法


### 动态代理有哪些方式

### java运行时内存分布

### java class文件结构
* u2 magiccode
* u2 minor version
* u2 major version
* u2 constant pool count
* constant pool[constant pool count -1]
* access flag
* this class
* super class
* interface count
* [count] interfaces
* field count
* [count] fields
* method count
* [count] methods
* attributes


### java 字节码指令集包括哪些
#### 操作数栈与局部变量操作
* aload_0 
* astore_0
* iconst_0
* bipush 100
* pop
* swap
* dup, dup_x1
* inc
* getfield
* putfield
* getstatic
* putstatic


#### 方法调用
* invokestatic 调用静态方法
* invokevirtual 调用虚方法，动态分派
* invokespecial 调用构造器，私有方法，父类方法
* invokeinterface 调用接口方法
* invokedynamic java7增加的动态语言特性TODO

#### 运算
* iadd
* TODO

#### 流程控制
* goto
* ifcom TODO

#### 类操作
* new
* check instance
* cast TODO


### ClassLoader, Class关系，Class的加载、验证、准备、解析、初始化

### java 如何实现多态

### 如何实现动态加载、热部署

### 收藏资料
#### JRebel发布的
* [mastering java bytecode](https://github.com/liuzhengyang/interview/blob/master/mastering-java-bytecode.pdf)
* [do you really get classloader](https://github.com/liuzhengyang/interview/blob/master/do-you-really-get-classloaders.pdf)
* [Jrebel的实验室](http://zeroturnaround.com/rebellabs/)

## java语言

### java优点和缺点

### java集合框架有哪些类

### java并发集合框架，原子类，Executor

### AQS, Future, Lock, Semaphore等。

### Java线程状态

### 多线程的需要注意的地方
原子、可见性、重排序。
性能，死锁。
偏向锁、轻量级锁、自旋锁、重量级锁。
### 实现异步等待的方式


## IO
### 字节流的概念，网络中传输的都是字节流
### 字符集
### 文件操作
### BIO和NIO区别，阻塞的含义
read write
阻塞需要单独一个线程来负责一个连接，非阻塞可以更很少的线程来管理
### Channel, Selector, ByteBuffer
ServerSocketChannel, SocketChannel
SelectionKey
ByteBuffer clear, position, limit, flip, remaining等
* 推荐Doug Lea的nio.pdf *
### 异步IO
Future, Listener
### Netty
netty是什么
非阻塞的、事件驱动的快速网络开发框架，很快的开发出健壮高效的网络应用。
netty结构
大体包括Bootstrap启动模块
ChannelHandler 中实现我们的业务逻辑，或者一些Codec编码解码器
Channel 代表一个连接
ChannelPipeline, 每个Channel会有一个ChannelPipeline
ChannelHandlerContext， pipeline和handler关联起来
ByteBuf Netty里的ByteBuffer实现

### 收藏资料
* [Doug Lea的一个ppt](https://github.com/liuzhengyang/interview/blob/master/nio.pdf)
* 

### Jetty Tomcat
Servlet的作用，Servlet生命周期
Jetty结构，Jetty启动过程，一个请求从接收到返回的中间步骤

### Redis
redis 数据结构
redis 数据结构实现
redis cluster
redis 实现计数器
redis 实现缓存，缓存如何失效，缓存一致性，如何保证缓存和数据库的一致性
redis 实现发布订阅
redis 实现报警,判断一分钟达到阈值
## MQ
kafka,rabbitmq


## 延迟队列
rabbitmq、activemq, redis实现，beanstalk

## 日志收集监控

## Spring
### Spring是什么，Spring作用
### 常说的IOC和AOP是什么，作用。
### Spring 启动过程， Spring Bean加载过程和处理过程 BeanPostProcessor
### Spring如何实现生命式事务的
### Spring如何实现Aspect AOP的
### Spring MVC结构，一个http request在spring中是如何流转的
### spring boot 

## 数据库
### 事务是什么、作用
### 事务的几个特点 ACID
### mysql 存储引擎
### mysql默认隔离级别
### innodb 索引，B-Tree，B+Tree 结构
主键、索引、数据存储方式
### 索引的最左匹配原则、聚簇索引、非聚簇索引。覆盖索引。
### explain, full scan, tmp file. file sort. join .in.
### 字段选择，int, bigint, varchar, char, datetime
### 锁范围，行级锁，表级锁，锁索引。间隙锁(Gap).全表扫描




# 书籍记录
# 强烈推荐
* Java并发编程实践
* 深入理解Java虚拟机
* java虚拟机规范7、8
* 高性能mysql
* TCP/IP详解
* Netty In Action(英文版的)
* 计算机程序的构造与解释

# 推荐
* Clean Code( 代码整洁知道)
* EffectiveJava
* 重构( 我刚看了一点，羞愧，要补一补)
* Thinking In Java( 我刚看了一点，羞愧，要补一补)
* 代码大全

# 比较推荐的书籍
* 大型网站xxx（淘宝出的一些书，技术演进等等，能对互联网常用技术、发展有一个大概了解）
* Spring揭秘
* 
* 从Paxos到Zookeeper
* Go语言编程
* Java并发编程的艺术
* Docker的一些书(介绍用就可以了，主要靠实践)
* 深入分析javaWeb内幕

# 拓展视野的书籍
* 软技能
* 人月神话
*



# 选择读的书籍(一般推荐,有时间读一读)
* Java特种兵
* ElasticSearch服务器开发
* Spring 3.x 企业应用开发
* spring技术内幕



