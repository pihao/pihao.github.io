---
layout: post
title: Starling 中纹理 repeat 的问题
---

在 Starling 中, 经常需要重复纹理. 你的代码可能是这样的:

{% highlight as3 %}
var tex:Texture = ...
var w:int = 300;
var h:int = 200;
var img:Image = new Image(tex);
img.texture.repeat = true;
img.setTexCoords(1, new Point(w / tex.width, 0));
img.setTexCoords(2, new Point(0, h / tex.height));
img.setTexCoords(3, new Point(w / tex.width, h / tex.height));
img.width = w;
img.height = h;
{% endhighlight %}

但运行得到的结果却不是想像中的那样. 其实代码没错, 而是素材有问题. 素材要注意以下两点:

1. 纹理必须是单独的. 否则就不是重复你要的那个纹理, 而是把旁边的纹理给你了. 试下便知.

2. 纹理的尺寸必须是2的N次幂. 否则 Starling 会取大于纹理尺寸的最小值. 比如纹理尺寸是`6*15`, 则 Starling 在 repeat 的时候会按`8*16`的尺寸来重复. 所以你会看到重复的图片之间有空隙, 就是这个原因造成的.


### Feathers 扩展方案

Feathers 包有个`feathers.display.TiledImage`类. 用它就没有上面两个限制.

    var tex:Texture = ....
    var img:TiledImage = new TiledImage(tex);
    img.width = 300;
    img.height = 200;


### 1.5.1 版本更新

Starling 1.5 版本的`repeat`变成了 ReadOnly 属性. 取厕代之的是在`Texture.fromEmbeddedAsset()`方法中的`repeat`参数. 即是说, 把 repeat 的设置转移到了这个接口中. 这样的用法比之前更加明了, 不会像之前, 用别的方法(非单独 Texture)取得的 Texture 在 repeat 后有"异常". 不过, 纹理的尺寸还是需要注意, 应为2的N次幂.

