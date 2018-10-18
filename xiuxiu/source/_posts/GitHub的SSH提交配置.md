---
title: GitHub的基本使用
date: 2018-04-18 17:09:08
bgimage: "/images/github/bg.png"
comments: true
categories:
- GitHub
tags:
- GitHub的基本使用
---
## Git可以通过https方式和ssh方式连接服务器上的仓库。
两者比较：
1.https： 比较方便，但是每次fetch和push代码都需要输入账号和密码，略显麻烦
2.ssh： 传输前压缩数据，传输效率高，不需要每次提供账号密码
## Git的user name和email设置

```javascript
$ git config --global user.name "xxxx"
$ git config --global user.email "xxxx@163.com"
```

## 生成密钥
使用你注册github的邮箱生成秘钥

```javascript
$ ssh-keygen -t rsa -C "xxxx@163.com"
```

中间连续3次Enter键

![github图片](/images/github/githubsetup.png)

.ssh目录会生成id_rsa和id_rsa.pub两个文件，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人（关于RSA加密，可以自行百度，这里不详细展开）

## 添加SSH key到github账户

在GitHub的账户添加SSH Key，GitHub才能根据此进行加密解密，从而判断此提交是由你本人操作

![github图片](/images/github/githubssh.png)

## 测试SSH key是否设置成功

```javascript
$ ssh -T git@github.com
```

```javascript
The authenticity of host 'github.com (192.30.253.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
```

是否继续连接？输入 yes

输出如下，则表示通过

```javascript
Hi xxxx! You've successfully authenticated, but GitHub does not provide shell        access.
```

## 设置项目连接方式

```javascript
$ git remote set-url git@github.com:oDevilo/Java-Base
```

这里修改的是项目中 .git （隐藏）文件夹下的config文件
原来如下：

```javascript
[remote "origin"]
    url = https://github.com/oDevilo/Java-Base
    fetch = +refs/heads/*:refs/remotes/origin/*
```

修改后：

```javascript
[remote "origin"]
    url = git@github.com:oDevilo/Java-Base
    fetch = +refs/heads/*:refs/remotes/origin/*
```

## 自动部署代码的方法

```javascript
//在项目的_config.yml文件中进行设置
deploy:
  type: git
  repo: git@github.com:FENGXIUWEI/FENGXIUWEI.github.io.git
  branch: master

//命令
hexo clean //清理缓存文件和已生成静态的文件
hexo d //部署网站
```

