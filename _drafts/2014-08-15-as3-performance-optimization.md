---
layout: post
title: AS3 & Starling 性能优化
---

### AS3 Base

* 乘法代替除法
* Array 和 Vector 用`for...i`, Object 和 Dictionary 用`for...each`和`for...in`
* 禁用不需要的功能. 如文本的选择, 显示对象的 MouseEvent
* 需反复控制对象显示状态时, 用`visible`控制, 而不是`removeChild`和`addChild`
* 尽量用位图缓存`isplayObject.cacheAsBitmap`, 特别对于矢量对象(如文本). 对需要频繁重绘的对象效果不大, 反之, 对重绘少移动多的对象效果显著
* 避免频繁调用对象属性, 建议把要用的属性暂存后再用. 如显示对象宽高/数组长度/数组下标...等
* 实例化对象的开销较大, 尽量重复使用, 而不要重复创建. 如使用对象池
* BitmapData 对象用完必须手动`dispose()`
* 事件用完必须手动清除, 否则会导致其关联对象无法回收


### Starling

* 尽量合并显示对象, 减少显示对象数量
* 若 Sprite 对象及其子对象是静态的, 则使用`flatten()`
* 不需要操作的对象就禁用`touchable`
* 不需要 Alpha 通道的显示对象, `blendMode`属性置为`BlendMode.NONE`
* 在不影响效果的情况下, 把 Image 对象的`smoothing`属性置为`TextureSmoothing.NONE`. 如果拉伸 Image 时边缘模糊透明, 是因为 smoothing 为`TextureSmoothing.BILINEAR`(默认值).
* 尽量用`dispatchEventWith()`代替`dispatchEvent()`
* 使用位图字体. 如果程序需要控制字体颜色的话, 纹理图片字必须为白色
* 使用纹理集. 纹理集把原本零碎纹理合在一起, 能大幅提升GPU的使用效率
* 纹理集应`高内聚, 低耦合`. 否则加载用不到的纹理会降低性能, 程度视耦合程度而定
* 同时使用到多个纹理集时, 尽量先使用完一个, 再使用另一个. 交替使用会导致纹理集重复绘制
* 不需要的纹理(集)必须手动销毁. 特别注意临时创建的纹理, 如:`Texture.fromColor()`


### 参考

* [优化 Flash Platform 的性能](http://help.adobe.com/zh_CN/as3/mobile/index.html)
* [Tuning Starling based games](http://villekoskela.org/2012/02/18/tuning-starling-based-games/)
