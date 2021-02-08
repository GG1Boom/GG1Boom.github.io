---
title: 使用github+Hexo搭建个人博客
date: 2021-01-16 18:00:08
tags: Hexo
categories: 博客
---



##为何要使用github

之前自己买过服务器，在服务器上搭建过博客

* 会有买服务器的额外支出
* 自己买的云服务器经常会有网络攻击
* 恢复以前版本只能依靠快照
* 需要一定的linux运维能力
* 自己在服务器上写博客需要一定的前端知识，hexo只需要会写MarkDown就行

（以上都是博客小白的观点，可能视野还比较狭隘，但目前自我感觉来看，还是依靠github搭建一个自己的博客更加方便实惠并且git也是每一个程序员需要掌握的知识）

<!--more-->

## Git入门基础

* 注册github不用讲了
* Git仓库也不用说，如果要使用gitpage记得仓库名用： ```用户名.github.io```
* 主要讲讲配置SSH,毕竟我也不是经常用到，怕以后忘了（其实就是现在已经忘了马上复习下）
  + 首先在电脑上安装[git Bash](https://git-scm.com/download/win)
  + 查看是否生成过SSH   ```cat ~/.ssh/id_rsa.pub```
  + 生成SSH  ```ssh-keygen -t rsa -b 4096 -C "your_email@example.com"``` ,```your_email@example.com```替换成你注册github的邮箱
* git clone
  - 第一次使用git,git会提示进行全局变量的设置：```git config --global user.name "  "```以及```git config --global user.email “”```
  - 找到喜欢的仓库直接 git clone SSH地址
* 可能用到的一些linux命令：
  - ```ls``` 查看当前目录下的文件
  - ```touch``` 创建文件
  - ```mkdir``` 创建文件夹
  - ```cd``` 进入文件夹
  - ```rm -rf``` 删除指定文件
* 把本地文件夹绑定到GitHub
  - 在GitHub创建一个和本地文件夹同名的*空仓库*
  - ```git init```将一个文件夹初始化为一个git仓库
  - ```git  remote -v```查看当前git仓库绑定的远程仓库。没有绑定的文件夹使用命令```git remote add origin 仓库地址```来绑定
  - Git提交三部曲：
    - git add -A
    - git commit -m " "
    - git push (origin main/dev)
  - 另外还有git pull多人开发时会会有远程仓库和本地仓库不一致的情况，比如远程仓库上文件是[A,B],本地是[B,C],这时就需要git pull一下
* 创建分支
  - 最开始默认的是main分支
  - 用 ```git branch dev``` 创建新的分支
  - ```git checkout dev```切换到dev分支
  - 也可以合成为一条命令 ```git checkout -b dev``` -b就是branch的意思

## GitPage

- 在仓库设置里找到gitpage的选项打开

- 选择分支master或者main，主题先不用配置

- 命名规则 ```用户名.github.io``` ，然后输入这个域名就可以直接浏览gitpage了

- 但是想要装逼点，可以设置下域名跳转：

  - ping一下自己的gitpage找到服务器地址，我自己没ping通自己的gitpage地址，显示ip地址127.0.0.1(本地ip)，也没找到原因，直接通过站长之家ping出来ip地址
  
- 在自己的域名解析管理中添加A记录和CNAME记录。
  
    ![1](F:\GG1Boom_Hexo\Hexo_blog\source\images\Hexo01.png)
  
  - 第三步：在github pages下面设置Custom domain为替换的域名
  - 第四步：在source文件夹里面添加一个CNAME文件，把域名写进去，不然每次```hexo d```后自定义域名都会失效，自己遇到的大坑，提交完后发现git page站点直接404了，以为不小心删了什么东西或者配置文件是不是出问题了找了半天错，发现自定义域名失效了。

## hexo的使用

- 执行命令：```hexo init blog``` ,创建有一个 博客文件夹

- 安装hexo:```npm install -g hexo-cli```，前提是需要自己安装[npm](https://nodejs.org/zh-cn/)

- 创建博客：```hexo new 博客名```

- 修改配置文件```_config.yml```设置

  ```config.yml
  theme: landscape
  
  deploy:
  
    type: git
  
    repository: 你的GitHub仓库地址
  
    branch: master
  ```

- hexo提交三部曲

  - hexo clean
  - hexo g
  - hexo d

