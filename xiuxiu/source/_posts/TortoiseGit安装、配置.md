---
title: TortoiseGit安装、配置
date: 2018-09-25 15:48:07
categories:
- TortoiseGit,git
tags:
- TortoiseGit,git
---
### 1.TortoiseGit简介
tortoiseGit是一个开放的git版本控制系统的源客户端，支持Winxp/vista/win7.该软件功能和git一样
### 2.TortoiseGit下载
tortoiseGit下载地址：https://download.tortoisegit.org/tgit/
![TortoiseGit图片](/images/TortoiseGit/1.png)
安装包下载
![TortoiseGit图片](/images/TortoiseGit/2.png)
### 3.TortoiseGit安装
安装顺序：先安装程序包,然后安装语言包(LanguagePack).
安装说明：因为TortoiseGit 只是一个程序壳,必须依赖一个 Git Core,所以安装前请确定已完成git安装和配置
  可参考：Git安装：https://www.cnblogs.com/xiuxingzhe/p/9300905.html
          Git生成秘钥及GitLab配置： http://www.cnblogs.com/xiuxingzhe/p/9303278.html
#### 3.1 安装程序包
+ 双击TortoiseGit-2.6.0.0-64bit.msi，弹出安装导向页面
![TortoiseGit图片](/images/TortoiseGit/3.png)
+ 一路Next> 即可，配置均选择默认
![TortoiseGit图片](/images/TortoiseGit/4.png)
+ 点击Install
![TortoiseGit图片](/images/TortoiseGit/5.png)
+ 点击Finish，如果以前有老版本,则选择覆盖,关闭旧程序并尝试重启即可
![TortoiseGit图片](/images/TortoiseGit/6.png)

#### 3.2 安装语言包
如果想使用英文版本的该工具，不想使用中文版本的，则该模块操作可忽略
+ 双击TortoiseGit-LanguagePack-2.6.0.0-64bit-zh_CN.msi，弹出安装导向
![TortoiseGit图片](/images/TortoiseGit/7.png)
+ 点击下一步，安装完成后，点击完成
![TortoiseGit图片](/images/TortoiseGit/8.png)

#### 3.3 配置TortoiseGit的环境
+ 在环境变量中添加TortoiseGit的路径
![TortoiseGit图片](/images/TortoiseGit/17.png)

### 4 TortoiseGit配置
#### 4.1 常规配置
+ 先选择一个本地的目录，作为git项目存放的目录，方便管理。本文选择：
  E:\project\clear-project，建议：路径中不要包含中文
![TortoiseGit图片](/images/TortoiseGit/9.png)
+ 在空白处点击鼠标右键, 选择 --> TortoiseGit --> Settings, 弹出配置界面(当TortoiseGit安装完成后，鼠标右键点击后，默认出现 TortoiseGit 相关选项)
![TortoiseGit图片](/images/TortoiseGit/10.png)
+ 点击General，在页面中选择Language下拉框，选择“中文(简体)中华人名共和国”，然后点击应用，确定关闭对话框(当然也可以继续使用英文)
![TortoiseGit图片](/images/TortoiseGit/11.png)

#### 4.2 Git生成秘钥
+ 在.ssh 目录下右键打开Git Bash(.ssh目录不存在，手动创建)
![TortoiseGit图片](/images/TortoiseGit/14.png)
+ 生成秘钥：ssh-keygen -t rsa -C "your_email@youremail.com" ，直接Enter就行，然后会提示输入密码(可输可不输)
![TortoiseGit图片](/images/TortoiseGit/15.png)
+ 执行完成之后，在.ssh 目录下就会生成秘钥文件
![TortoiseGit图片](/images/TortoiseGit/16.png)

#### 4.3 Github 配置密钥
将.ssh文件夹中id_rsa中的密钥拷贝到github中SSH keys / Add new 的key中
![TortoiseGit图片](/images/TortoiseGit/19.png)
### 5 TortoiseGit使用示例
+ 在本地目标下载目录下，右键-->TortoiseGit(T)-->克隆，粘贴SSH 链接地址到URL，点击确定
![TortoiseGit图片](/images/TortoiseGit/12.png)
+ 确认项目已从gitlab上克隆到本地
![TortoiseGit图片](/images/TortoiseGit/13.png)