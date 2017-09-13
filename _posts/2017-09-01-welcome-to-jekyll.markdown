---
layout: post
title:  "第一篇文章 - 我是如何搭建个人博客的"
date:   2017-09-01 21:48:39 +0800
categories: jekyll update
---
大家好，我是张二狗，这里是我的个人博客。表示想开博客很久了，既是因为写博客可以提高自身的姿势水平，也因为继承了程序猿的分享精神。希望我的文章能对大家有所帮助。

第一篇文章，讲讲这个博客是怎么搭建的吧。用一句话概括就是是：在`mac`上使用`jekyll`构建网页系统，并显示在`github page`上.

## Step1 在mac上使用Jekyll搭建网页系统

[Jekyll](http://jekyllrb.com/)是一个将纯文本转换成静态站点或blog的工具，我们利用markdown语法写完文章后，它会自动生成静态网页，非常地强大。同时呢，github pages对Jekyll提供原生支持，可以免费将你的blog托管到github pages

### 1.1 安装Jekyll
Jekyll是用Ruby开发的，因此在使用Jekyll之前，要检查一下你的Ruby和RubyGem是否已经安装好（以下是我的环境）。通常来讲，macOS自带Ruby。

	ruby -v // ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
	gem -v // 2.6.11

看起来没问题，然后就可安装Jekyll了

	gem install jekyll bundler
	
我在这里遇到个坑，执行上面这条命令时会报错

	ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
    
原因即字面意思, 就是 gem 要往某个神奇的目录写文件但是你的权限不够. 因为你使用的是 Apple 家自带的 ruby, 在尝试往 Apple 自家的库中塞东西, 默认是不允许的

这就尴尬了，自带的Ruby不能用，坑爹呢。这个时候我们就要自己另外装一个ruby了，方法很简单，使用[homebrew](https://brew.sh/)即可轻松安装

	brew install ruby
	
默认情况下, brew 的各种 gems 会装到 /usr/local/lib/ruby/gems/2.3.0 这个位置. 2.3.0 是版本号, 也许在其它位置. 而不是原来的 /Library/Ruby/Gems/2.0.0 这个位置.

然后呢再次安装jekyll

	gem install jekyll bundler
	
结果可能会报同样的错误，这时候不要慌，这是因为系统默认使用的gem还是macOS自带的那个gem，你需要切换到自己安装的这个gem上来。首先要打开  `~/.bash_profile`，没有的话就新建一个，然后在里面添加一行

	export PATH=/usr/local/bin:$PATH
	
保存后，在命令行执行

	source ~/.bash_profile
	
这样，就能保证优先使用你自己的gem了（记得先重启一下命令行）

OK，这样安装jekyll就没有什么问题了（至少我还没发现别的问题）

### 1.2 使用Jekyll构建网页

成功安装好jekyll后，就可以自动初始化你的网页系统了

	jekyll new myblog // myblog是你网页系统的名字
	cd myblog // 进入文件夹
	jekyll serve // 启动本地服务器
	
打开你的浏览器，输入 [http://localhost:4000](http://localhost:4000)，就能看到你的网页了，就像下面这样：

![init website](http://upload-images.jianshu.io/upload_images/1464256-66ad5ad05132fc0f.png?imageMogr2/auto-orient/strip%7CimageView2/2)
	
很好，这个时候你就可以编辑自己的网页内容了，这里你需要了解`jekyll文件系统的构成`和`markdown语法的使用`，以后有时间我会写出来，此处不做讨论。

## Step2 发布到github pages

这个就比较简单了，首先你需要在github上新建一个repo，把我们本地的内容上传到该项目即可。以我为例，在github上新建一个repo后，打开命令行，进入你网站项目的目录
	
	git init	// 初始化git
	git add . // 把目录中的文件放到git工作区
	git commit -m "first commit"	// 提交
	git remote add origin https://github.com/johnbryant/test.git // 关联github远程仓库，后面是你具体的地址
	git push -u origin master // 发布到github远程仓库
	
上传完成后，在github该项目的setting里，把github pages设置的status改为public即可
