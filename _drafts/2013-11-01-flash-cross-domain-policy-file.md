---
layout: post
title: Flash跨域策略文件的使用说明
---

### 两种连接, 两种策略文件

AS 中的跨涉及两种服务器连接, URL 连接和 Socket 连接. 对应两种策略文件: URL 策略文件和 Socket 策略文件. 策略文件必须与连接方法相匹配.


### 主策略文件与其它策略文件

URL连接会默认在Web服务器根目录中查找名为`crossdomain.xml`的URL策略文件, Socket 连接默认在`843`端口和主 Socket 连接所在端口上查找 Socket 策略文件, 这些文件又称`主策略文件`.

SWF 文件可以通过调用`Security.loadPolicyFile()`方法检索其他策略文件名或其他目录位置. 但是, 如果主策略文件未指定目标位置能提供策略文件, 则调用`loadPolicyFile()`无效, 即使该位置有策略文件.

主策略文件包含一条`元策略`语句(permitted-cross-domain-policies). 元策略指定哪些位置可包含策略文件. URL 策略文件的默认元策略为`master-only`, 它表示 /crossdomain.xml 是服务器上唯一允许的策略文件. 套接字策略文件的默认元策略为`all`, 它表示主机上的任何套接字都能提供套接字策略文件. 当主策略文件中的元策略语为`master-only`时, 调用`Security.loadPolicyFile()`方法指定的其它策略文件不会生效.

故, 要想指定的其它策略文件有效, 要满足两个条件: 一是必须有主策略文件, 二是主策略文件中的元策略必须为`all`.


### 策略文件范围

URL 策略文件仅适用于从其中加载该文件的目录及其子目录. 根目录中的策略文件适用于整个服务器；而从任意子目录加载的策略文件仅适用于该目录及其子目录.

URL 策略文件仅影响对其所在特定服务器的访问. 例如, 位于`https://www.adobe.com:8080/crossdomain.xml`的策略文件仅适用于在端口`8080`通过`HTTPS`对`www.adobe.com`进行的数据加载调用.

Socket 策略文件没有目录这个概念, 因为它只涉及对某个端口的访问, 而不是针对某个目录.


### 策略文件的部署

对于 URL 连接, 需要部署 WEB 服务, 然后把策略文件放在对应的位置, 让 URL 连接能请求到这个文件即可.

对于 Socket 连接, 需要部署 Socket 服务, 监听对应的端口. 在端口收到请求时返回策略内容(xml 格式).


### 策略文件语法

    <cross-domain-policy>

        <!-- 元策略语句. 取值为: "all", "master-only", "none" -->
        <site-control permitted-cross-domain-policies="master-only"/>

        <!-- 各种域写法 -->
        <allow-access-from domain="*" to-ports="*"/>
        <allow-access-from domain="*.example.com" to-ports="*"/>

        <!-- 各种端口写法 -->
        <allow-access-from domain="*" to-ports="507" />
        <allow-access-from domain="*" to-ports="507,516" />
        <allow-access-from domain="*" to-ports="516-523" />
        <allow-access-from domain="*" to-ports="507,516-523" />

        <!-- 用IP时不能用通配符, 只有域和端口才可用 -->
        <allow-access-from domain="192.0.34.166" to-ports="*" />

    </cross-domain-policy>


### 参考

* [Flash安全性-加载数据](http://help.adobe.com/zh_CN/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c60.html)
* [权限控制-策略文件](http://help.adobe.com/zh_CN/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c85.html#WS5b3ccc516d4fbf351e63e3d118a9b90204-7e08)
* [策略文件语法 - Setting a crossdomain.xml file for HTTP streaming](http://www.adobe.com/devnet/adobe-media-server/articles/cross-domain-xml-for-streaming.html)
