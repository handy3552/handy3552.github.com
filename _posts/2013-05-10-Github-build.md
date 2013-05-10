---
layout: post
title: pages.Github使用步骤
date: 2012-05-23 17:33
---
说是git的使用心得，不如说是pages.Github的使用心得，自从第一次听说有这个好地方，就像尝试一下，想看看这到底是个什么好东西被大家那么赞不绝口（当然也有说不好的，现在我认为说这话的都是没学会用的人）。以前都是在csdn上开博，可是csdn的打开速度真的很让人d疼，不知道是我网速不好还是csdn的问题。不闲扯了，开始正事。

一.安装git

要使用Git，需要安装它的客户端，推荐在Linux下使用Git，会比较方便。Windows版的下载地址在这里[http://code.google.com/p/msysgit/downloads/list](http://code.google.com/p/msysgit/downloads/list)。其他系统的安装也可以参考官方的[安装教程](https://help.github.com/articles/set-up-git)

二.检查ssh

1.检查ssh key

	$ cd ~/.ssh

如果显示“No such file or directory”，继续下一步。

2.生成新的SSH Key

输入下面的代码，就可以生成新的key文件，我们只需要默认设置就好，所以当需要输入文件名的时候，回车就好（我一般都是输完邮件地址就一路回车下去）。

	$ ssh-keygen -t rsa -C "邮件地址@youremail.com"
	Generating public/private rsa key pair.
	Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>

然后系统会要你输入加密串（Passphrase）：

	Enter passphrase (empty for no passphrase):<输入加密串>
	Enter same passphrase again:<再次输入加密串>

3.加SSH Key到GitHub

在本机设置SSH Key之后，需要添加到GitHub上，以完成SSH链接的设置。

用文本编辑工具打开id_rsa.pub文件，如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。

在GitHub的主页上点击设置按钮：![](images/account setting.png)

然后输入公匙：![](images/add key.png)

保存就好了。
稍等片刻验证公匙是否成功（要等一会哦），下面的$ git@github.com不能更改。

	$ ssh -T git@github.com

如果显示这样：

	The authenticity of host 'github.com (207.97.227.239)' can't be established.
	RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
	Are you sure you want to continue connecting (yes/no)?

输入yes回车就好了，会出现下面代码：

	Hi <em>username</em>! You've successfully authenticated, but GitHub does not provide shell access.

4.Git会根据用户的名字和邮箱来记录提交。GitHub也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字必须是你的真名，而不是GitHub的昵称。

	$ git config --global user.name "你的名字"
	$ git config --global user.email "your_email@youremail.com"

三：创建项目

1.项目名必须是
	username.github.com

2.向master提交index.html

文件我是使用git GUI上传的，使用方法自己看，很简单。

Github Pages[官方帮助文档](https://help.github.com/categories/20/articles)，Git中文[帮助文档](http://git-scm.com/book/zh)

四：使用jeklly维护网站

把[jeklly模版](https://github.com/mojombo/jekyll/tree/master/site)下载下来，复制到自己本地资源的文件夹，用Git GUI传上去就好了

▷▷▷▷▷▷▷▷推荐[参考教程](http://beiyuu.com/github-pages/)◁◁◁◁◁◁◁◁