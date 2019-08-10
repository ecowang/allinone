---
title: 如何使用jekyll建设一个网站
author: 老王
date: '2016-08-27'
slug: jekyll-website
categories:
  - Website
tags:
  - website
---

# 一、可能感兴趣的人

+ 没有多少专业知识，对电脑的了解仅限于正常办公、下载电影、知道几个dos命令。
+ 有记录、整理、提升自己的需求。
+ 认同接下来的时代是信息时代，不在网上的东西趋近于不存在。
+ 感受到一些大型博客网站的不自由，不顺手。
+ 想做自己的博客，又不想在搭建上费太多劲。

如果是这样，你和我有一样的需求，接下来这些记录估计会有用。

**本文还没写完，随时更新。**
**哦，没更新了，改用blogdown维护……囧**

# 二、几个概念

概念是厘清过程的基石，这些概念都是需要了解的，知道了这些，才知道自己每一步是在做什么。以下概念不一定很准，但相当通俗，因为我就是这么理解的，有错误的话欢迎提出来随时修改。

## 1、github

[github](https://github.com/)是一个托管开源程序的网站，各种语言都可以。各种程序以repository的形式放在其服务器上，简称repo。下面说的ruby、jekyll和各种theme都可以放在上面。github通过[git](git-scm.com)系统来进行版本控制。 **github是个网站也是个远程硬盘，可以把代码图片等等放上去，大家合作做一些东西，方式就是git**。

想要熟悉github，首先要注册一个用户，然后`fork几个repo`，就在网页上多点点改改，看看有什么反应，泡的时间够了，对那些概念就会有一个初步的认识，起码就知道上面这句话是啥意思了。

## 2、git

[git](git-scm.com)是一个版本控制系统。表现形式是一个命令行界面，在windows下需要下载一个新的命令行界面不能用系统自带的cmd，而是用安装后的[gitbash](https://git-scm.com/downloads)。这个看着和cmd差不多都是黑乎乎的，但前面有个$符号，原因是不同的shell。shell是相对core的，是系统外层的壳，如果core是中央政府，shell就相当于职能部门，完成特定工作。部门是分锅吃饭的，shell也有不同种类，要用git的话，必须用gitbash，是bash的shell，linux一脉相承下来的。 其实用git最好再linux上用，苹果也行（好像苹果也是基于linux还是unix开发的？），在windows上需要设置的东西相对更多。

git 六脉神剑(目前就用过这几个囧)

| 命令                           | 使用及作用                                    |
| ---------------------------- | ---------------------------------------- |
| git init                     | 初始化一个repo，代表git对这个文件夹的变化开始全面掌控了，会有一个隐藏文件夹作为总控室。 |
| git add .                    | 这个文件夹里所有的变化，都报告给git总控室。                  |
| git commit -m "some changes" | 总控室把所有的变化都批准了进行提交，建立一个时间节点，并对这些变化有个标注。   |
| git checkout gh-pages        | 新建一个分支，这里用`gh-pages`做例子，因为要做博客，必须建一个这样的分支，这样gitpage这个网站才能从github的repo里生成网页。 |
| git push                     | 我们在电脑上的变化，比如我用记事本写了一个博客，要放到github上去，不需要像邮件一样上传，在gitbash或者别的命令行界面中推送就行了。 |
| git pull                     | 上一个动作的反向动作。如果我在网站上有变化，或者从其他电脑推送变化了，在另一台电脑上，可以把这些变化更新到本地，把变化拉过来。 |


## 3、ruby

[ruby](www.ruby-lang.org)其实是一种语言。语言也是需要安装的。在window里要[下载](http://www.ruby-lang.org/en/downloads/)，安装后会有一个新的命令界面，叫start command promot with ruby，这大概是把ruby和window自带的命令提示符结合了，没有$符号。装ruby的目的，是安装和应用jekyll。

linux里方便的多，一条命令就够了。
> $ sudo apt-get install ruby-full


## 4、jekyll

[jekyll](http://jekyll.com.cn/)，是一个免费的博客生成工具。首先，需要在上面说的那个结合ruby语言的命令提示符下安装。装好后，按照官方说明，只要几秒钟就可以跑起来，确实没骗人，但没说前面配置需要多长时间。我的经历，耗时月余，开始在window下弄，接连不断的错误，后来受不了装了个Ubuntu，用linux系统装，也是好多需要踩的雷。但开源软件的好处是只要有时间有耐心，遇到的问题都是有解决方法的。现在在windows和ubuntu上都可以简单操作了。

jekyll的使用步骤是这样的：
> $ gem install jekyll
> ~ $ jekyll new my-awesome-site
> ~ $ cd my-awesome-site
> ~/my-awesome-site $ jekyll serve

他会自动生成一个博客网站的结构，统一套用格式，可以用Markdown语法书写。按照其规则，可以进行博客网站结构的定制，一般人肯定没能力也没必要从头定制，可以用别人做好的，这就是模板theme。jekyll自己生成网站和模板的关系是这样的：
> 如果你用别人的模板，就不需要自己生成了，直接在模板文件夹里运行`jekyll serve`就可以了。


## 5、theme

就是高人们做好的模板，拿过来就可以套用的自己的博客上。一般这些模板都以repo的形式放在github上，想用的话可以直接拿来用。可以先fork（大概就是复制的意思）到自己的账户上，然后修改自己的关键信息。比如我这个博客就是用的[LessOrMore](https://github.com/luoyan35714/LessOrMore.git)的模板。

模板也是按照jekyll规则做好的，不过加入了一些css之类的语法，能实现更多功能，也更美观。像我一样的外行的话，用别人的模板，拿来主义就行了，不需要自己设计。

## 6、Markdown

一种书写语法，可以在记事本上写出带格式的脚本，语法很简单，可以参考[这篇](http://sspai.com/25137)。看到本篇的格式了没，都是markdown的功劳，加一些符号就可以了。


## 7、网址

自己需要申请，可以绑定github上自动生成的网址。目前国内可以在万网、新网、西部数码等申请。我在西部数码上申请的.wang的网址。花钱的事儿不会太难，不多说了。

# 三、目标

从刚才的概念出发，我们的目标就是：安装好git、ruby和jekyll，注册好github账号，fork一个合适的theme，git clone到本地，修改必要信息把原来的网站信息改成自己的，然后push回到github， 配置一下网址，基本就行了。

关于概念的进一步理清，可以参考[这篇文章](http://www.worldhello.net/gotgithub/03-project-hosting/050-homepage.html)。如果早仔细看几遍，就不会费这么大劲儿了。

# 四、使用LessOrMore模板

以下基本为为LessOrMore官方安装方案。

## 1、下载

使用git从[LessOrMore](https://github.com/luoyan35714/LessOrMore.git)主页下载项目

{% highlight bash %}
git clone https://github.com/luoyan35714/LessOrMore.git
{% endhighlight %}

## 2、配置

`LessOrMore`项目需要配置的只有一个文件`_config.yml`，打开之后按照如下进行配置。

> 特别注意`baseurl`的配置。如果是`***.github.io`项目，不修改为空''的话，会导致JS,CSS等静态资源无法找到的错误

{% highlight bash %}
name: 博客名称
email: 邮箱地址
author: 作者名
url: 个人网站
baseurl: "/LessOrMore"  baseurl修改为项目名，如果项目是'***.github.io'，则设置为空''
resume_site: 个人简历网站
github: github地址
github_username: github用户名称
FB:
  comments :
    provider : duoshuo
    duoshuo:
        short_name : 多说账户
    disqus :
        short_name : Disqus账户
{% endhighlight %}

旁白：需要配置的还有一些图片、读书、友情链接之类的，自行修改替换。


## 3、如何写文章

在`LessOrMore/_posts`目录下新建一个文件，可以创建文件夹并在文件夹中添加文件，方便维护。在新建文件中粘贴如下信息，并修改以下的`titile`,`date`,`categories`,`tag`的相关信息，添加`* content {:toc}`为目录相关信息，在进行正文书写前需要在目录和正文之间输入至少2行空行。然后按照正常的Markdown语法书写正文。

## 4、执行

使用`jekyll server`命令。


## 5、效果

打开浏览器并输入URL`http://localhost:4000/`,回车。

这样就可以在本地浏览了，一些修改可以立马看到效果，基本上在本地能正常运行，推送到github上也可以，如果不能，那是因为一些概念没弄明白，比如修改的分支不对。

## 6、推送到github

上面一般的执行是在master分支下，直接推送的话没反应。必须check out gh-pages，在这个分支下操作，或者把master分支的merge过来`git merge master`，然后再push到github上，就会发现github直接给你jekyll好了，可以浏览了。

想用自己的域名，在CNAME里改称自己的网址。

# 五、一点感受

有很多可能出现的问题。

如果用windows，将会发现实现一个简单的jekyll new都是如此困难，不过熬过来以后，会发现想到达到写个博客的目标没那么难，常用的命令也就那么几个。

如果用linux，将会发现更多的问题，因为那是和windows完全不同的一个世界，安装、输入法、装软件都需要学习，但好在开源的程序，几乎所有问题都能google到解决办法。弄好以后发现在linux上做关于网络的东西确实有方便的地方，也能想象到，如果对各种命令再熟悉一点，会感觉更方便。

# 追加的番外

过了大概一个多月，发现很多工作在ubuntu上没法干，因为大部分工作还是打开word写材料。。。而有些大点的word，在ubuntu上根本打不开，笔记本利用效率极低。没办法，装回windows。

这次安装jekyll比较顺利，基本按照[官方文件](https://jekyllrb.com/docs/windows/)，一步步来就完成了，简述如下：

- 安装一个叫做[Chocolatey](https://chocolatey.org/install)的东西，是用来管理需要安装的语言包的。 很简单，在命令提示符上右击，管理员运行，然后把后面这一串考进去运行。`@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`
- 然后关了命令提示符，再重新打开一次，安装Ruby，装了Ruby才能装Jekyll。 运行这一段：`choco install ruby -y`
- 完了继续，关了重开，也可以直接打开新的命令提示符，**start promote with ruby**。开始安装jekyll。官方说直接运行`gem install jekyll`。但在国内是不行的，需要看下一条。
- 到[这里](http://guides.rubygems.org/ssl-certificate-update/#installing-using-update-packages)，先下载[rubygems-update-2.6.7.gem](https://rubygems.org/downloads/rubygems-update-2.6.7.gem)，然后把它放到命令提示符所在的文件夹。比如我就是C:\Users\wq
- > C:\>gem install --local C:\Users\wq\rubygems-update-2.6.7.gem
C:\>update_rubygems --no-ri --no-rdoc

- 现在，可以放心的`gem install jekyll`了。