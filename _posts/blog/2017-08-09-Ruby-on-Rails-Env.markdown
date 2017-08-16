---
layout: post
title: ruby on rails 环境&libv8安装 -爬坑记
categories: Rails
description: 环境安装爬坑记。
keywords: 爬坑，ruby on rails
---

#### 前奏

本以为经过起步ror时装环境的经验，安装ror环境只是时间问题了，才发现自己高估自己了，在环境出错的情况下花了将近1天半时间才解决问题（离心态爆炸已经不远了），记录下来。

掉进坑里不可怕，掉进同样的坑里也不可怕，可怕的是掉进坑里出不来。  

ror环境的安装终归就几点（可以参考之前的文档）：  
1.rvm的安装：      不多写了，参考`https://www.rvm.io/`  
2.ruby的安装：    参考`https://ruby-china.org/wiki/rvm-guide`  
3.rails的安装  
4.bundler的安装   

#### 缓进

昨天因为遇到一个bug，网上提供一个解决方案运行bundle   update，结果改变了整机环境，稀里糊涂的弄了很久，真的心累    还好爬出坑了～  
整个安装的过程用的是之前自己安装ror时记录的文档，尴尬的是竟然安装不成功，一直不能运行，后来了解到是bundle update的时候改变了gemfile.lock文件，特意了解了gemfile和gemfile.lock两个文件的作用，总结如下：  
- Gemfile这个文件指定程序需要使用的哪些gem及其版本； 
- Gemfile.lock文件是Bundler记录已经安装了的版本的地方。通过这样的方式，当相同库/项目在另外一台机器上部署的时候，运行bundle install将会查看Gemfile.lock，然后安装同样的版本，而不是使用Gemfile以及安装最新的版本。（在不同的机器上运行不同版本会导致测试的失败……）你不需要直接地更改Gemfile.lock.  
所以很容易很轻松的把Gemfile.lock文件回退到之前的版本后再运行bundle install命令安装gems包时发现一路顺风，结果等了大半天还是报错哈哈哈哈
具体错误是libv8安装不成功，不过经过一天后看到的不是之前那个错后，心情还是相当的激动，赶紧搜查解决方案，结果发现也是坑的一批，如何坑就不赘述了，最后用的下面的方法解决

#### 过程

libv8安装：

![来自：https://stackoverflow.com/questions/27260199/libv8-3-16-14-3-fails-to-install-rails-4-1-8](http://upload-images.jianshu.io/upload_images/4755434-867313b3398e7ac2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

关于libv8的安装解决方案还有很多，恰巧这个解决了我的问题，还有一种思路：  

![来自：https://ruby-china.org/topics/22331](http://upload-images.jianshu.io/upload_images/4755434-40f51f9c33f64254.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

不过大同小异，能安装成功就行，如果想详细了解lbv8，可以去https://github.com/cowboyd/libv8。
吃一堑长一智，环境不要轻易手闲改动，热爱生命，远离环境安装。