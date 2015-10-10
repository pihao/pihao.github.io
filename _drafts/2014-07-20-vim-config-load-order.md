---
layout: post
title: vim 配置加载顺序(配置无效的原因之一)
---

如果你修改了 vim 配置后, 却无法生效. 就可能是配置被覆盖. 可是, 被谁覆盖呢? 你并不知道.


### :scriptnames

我们需要用到`:scriptnames`这条命令. 它会列出所有执行过的脚本名字, 并以它们的执行顺序排列. 你会发现你平时使用的那个配置文件就是其中之一. 在它之后执行的那些脚本, 都会对你的配置造成覆盖(只会覆盖相同项). 剩下的工作就是去检查那些脚本, 找到覆盖语句, 注释掉即可.


### :redir

附一个小技巧. 有时候我们需要把 vim 中命令执行的结果保存起来. 比如上面的`:scriptnames`. 那么`redir`命令有派上用场了. 以`:scriptnames`为例:

    :redir >~/foo.txt
    :scriptnames
    :redir END

执行完上面三条命令, 就可在`~/foo.txt`中看到`:scriptnames`命令的内容了.


### 参考

* [:scriptnames](http://vimdoc.sourceforge.net/htmldoc/repeat.html#:scriptnames)
* [:redir](http://vimdoc.sourceforge.net/htmldoc/various.html#:redir)
