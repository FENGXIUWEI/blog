---
title: ngrok的基本使用
date: 2018-05-03 14:15:33
bgimage: "/images/ngrok/bg.png"
categories:
- ngrok
tags:
- ngrok的使用
---
### 1.把项目放到tomcat启动（即点击startup.bat）tomcat
将项目放到tomcat下

![ngrok图片](/images/ngrok/1.png)

启动tomcat

![ngrok图片](/images/ngrok/2.png)

### 2.打开[https://www.ngrok.cc/](https://www.ngrok.cc/)
打开https://www.ngrok.cc/，登录系统，设置相关信息。

![ngrok图片](/images/ngrok/3.png)

### 3.通过cmd进入客户端根目录（即sunny.exe所在目录），启动sunny.exe
找到Sunny.exe所在的根目录

![ngrok图片](/images/ngrok/4.png)

通过cmd进行启动，sunny.exe clientid id（https://www.ngrok.cc/ 网站上面的id）

![ngrok图片](/images/ngrok/5.png)

### 4.外网访问（即：第三步，窗口看到的ip就是外网ip）
红色线部分是指IP，[http://xiuxiu.free.ngrok.cc/dist/index.html](http://xiuxiu.free.ngrok.cc/dist/index.html) ，dist是指项目名称，index.html页面。

![ngrok图片](/images/ngrok/6.png)






