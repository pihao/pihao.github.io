---
layout: post
title: git 本地仓库关联多个远程仓库
---

### 账户关联

要关联仓库, 必须要先关联账户. 比如 github, bitbucket, heroku...等等. 一般用 ssh-key 的方式. 关于 ssh-key 的本地操作, 可参考[ssh-key 管理][1].


### 创建仓库

这步主要针对本地仓库已经存在, 远程仓库还未创建的情况. 如果是 github, 在创建的时候要注意, 不要勾选`Initialize this repository with a README`, 否则 github 会初始化这个新仓库, 导致与本地仓库不一致. 如果是 bitbucket, 就不用注意什么选项, 直接创建即可.


### 关联

1. 在本地仓库中, 用命令`$ git remote add <remote-name> [url]`关联远程仓库. 例如:

    $ git remote add origin git@github.com:foo/bar.git
    $ git remote add bitbucket git@bitbucket.org:foo/bar.git

2. [可选]如果不同账户用的不同的 ssh-key, 那就需要配置`~/.ssh/config`(注意`IdentityFile`字段的值是私钥文件):

    Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa

    Host bitbucket.org
        HostName bitbucket.org
        User git
        IdentityFile ~/.ssh/id_rsa

至此, 关联两个远程仓库就完成了. 可用命令`git remote -v`来查看关联的所有远程仓库. 远程仓库的具体操作可参考阮一峰的这篇[Git远程操作详解][2], 或者去 git 官网看文档.


### 移除关联

移除命令:`$ git remote rm <remote-name>`. 例如:

    $ git remote rm origin
    $ git remote rm bitbucket


[1]: {{site.baseurl}}/2014/07/14/git-associated-multiple-remote-repos  "ssh-key 管理"
[2]: http://www.ruanyifeng.com/blog/2014/06/git_remote.html  "Git远程操作详解"
