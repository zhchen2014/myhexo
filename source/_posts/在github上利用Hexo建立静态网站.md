title: 在github上利用Hexo建立静态网站
tags:
  - hexo
  - github
  - 记录
categories: 技术宅
date: 2015-06-09 20:01:35
---
#前言
相关的教程一搜一大把，我把最重要的部分提炼总结。这是一个信息过剩的时代，浓缩的才是精华啊。
想要自己架设一个网站已经有些日子了，前段时间想要使用`wordpress`甚至`织梦`来架设。但是由于其涉及数据库的复杂性，加上本人是个完美主义者，不相对彻底的搞明白其原理，怎么也不愿意使用，此事搁浅两年有余。如今又不少的东西希望能够分享，于是横下心好好学习一番。机缘巧合，在搜索wordpress资料的时候，恰好看到了所谓静态博客。两年前的不了了之不就是因为数据库不会弄吗，而且还要花钱租服务器和买域名。而静态博客恰好解决了上述矛盾，所有就有了这第一篇文章。

<!--more-->

# GitHub
##建立仓库
注册完账号后，建立仓库。
>Note:仓库的名字必须是`[yourusername].github.io`

建立完仓库后别忘了记下SSH地址，后面Hexo上传的时候会用到
>Note:SSH地址形如`git@github.com:[yourusername]/[yourusername].github.io.git`

##配置SSHkey
如果后面上传时候出现形如`Permission denied (publickey)`的错误说明你没有配置好SSHkey，所以这里最好就先检查一下。
查看是否存在`~/.ssh/id_rsa.pub`如果不存在则输入如下命令创建新key
``` bash
$ ssh-keygen
```
然后打开`~/.ssh/id_rsa.pub`，将其中的内容复制到GitHub上，有个SSHkey的地方，title无所谓。
至于多个GitHub的需要配置多个key的情况，需要生成多个公钥分别上传到GitHub上。然后在deploy的地方写清楚地址，并不会出现公钥选择错误的情况，虽然直接git好像确实会出错。

#Hexo
##Hexo安装
请查看[官方网站](http://hexo.io/zh-cn/)
##Hexo配置
在init之后，进入对应的目录。其主要的配置文件就是`_config.yml`，其中最重要的部分是`deploy`部分，这个部分表示你将要上传的仓库ssh地址，就是刚才前面提到要记下的SSH地址。配置如下：

``` 
deploy:
  type: git
  repository: git@github.com:[yourusername]/[yourusername].github.io.git
  branch: master
```
接下来就可以上传到网上测试了

``` bash
$ hexo g -d
```
当然也可以就在本地测试
``` bash
$ hexo generate
$ hexo server
```

##Hexo目录结构初步

* public:这个是上传到仓库之前的最后版本
* source:这里存储md格式的原始页面
* themes:主题以及外貌相关的css等配置文件
* scaffolds:这里是生成md文件的模版文件，也就是初始化md的文件的样子。

#后续
* 主题的引入，主要是本博客使用Jacman主题以及其修改
* 个性化的多说的评论设置

#更新记录
2015-06-09 初始版本
2015-06-10 更新前言，增加后续
