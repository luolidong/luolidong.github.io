---
title: pyenv安装与使用-多版本python共存解决方法
date: 2016-08-30 17:22:22
tags: python
---

centOS只带python2.6，但是现在的python一般是2.7，直接升级python会造成yum等利用python使用的命令的错误，因此使用pyenv可以在一个系统里共存2套python版本，而补影响系统自带的python使用。

**安装pyenv首先安装好python编译需要的rpm包环境：**
```
yum install readline readline-devel readline-static -y
yum install openssl openssl-devel openssl-static -y
yum install sqlite-devel -y
yum install bzip2-devel bzip2-libs -y
```


**安装pyenv**
```
git clone git://github.com/yyuu/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
exec $SHELL -l
source ~/.bashrc
```


**安装python 2.7.9 **
``pyenv install 2.7.9 -v``


**刷新数据库**
``pyenv rehash``

**切换数据库**
``pyenv global 2.7.9``




本文出自 “shine_forever的博客” 博客，请务必保留此出处
http://shineforever.blog.51cto.com/1429204/1642113