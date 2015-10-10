---
layout: post
title: AIR 应用在 iphone5 上出现黑边解决办法
---

应用在 iphone4/ipad 上都正常, 但在 iphone5/iPod5 上出现黑边. 具体来说, 就是屏幕竖着, 在上下两端各有约 100px 高的黑色区域. 问题的关键是一张名为`Default-568h@2x.png`的图片. 针对不同的开发环境, 解决办法如下:

1. Flash Builder. 在`src`目录下放入一张尺寸为`1136*640`, 名称为`Default-568h@2x.png`的图片. 这样打包的程序在 iphone5 这样的屏幕上就正常了.
2. FlashDevelop. 使用最新版, 不会出现这个问题, 因为它的 Mobile 工程已默认创建了这些图片. 位置虽然与 FB 不同, 但打包时效果一样.
3. 如果手动编译, 记住一点: 加这张图片, 目的是让程序包的根目录持有这张图片. 只要的 ipa 包根目录中有这张图就OK(可以压缩软件查看包内容).

如果使用 Starling, 已经没问题了. 但如果用的原生代码写的应用, 下面这两个参数要注意, 不然显示也会有异常:

    stage.scaleMode = StageScaleMode.NO_SCALE;
    stage.align = StageAlign.TOP_LEFT;


### 参考

* [[AIR] Iphone5 上下不留黑边的解决办法](http://bbs.9ria.com/thread-224196-1-1.html)
* [iOS 启动图像](http://help.adobe.com/zh_CN/air/build/WS901d38e593cd1bac1e63e3d129907d2886-8000.html#WS901d38e593cd1bac58d08f9112e26606ea8-8000)
