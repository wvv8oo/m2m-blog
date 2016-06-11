<!--
title: 如何安装M2M
-->

## 程序员

### MacOSX

如果你是一个程序员，又是使用了`MacOSX`系统，谢天谢地，这会超级简单，你只需要在终端键入：

    sudo gem install m2m

如果安装时出现类似如下的错误：

    ERROR:  While executing gem ... (Errno::EPERM)
        Operation not permitted - /usr/bin/m2m

则可以使用如下命令：

    sudo gem install m2m -n /usr/local/bin

### Windows系统

Windows是一个对使用者极其友好，对开发者极不友好的操作系统，所以，在Windows环境下安装是有点麻烦的。

#### 安装Ruby环境

**如果你的机器上已经安装，请忽略此步骤**

请使用`RubyInstaller`进行安装，下载地址：http://rubyinstaller.org/downloads/，一定要注意，你只能下载`2.2.4`版本的，因为某个依赖不支持`2.3.0`的，What the hell。

如果你的系统是64位，记得要选择64位的，直接下载链接如下：

* [RubyInstaller 2.2.4 for x86](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.2.4.exe)

* [RubyInstaller 2.2.4 for x86](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.2.4-x64.exe)

#### 在Windows下安装m2m

其实和`MacOSX`是一样的，安装完ruby，你就可以在windows环境下使用`gem`命令了，打开命令行工具，输入：

`gem install m2m`

### Linux系统

这么高端的程序员，应该不需要教程了吧，自行参考`MacOSX`

## 非程序员

请找个程序员做男朋友或者女朋友，因为我实在不知道怎么写教程了

## 其它问题

请到github上提issue吧， 传送门：https://github.com/wvv8oo/m2m/issues