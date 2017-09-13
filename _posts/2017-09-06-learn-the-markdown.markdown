---
layout: post
title:  "markdown学习笔记（基础篇）"
date:   2017-09-06 18:15:39 +0800
category: markdown
---
![macdown-logo]({{ site.url }}/assets/image/macdown-logo.png)

## Macdown简介
Macdown是MacOS上一款很好用的开源markdown编辑器，它除了支持所有markdown语法，还有更强大的功能

## Markdown基础

### 换行
正常情况下，当你需要强制换行时，只有一个回车是不起作用的，  
需要先在行末输2个空格，然后再回车

	这样是可以（2个空格）
	换行的

### 加粗和斜体
**加粗**: `**加粗**` 或 `__加粗__`  
*斜体*: `*斜体*` 或 `_斜体_`

### 标题
按大小分为1到6号

	# 1号标题
	## 2号标题
	### 3号标题
	#### 4号标题
	##### 5号标题
	###### 6号标题
	
另一种方式

	1号标题
	======
	
	2号标题
	------

### 链接和邮箱地址
#### 行内链接
用尖括号括住邮箱地址就能让它变得可点击：<johnbryant262@gmail.com>  
`<johnbryant262@gmail.com>`  

链接同理：<https://johnbryant.github.io/myblog>  
`<https://johnbryant.github.io/myblog>`

有时候你觉得直接放链接太丑了，可以替换成链接名：[我的链接](https://johnbryant.github.io/myblog)
`[我的链接](https://johnbryant.github.io/myblog)`

#### 链接变量
从程序员的角度看，如果一篇文章有很多链接，用上面那样的方式，就会显得不够整洁，你或许可以把所有的链接放到一个地方进行管理  
首先创建一个链接，[我的链接1][link1]`[我的链接1][link1]`, 然后在文章的任何一个地方定义你的链接变量：`[link1]:https://johnbryant.github.io/myblog`


如果链接名足够简洁的话，可以直接用作链接变量，比如[like this][]`[like this][]`，然后在文章的任何一个地方定义变量：`[like this]:https://johnbryant.github.io/myblog`

[link1]:https://johnbryant.github.io/myblog
[like this]:https://johnbryant.github.io/myblog

### 图片
#### 行内链接
网络图片:`![whatever name](http://picture.cn)`  
本地图片: `![whatever name](../image/image1.png)`

#### 链接变量
`![whatever name][image-id]`  
然后在文章的任何一个地方定义链接变量：`[image-id]:(../image/image.png)`

### 列表
* 在列表之前一定要空一行
* 无序列表项以`*`开头
- 无序列表项也可以`-`开头
	* 通过缩进实现子列表
		* 可以多次缩进
	* 有序列表
		1. 有序列表的格式是数字+点+空格，像 `1. `
		42. 前面的序号，不管你用什么数字，都会自动按顺序排好

以下是上面的代码:

```
* 在列表之前一定要空一行
* 无序列表项以`*`开头
- 无序列表项也可以`-`开头
	* 通过缩进实现子列表
		* 可以多次缩进
	* 有序列表
		1. 有序列表的格式是数字+点+空格，像 `1. `
		42. 前面的序号，不管你用什么数字，都会自动按顺序排好

``` 

### 引用块
> 用`>`开头可以表示引用块  
> > 通过多个`>`可以实现子引用
> > > 展示多个层级  
除了第一行，每行的格式继承自上一行，因此不一定要以`>`开头

> > 如果不想继承上一行的格式，需要空一行

> 大部分的markdown语法在引用块内是可用的
> 
> * 比如列表
> * 这样子

### 行内代码块
`inline code`如果想像这样在行内把内容包起来，可以这么写  
`` `inline code` ``，即用两个`` ` ``把内容包起来  
如果要包裹的内容含有i个`` ` ``，那么就用i+1个`` ` ``包裹，比如``` `` ` `` ```

### 代码块
要实现这样的代码块

	var i = 0;
	i++
	
需要上下各空一行，并且每行以tab或4个空格开头

### 分割线
输入`***`或`___`就能实现以下的分割线
***

以上就是macdown学习的基础知识，之后我会学习Macdown更酷炫的一些语法