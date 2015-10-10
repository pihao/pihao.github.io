---
layout: post
title: protobuf 简介
---

### 什么是序列化

* 序列化：是指将结构化的数据按一定的编码规范转成指定格式的过程
* 反序列化：是指将转成指定格式的数据解析成原始的结构化数据的过程(就是反过来)

举个例子，Person 是一个表示人的对象类型，Person 是一个 Person 类型的对象，将 Person 存到一个对应的XML文档中的过程就是一种序列化，而解析XML生成对应 Person 类型对象 Person 的过程，就是一个反序列化的过程. 在这里结构化数据指的就是 Person 类型的数据，一定的编码规范指的就是XML文档的规范. XML 是一种简单的序列化方式，用 XML 序列化的好处是，XML 的通用性比较好，另外，XML 是一种文本格式，对人阅读比较友好，但是 XML 方式比较占空间，效率也不是很高. 通常，比较高效的序列化都是采用二进制方式的，将要序列化的结构化数据，按一定的编码规范，转成为一串二进制的字节流存储下来，需要用的时候再从这串二进制的字节流中反序列化出对应的结构化的数据.


### 什么是 protobuf

Google Protocol Buffers，简称 protobuf. 是Google制定的一种用来序列化结构化数据的程序库.

它轻便高效，可用于通讯协议、数据存储等领域的语言无关、平台无关、可扩展的序列化结构数据格式. 目前提供了 C++、Java、Python 三种语言的 API.


### AS3 与 GPB

Google 官方并不支持 AS3，可通过第三方库来实现.


### 参考

* [详解Google-ProtoBuf中结构化数据的编码](http://www.wuzesheng.com/?p=1258)
* [Google Protocol Buffer 的使用和原理](http://www.ibm.com/developerworks/cn/linux/l-cn-gpb/)
