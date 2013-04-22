---
layout: post
title: "使用github+jekyll搭建blog环境"
category: tutorials
tagline: github pages
tags: [github, jekyll]
description: "如何使用github+jekyll搭建blog环境"
---
花了两天时间终于成功在github使用jekyll把blog搭建出来，来做个小结，以作后记

##好处、优点和入门
请直接移步[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

当然上面这个一个项目的Pages, 个人Pages的搭建方法：[这个是官方帮助](http://pages.github.com/)
个人pages与项目pages不同的是：需创建一个名字为`username.github.io`的仓库(注意：这个username必须为你的用户名),不再使用gh-pages分支，而是直接使用master分支，其他的都类似

当然你可以直接clone别人的blog，可以从[这里](https://github.com/mojombo/jekyll/wiki/Sites)选一个你喜欢的，还可以在[jekyll-bootstrap](http://jekyllbootstrap.com/)基础上搭建

###jekyll-bootstrap
[jekyll-bootstrap](http://jekyllbootstrap.com/)就是一个jekyll构建站点的demo，并提供了一些额外的api增强jekyll的功能，在此基础上构建站点相当快捷容易。除此之外，octopress也是基于jekyll上的不错的工具套件。

参考文章：
[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)
[基于jekyll的github建站指南](http://jiyeqian.github.io/2012/07/host-your-pages-at-github-using-jekyll/)
[GitPages官方帮助文档](http://pages.github.com/)
[jekyllbootstrap官方使用文档](http://jekyllbootstrap.com/)

最后再附上markdown的语法文档
[中文翻译](https://github.com/othree/markdown-syntax-zhtw/blob/master/syntax.md)
[英文原版](http://daringfireball.net/projects/markdown/syntax)