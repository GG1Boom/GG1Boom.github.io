---
title: nexT心得
date: 2021-01-14 03:53:09
tags: nexT
categories: 博客
---

# 下载next主题

[Hexo](https://hexo.io/zh-cn/) 是高效的静态站点生成框架，它基于 [Node.js](https://nodejs.org/)。 通过 Hexo 你可以轻松地使用 Markdown 编写文章，除了 Markdown 本身的语法之外，还可以使用 Hexo 提供的 [标签插件](https://hexo.io/zh-cn/docs/tag-plugins.html) 来快速的插入特定形式的内容。

> 你可以访问 [Hexo 的文档](https://hexo.io/zh-cn/docs/) 了解如何安装 Hexo,之后我也会再简单写一下如何安装hexo,和国内下载hexo中遇到的一些坑。

<!--more-->

##下载方法一：

我先是尝试了用git clone，可能是最近加速器出了点问题，运营商快跑路了。

在hexo文件夹内使用命令```git clone https://github.com/iissnan/hexo-theme-next themes/next```

此方法失败

---



##下载方法二：

1. 前往 NexT 版本 [发布页面](https://github.com/iissnan/hexo-theme-next/releases)。
2. 选择你所需要的版本，下载 Download 区域下的 Source Code (zip) 到本地。例如，下载 v0.4.0 版本： ![next-releases](https://theme-next.iissnan.com/uploads/five-minutes-setup/download-stable-version.png)
3. 解压所下载的压缩包至站点的 themes 目录下， 并将 解压后的文件夹名称（`hexo-theme-next-0.4.0`）更改为 `next`。



与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开hexo的 **_config.yml**， 找到 `theme` 字段，并将其值更改为 `next`。

启用 NexT 主题

```
theme: next
```

# 设定主题

##选择 Scheme

Scheme 是 NexT 提供的一种特性，借助于 Scheme，NexT 为你提供多种不同的外观。同时，几乎所有的配置都可以 在 Scheme 之间共用。目前 NexT 支持三种 Scheme，他们是：

- Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
- Mist - Muse 的紧凑版本，整洁有序的单栏外观
- Pisces - 双栏 Scheme，小家碧玉似的清新

Scheme 的切换通过更改next中的 **主题配置文件**"_config.yml"，搜索 scheme 关键字。 你会看到有三行 scheme 的配置，将你需用启用的 scheme 前面注释 `#` 去除即可。

选择 Pisces Scheme

```
#scheme: Muse
#scheme: Mist
scheme: Pisces
```

# 设置菜单

菜单配置包括三个部分，第一是菜单项（名称和链接），第二是菜单项的显示文本，第三是菜单项对应的图标。 NexT 使用的是 [Font Awesome](http://fontawesome.io/) 提供的图标， Font Awesome 提供了 600+ 的图标，可以满足绝大的多数的场景，同时无须担心在 Retina 屏幕下 图标模糊的问题。

编辑 **主题配置文件**，修改以下内容：

1. 设定菜单内容，对应的字段是 `menu`。 菜单内容的设置格式是：`item name: link`。其中 `item name `是一个名称，这个名称并不直接显示在页面上，她将用于匹配图标以及翻译。

   菜单示例配置

   ```
   menu:
     home: /
     archives: /archives
     #about: /about
     #categories: /categories
     tags: /tags
     #commonweal: /404.html
   ```

   若你的站点运行在子目录中，请将链接前缀的 `/` 去掉

   NexT 默认的菜单项有（除了首页和归档都需要手动创建页面）：

   如手动创捷categories页面，在hexo文件夹中输入命令```hexo new page categories```

   然后在*Hexo_blog\source\categories*中打开index.md文件加上```type: categories```

   | 键值       | 设定值                    | 显示文本（简体中文） |
   | :--------- | :------------------------ | :------------------- |
   | home       | `home: /`                 | 主页                 |
   | archives   | `archives: /archives`     | 归档页               |
   | categories | `categories: /categories` | 分类页               |
   | tags       | `tags: /tags`             | 标签页               |
   | about      | `about: /about`           | 关于页面             |
   | commonweal | `commonweal: /404.html`   | 公益 404             |

2. 设置菜单项的显示文本。在第一步中设置的菜单的名称并不直接用于界面上的展示。Hexo 在生成的时候将使用 这个名称查找对应的语言翻译，并提取显示文本。这些翻译文本放置在 NexT 主题目录下的 `languages/{language}.yml` （`{language}` 为你所使用的语言）。

   以简体中文为例，若你需要添加一个菜单项，比如 `something`。那么就需要修改简体中文对应的翻译文件 `languages/zh-Hans.yml`，在 `menu` 字段下添加一项：

   ```
   menu:
     home: 首页
     archives: 归档
     categories: 分类
     tags: 标签
     about: 关于
     search: 搜索
     commonweal: 公益404
     something: 有料
   ```

3. 设定菜单项的图标，对应的字段是 `menu_icons`。 此设定格式是 `item name: icon name`，其中 `item name` 与上一步所配置的菜单名字对应，`icon name` 是 Font Awesome 图标的 名字。而 `enable` 可用于控制是否显示图标，你可以设置成 `false` 来去掉图标。

   菜单图标配置示例

   ```
   menu_icons:
     enable: true
     # Icon Mapping.
     home: home
     about: user
     categories: th
     tags: tags
     archives: archive
     commonweal: heartbeat
   ```

   在菜单图标开启的情况下，如果菜单项与菜单未匹配（没有设置或者无效的 Font Awesome 图标名字） 的情况下，NexT 将会使用 作为图标。

   请注意键值（如 `home`）的大小写要严格匹配
   
   # 设置语言
   
   编辑 **站点配置文件**， 将 `language` 设置成你所需要的语言。建议明确设置你所需要的语言，例如选用简体中文，配置如下：
   
   ```
   language: zh-Hans
   ```
   
   遇到的坑： 在新版本中好多没有zh-Hans.yml这个配置文件是zh-CN.yml这个文件，但是使用zh-CN没有任何作用，甚至可能乱码。于是在hexo文件夹（不是next)中找到```zh-CN.yml```这个文件重命名为```zh-Hans.yml```，最后```hexo clean```一下就好了
   
   # 首页文章截断
   
   刚配置完，发表的文章会在首页显示全部内容，会显得首页特别冗长。
   
   可以在编写markdown文档的时候使用```<!--more-->```截断。
   
   # 设置头像
   
   编辑 **主题配置文件**， 修改字段 `avatar`， 值设置成头像的链接地址。其中，头像的链接地址可以是：
   
   | 地址             | 值                                                           |
   | :--------------- | :----------------------------------------------------------- |
   | 完整的互联网 URI | `http://example.com/avatar.png`                              |
   | 站点内的地址     | 将头像放置主题目录下的 `source/uploads/` （新建 uploads 目录若不存在） 配置为：`avatar: /uploads/avatar.png`或者 放置在 `source/images/` 目录下 配置为：`avatar: /images/avatar.png` |
   
   # 设置浏览人数统计和评论系统
   
   最开始我是在一个大佬的next主题博客看到评论系统Disqus，但是不是很喜欢那种风格，然后知乎了一些：
   
   - Github大礼包：[gitment](https://link.zhihu.com/?target=https%3A//github.com/iissnan/hexo-theme-next/issues/1604)， [gitalk](https://link.zhihu.com/?target=https%3A//github.com/iissnan/hexo-theme-next/pull/2037)**（推荐），**[gitter](https://link.zhihu.com/?target=https%3A//www.vincentqin.tech/2016/08/09/build-a-website-using-hexo/%23%E5%A2%9E%E5%8A%A0Gitter)**（推荐）;** 三个都支持**Markdown；**
   - 基于leancloud的无后端评论系统：[Valine](https://link.zhihu.com/?target=https%3A//valine.js.org/%23/)**（推荐，**支持**Markdown）；**
   - 国外的有几个：[disqus](https://link.zhihu.com/?target=http%3A//www.disqus.com/)(漂亮，但需翻墙)，[hypercomments](https://link.zhihu.com/?target=https%3A//www.hypercomments.com/)**（推荐，**不支持**Markdown）.**
   
   最后我选择了Valine,它的评论管理需要登录leancloud。
   
   我们先来设置下这个评论系统
   
   ## 评论系统
   
   ### 获取APP ID 和 APP Key
   
   请先[登录](https://leancloud.cn/dashboard/login.html#/signin)或[注册](https://leancloud.cn/dashboard/login.html#/signup) `LeanCloud`, 进入[控制台](https://leancloud.cn/dashboard/applist.html#/apps)后点击左下角[创建应用](https://leancloud.cn/dashboard/applist.html#/newapp)：
   
   ![img](https://i.loli.net/2019/06/21/5d0c995c86fac81746.jpg)
   
   应用创建好以后，进入刚刚创建的应用，选择左下角的`设置`>`应用Key`，然后就能看到你的`APP ID`和`APP Key`了：
   
   ![img](https://i.loli.net/2019/06/21/5d0c997a60baa24436.jpg)



next特别好的一点，_config.yml中有valine的配置信息。

ctrl+F在编辑器中查找valine,找到valine的配置信息。

![valine](/images/valine评论.png)

由于Valine 是无后端评论系统，所以也就没有开发评论数据管理功能。请自行登录`Leancloud应用`管理。

具体步骤：`登录`>`选择你创建的应用`>`存储`>选择Class `Comment`，然后就可以尽情的发挥你的权利啦(～￣▽￣)～

![leancloud](/images/leancloud.png)

> 当然，你也可以配合 [@DesertsP](https://github.com/DesertsP) 开发的 [Valine-Admin](https://github.com/DesertsP/Valine-Admin) 进行`评论数据管理`

##设置浏览人数

上面已经注册了leancloud的账号，依然是在```主题配置文件```中ctrl+F

设置这两个地方

![valine浏览1](/images/valine浏览1.png)

![valine浏览2](/images/valine浏览2.png)

评论功能就开启啦

## 更新

增加实时聊天功能 源自 [大佬博客](http://xietonglei.xyz/2019/11/13/Github+Hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%EF%BC%887%EF%BC%89%E2%80%94Next%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%964/)

难得自己打了，避免大佬博客挂掉，CTRL+C一波

#### DaoVoice在线联系

**实现效果图**
[![ ](https://xtlei.oss-cn-hongkong.aliyuncs.com/xtlei/7_1.png)](https://xtlei.oss-cn-hongkong.aliyuncs.com/xtlei/7_1.png)





**具体实现方法**
首先在daovoice注册账号[**点我注册**](http://dashboard.daovoice.io/get-started),邀请码是0f81ff2f，注册完成后会得到一个 app_id:
[![ ](https://xtlei.oss-cn-hongkong.aliyuncs.com/xtlei/7_2.png)](https://xtlei.oss-cn-hongkong.aliyuncs.com/xtlei/7_2.png)





记下这个app_id的值，然后打开/themes/next/layout/_partials/head.swig,写下如下代码：

```
{% if theme.daovoice %}
  <script>
  (function(i,s,o,g,r,a,m){i["DaoVoiceObject"]=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;a.charset="utf-8";m.parentNode.insertBefore(a,m)})(window,document,"script",('https:' == document.location.protocol ? 'https:' : 'http:') + "//widget.daovoice.io/widget/0f81ff2f.js","daovoice")
  daovoice('init', {
      app_id: "{{theme.daovoice_app_id}}"
    });
  daovoice('update');
  </script>
{% endif %}
```

复制

接着打开主题配置文件，在最后写下如下代码：

```
# Online contact 
daovoice: true
daovoice_app_id: 这里填你的刚才获得的 app_id
```

复制

重新hexo g，hexo s就能看到效果了。



### 关于下载插件时npm卡住

####方案一：安装cnpm镜像

这个是比较常用的方法，我首先也是使用了这个方法。cnpm的安装方法，参考http://npm.taobao.org/

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

cmd输入以上命令就可以了，然后输入

```
cnpm install -g @angular/cli
```

后面的操作跟不使用镜像的操作是差不多的。
但是笔者在后续使用过程中遇到了一些问题，运行ng eject后发生了一些错误，所以放弃了这个方案，采用了方案二。

####方案二：使用代理registry

在网上查阅了一些资料后，决定使用代理的方式，方法也很简单，就是

```
npm config set registry https://registry.npm.taobao.org
```

然后后续的install等命令还是通过npm运作，而不是cnpm。



## 关于下一波更新

- 想搞个看板娘出来
- 有些文章想弄密码保护
- 百度和谷歌的搜索推广



## 2.8更新

看板娘出来了，但是昨天的Daovoice挂了，昨天都还可以用，不知道今天怎么就兼容不了了，只要开着Daovoice博客就一片空白。

今天增加了看板娘：

###安装模块:

hexo博客根目录选择`cmd`命令窗口或者`git bash` 输入以下代码，安装插件，我电脑上始终npm不了会卡住，一下npm建议都换成cnpm。

### 操作：

```
npm install --save hexo-helper-live2d
```

### 下载模型

作者提供了三个下载模型的办法，我选择操作比较简单的一种
`npm 模块名` 的方法

作者提供以下模型的模型包，模型包预览地址见下面的链接，选择你想用的模型，记住名字，选择对应的后缀模型包

[作者各种模型包展示](https://huaji8.top/post/live2d-plugin-2.0/)

```
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
12345678910111213141516171819202122
```

选择好对应的模型，使用 `npm install 模型的包名`来安装，比如我选择的的是`live2d-widget-model-koharu` 模型包

### 操作：

在hexo博客根目录选择`cmd`命令窗口或者`git bash` 输入以下代码

```
npm install live2d-widget-model-koharu
1
```

执行安装就完事了

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWctYmxvZy5ub3MtZWFzdGNoaW5hMS4xMjYubmV0L2tvaGFydTMucG5n)

###配置

请向`Hexo`的 `_config.yml` 文件添加配置.

### 操作：

打开个人Hexo博客文件根目录下的 `_config.yml` 文件，在最后添加一下代码
示例:

```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-koharu
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
12345678910111213141516
```

注：在移动端可能会干扰阅览，可以选择取消移动端显示，`true`改为`fasle`

```
  mobile:
    show: fasle
```

你需要配置的是`use: live2d-widget-model-koharu`
`use`后为你选择的安装包的全称

一个完美的看板娘完成啦。

### 下一波更新：

阿里图床

---

未完待更...