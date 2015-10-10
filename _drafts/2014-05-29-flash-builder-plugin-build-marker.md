---
layout: post
title: Flash Builder 版本插件 BuildMarker
---

在项目快速迭代过程中, 经常需要跟踪程序版本. 解决办法之一是在代码中写死版本号, 或者外部配置一个版本号, 编辑时嵌入. 使用这种方式, 必需要在每次发布之前手动更新版本号. 但在快速迭代时, 这个手动操作很容易被漏掉. 即使没有漏掉, 这也是一个很不人性化的方法. 因为每次发布都要分出精力来完成这项无脑的操作. 要是能让这个步骤自动完成, 那才是 Lifestyle.


### BuildMarker

[BuildMarker][1] 就是用来完成这个任务的.

BuildMarker 是 Flash Builder 的一个插件. 关闭 FB 后把插件jar包放到 FB 安装目录下的 dropins 目录即可. 工程在每次 build 或者 release 时会在工程目录下生成一个名为`.version`的 XML 文件, 里面包含了 build/release 的次数和时间.


### 其它

其实, BuildMarker 是一个 eclipse 插件, 只不过针对 Flash 的资源做了过滤, 所以在 FB 中才有效. 如果把过滤条件放开, 它将兼容所有 eclipse 工程.

这个插件本为 [snowkit][2] 所开发. 在 Mac 上使用时, `.version`文件生成异常: 在工程目录的上级目录生成文件`ProjectName\.verion`. 估计是路径中的反斜杠造成的. 因原项目已不再维护, 也无源码. 故反编译修复后, 放在 [Github][1] 上, 大家一起维护. 


[1]: https://github.com/kissyid/BuildMarker  "BuildMarker on Github"
[2]: https://code.google.com/p/buildmarker  "BuildMarker on Google code"
