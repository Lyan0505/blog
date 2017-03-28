---
title: vue2blog by github api
date: 2017-03-20 19:46:47  
tags: [vue, blog]
---

vue2 gh-pages blog

<!-- more -->


> 相信大家都折腾过自己的blog，从早期的wordpress，到现在可以用一些比较方便的hexo, jekyll来生成自己的静态博客，并且还能很方便的布署到github pages，这里就不详细介绍hexo,jekyll这些博客的玩法了，给个链接：[hexo搭建github pages个人博客](http://opiece.me/2015/04/09/hexo-guide/#发表一篇文章), [将GitHub关联到自己的域名](http://jingyan.baidu.com/article/dca1fa6fa1e403f1a5405262.html)，但是吧，我又是个喜欢折腾的人，在某个周末的下午，无意间看到一篇文章，可以通过 github 的 [api](https://developer.github.com/) 来获取自己仓库中的文章，并且在github中也搜到了此类开源项目，于是乎我也就开始动手用 vue-cli + github api + [Bmob](http://www.bmob.cn/)后端云来实现一个自己的博客。Bmob 为你提供了实时数据与文件存储功能，轻松实现应用“云与端”的数据连通。数据存储除了常规应用文本信息的存储，还可以存储图片、视频、音频、地理位置等信息。此外数据服务还内置用户系统、即时通讯、权限控制等，开发者几行代码即可实现快速集成。



### 1. 利用项目仓库的gh-pages分支展示项目

  首先我们在github建立一个新的仓库用来放置我们的代码，比如说仓库就叫 vue2-blog，然后我们在本地用脚手架搭一个博客框架--vue init webpack vueblog，ok，然后一些依赖安装，起服务的操作就不提了，接下来就把代码都推送到远程仓库的master分支，OK，然后我们到npm run build 打包这步，执行完打包程序后，关键一步：

	git subtree push --prefix=dist origin gh-pages

执行完以上代码，我们打包完的dist文件夹下的内容就被推送到了仓库的gh-pages分支，然后我们就可以使用 yourGithubName.github.io/仓库名/ 来访问演示内容啦。


### 2. TodoList

用户注册  （未完成）

用户登录  （已完成）

发送邮件   (已完成)

评论系统  （未完成）

点赞系统	 （未完成）

标签部分   （未完成）

分享部分   （未完成）


### 参考项目

mmf-blog-vue2: [https://github.com/lincenying/mmf-blog-vue2](https://github.com/lincenying/mmf-blog-vue2)

vue-ghpages-blog: [https://github.com/viko16/vue-ghpages-blog](https://github.com/viko16/vue-ghpages-blog)

