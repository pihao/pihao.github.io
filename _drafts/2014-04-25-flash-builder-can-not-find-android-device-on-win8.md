---
layout: post
title: 解决 Window8 中 Flash Builder 调试找不到 Android 设备的问题
---

FB 找不到 Android 设备一般是 Android 驱动的原因。


### 安装驱动

首先, 按[Adobe官方提供的方法][1]安装驱动. 这里注意, 如果在`android_winusb.inf`文件中没有找到你的 Adnroid 型号, 就自己添加. 设备的硬件ID在设置管理器中去查(不知道自行Google), 然后按已有的格式在32位和64位都添加你的设备. 之后就即可安装驱动, 方式为:

1. 在设备管理器中右键选择 Android 设备
2. 选择"更新驱动程序软件..."
3. 浏览计算机以查找驱动程序软件
4. 选择`<Adobe Flash Builder 4.7 Home>\utilities\drivers\android\`目录安装


### 驱动安装失败

这里是关键, 在 XP 和 Win7 上应该是能安装成功的, 但在 Win8 上却提示`文件的哈希值不在制定的目录文件中。此文件可能已损坏或被篡改错误`这样的错误, 导致驱动无法安装. 这应该是 FB 提供的驱动还不支持 Win8, 所以只好强行安装:

1. 打开 Win8 设置
2. 搜索并选择"更改高级启动选项"
3. 选择"立即重启"

重启后的开机画面和平时不同, 依次选择:

1. 疑难解答
2. 高级选项
3. 启动设置
4. 禁用驱动程序强制签名

重启后再按上面的方法安装驱动, 安装完成后 FB 即可选择在设备上进行调试. 记得打开 Android 的开发选项.


### 参考

* [Adobe Flash Builder 4.7 * 连接 Google Android 设备][1]
* [解决 Windows 8 无法安装（Android）驱动][2]

[1]: http://help.adobe.com/zh_CN/flashbuilder/using/WSe4e4b720da9dedb5-2e7310a1136ab7c1811-7ff3.html#WSe4e4b720da9dedb5-2e7310a1136ab7c1811-7ff0  "Adobe Flash Builder 4.7 * 连接 Google Android 设备"
[2]: http://app.wepost.me/solve-can-not-install-android-drive-on-windows-8/  "解决 Windows 8 无法安装（Android）驱动"
