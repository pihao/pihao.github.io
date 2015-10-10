---
layout: post
title: Pow, A nice web server for rails development
---

[pow][1] 是用于 rails 的一个 webserver.  为什么用 pow 而不用 rails 自带的 server 呢? 因为 pow 不用重启. 比如更改表, 或者更改路由的时候.


### 安装配置

这里我们使用 [powder][2] 这个 gem 来管理 pow.

* 安装 powder: 在 Gemfile 中添加`gem 'powder'`(记得`bundle install`), 或者直接手动安装`gem install powder`
* 安装 pow: 执行`powder install`

在项目目录中创建`.rvmrc`文件来指定 ruby 版本. 填入:

    rvm 2.1

在项目目录中创建`.powrc`, 填入:

{% highlight bash %}
if [ -f "$rvm_path/scripts/rvm" ] && [ -f ".rvmrc" ]; then
    source "$rvm_path/scripts/rvm"
    source ".rvmrc"
fi
{% endhighlight %}


### 使用

在 rails 目录执行`powder open`即可在浏览器在打开项目页面. 使用命令`powder down`关闭 pow. 命令`powder help`可查看所有 powder 命令.


### Live log

* 跟踪log文件`tail -f log/development.log`
* powder 命令`powder applog`. 其实也是对 tail 命令的包装


[1]: http://pow.cx/  "Pow: Zero-configuration Rack server for Mac OS X"
[2]: https://github.com/Rodreegez/powder  "powder"
