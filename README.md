---
title: 面试问题收藏
date: 2016-09-19 23:58:35
tags:
---

# 面试问题收藏
这些是我最近想到的一些问题，比较基础，但是一些自己还不是很明白，需要思考学习。

# 计算机基础方面
## 网络
### TCP/IP协议是什么
### TCP握手过程、关闭和状态变化，对应到程序中是哪些函数调用
### TCP是怎么保证可靠性的
### TCP和UDP的区别
### IP层的作用
### tcpdump、wireshark使用
### HTTP请求过程。
### ping命令使用了哪些协议
### Connection reset by peer的原因, RST包发生的时机。 
### TCP 连接参数  TCP_NO_DELAY, TCP_KEEPALIVE, TCP_SO_LINGER
### TCP延迟确认 200ms问题
### HTTP协议
### DNS是什么
### HTTPS是什么，HTTPS握手过程，对称加密、非对称加密是什么，有哪些加密算法。
### NGINX是什么，负载均衡原理，负载均衡算法

## 操作系统

### 操作系统的作用
### 进程作用，进程切换需要保存哪些内容
### 线程和协程
### 内核空间
### IO


## 数据结构

## 算法



## Java方面

### 常用的linux命令

### java的命令
jdk bin目录下的工具


## Java字节码、jvm相关

### 如何实现动态加载、热部署

### jvm是什么，作用是什么 

### 收集器和垃圾收集算法

### 动态代理有哪些方式

### java运行时内存分布

### java class文件结构

### java 字节码指令集包括哪些

### ClassLoader, Class关系，Class的加载、验证、准备、解析、初始化

### java 如何实现多态

### 收藏资料
JRebel发布的
[mastering java bytecode](https://github.com/liuzhengyang/interview/blob/master/mastering-java-bytecode.pdf)
[do you really get classloader](https://github.com/liuzhengyang/interview/blob/master/do-you-really-get-classloaders.pdf)
[Jrebel的实验室](http://zeroturnaround.com/rebellabs/)

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
ByteBuf netty里的ByteBuffer实现

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
### 
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

