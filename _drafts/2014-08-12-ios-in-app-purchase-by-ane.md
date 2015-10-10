---
layout: post
title: 使用 iOS In-App Purchase ANE 注意事项
---

* 在把一台 iOS 设备当作测试设备之前, 务必先退出自己的 App Store 和 Game Center 的账号. 否则开发过程中会出现各种问题.

* 应该使用向 Apple 申请的测试账号来登陆. 测试帐号运行在一个沙箱中, 能完全模拟真实环境. 注意, 不要把测试拿到真实环境中使用, 否则帐号有被封的危险.

* 事先检查设备网络, 免得中间出现问题不好找原因(ANE的错误提示很烂, 很难调试).

* 添加测试设备的 UDID, 准备好开发用的证书文件(.p12)和描述文件(.mobileprovision). 注意, 每次添加新的测试设备后都要重新生成描述文件, 否则新设备无效.

* 准备好 Apple 上的商品. 如商品状态, 商品类型, 核对商品 ID 等等.

* 使用 Adobe 官方提供的 ANE, 它们都包含在 [Adobe Gaming SDK][1] 包中. 用 Adobe Creative Clold 安装 SDK, 其实就是下载了一堆文件, 放在了默认的程序安装目录. 其中就包括了我们需要的 ANE 和相应的 API 文档. 这个 SDK 包里还有 Starling, AIR...等等, 这里用不到它们, 不用管. 可用 SDK 包中的 Demo 来测试和熟悉购买流程. 具体可参考[In App Purchase 详细介绍][2].


### 参考

* [Native extensions for Adobe AIR](http://www.adobe.com/devnet/air/native-extensions-for-air.html)
* [In App Purchase 详细介绍](http://www.cocoachina.com/iphonedev/sdk/2010/1125/2396.html)


[1]: https://creative.adobe.com/products/gaming-sdk  "Adobe Gaming SDK"
[2]: http://www.cocoachina.com/iphonedev/sdk/2010/1125/2396.html  "In App Purchase 详细介绍"
