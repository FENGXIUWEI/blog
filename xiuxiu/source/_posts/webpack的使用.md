---
title: webpack的使用
date: 2018-10-08 08:47:01
tags:
- webpack
categories:
- webpack
---
#### Webpack的使用
+ 创建工作目录webpack_test/src
+ 在src文件夹下方创建app.js&lt;项目运行起来的文件，入口文件&gt;
+ 在src文件夹下方创建index.html
+ 在webpack_test文件夹下方创建webpack.config.dev.js
+ 创建package.json文件
  `npm init -y`
+ 安装开发的依赖
  `npm i -D webpack`
   问题：创建的工程文件夹和依赖包的文件夹重名
   ![webpack](/images/webpack/name_error.png)
   结解决方案：重命名文件夹或重建文件夹
+ 打包项目
   问题1：
   ![webpack](/images/webpack/miss_dev.png)
   解决方案：
   手动在package.json文件中添加dev配置
   ![webpack](/images/webpack/miss_dev_solution.png)

#### Webpack 插件
+ 自动创建html插件
  `npm i -D html-webpack-plugin`
  ![webpack](/images/webpack/html_plugin.png)
  package.json页面会自动安装相关的依赖
  ![webpack](/images/webpack/html_plugin_package.png)
  在webpack.config.dev.js页面进行手动设置
  ![webpack](/images/webpack/html_plugin_webpack.png)
+ babel-loader配置（利用babel-loader等包实现es6转es5语法）
  Loader就是webpack用来预处理模块的，在一个模块被引入之前，会预先使用loader处理模块的内容。(是在react基础上使用的)
  + 安装react
  `npm i`
  `npm i -S react react-dom`
  ![webpack](/images/webpack/react_dom.png)
  在app.js页面引入react和react-dom插件
  ![webpack](/images/webpack/react_dom_app.png)
  + 安装babel-loader
  `npm i -D babel-loader babel-core`
  ![webpack](/images/webpack/babel_package.png)
  在webpack.config.dev.js配置js文件预处理的格式
  ![webpack](/images/webpack/babel_webpack.png)
  presets字段设定转码规则，需要进行安装`npm i -D babel-preset-react`
+ Devserver开发服务器配置
  `npm i -D webpack-dev-server`
  在package.json页面会自动生成webpack-dev-server依赖，手动设置start命令。
  ![webpack](/images/webpack/devserver_package.png)
  在webpack.config.dev.js页面设置运行时直接打开页面以及相应的端口号
  ![webpack](/images/webpack/devserver_webpack.png)
+ css代码引入
  `npm i -D css-loader`
  `npm i -D style-loader`
  在package.json文件中安装相关的依赖
  ![webpack](/images/webpack/css_package.png)
  在webpack.config.dev.js文件配置相关信息
   + 先是css-loader处理（webpack把mian.css文件作为模块打包）
   + 接着是style-loade处理（让打包后的css可以写入html文件中的&lt;style&gt;）
  ![webpack](/images/webpack/css_webpack.png)
  模块化css显示
  ![webpack](/images/webpack/css_module.png)
  非模块化显示
  ![webpack](/images/webpack/css_module.png)
+ 引入图片的方法
  + 通过file-loader的方式进行引入图片
  `file-loader` 就是将文件（由于一般是图片文件为主，所以下面通常使用图片两字作为替代，方便理解。其他的包括字体文件等），在进行一些处理后（主要是处理文件名和路径），移动打包后的目录中.
  `npm i -D file-loader`
  在package.json文件中安装相应的依赖
  ![webpack](/images/webpack/file_package.png)
  在webpack.config.dev.js文件中进行配置
  ![webpack](/images/webpack/file_webpack.png)
  app.js中使用图片的方法，先引入图片，再进行引用
  ![webpack](/images/webpack/app_img.png)
  css中使用图片的方法，直接写相应的路径进行引用
  ![webpack](/images/webpack/css_img.png)
  + 通过url-loader的方式进行引入图片
  `npm i -D url-loader`
  在package.json页面进行安装url-loader依赖
  ![webpack](/images/webpack/url_package.png)
  在webpack.config.dev.js页面进行相应的配置
  ![webpack](/images/webpack/url_webpack.png)
  url-loader的优点：减少图片的请求，默认会把所有资源以base64 解析成data：image格式可以给其设置limit约束其是否编码，小于limit会进行编码，大于limit会通过style-loader进行处理
+ 引入字体小图标的方法
  `npm i -S font-awesome`
  在package.json页面进行安装font-awesome依赖
  ![webpack](/images/webpack/font_package.png)
  在webpack.config.dev.js页面进行相应的配置
  ![webpack](/images/webpack/font_webpack.png)
  在app.js页面进行使用
  ![webpack](/images/webpack/font_app.png)
+ 引入less的方法
  `npm i -D less-loader less`
+ 引入sass的方法
  `npm i -D sass-loader node-sass`
+ webpack的插件clean-webpack-plugin
  `npm i -D clean-webpack-plugin`
  在package.json页面进行安装clean-webpack-plugin插件
  ![webpack](/images/webpack/clean_package.png)
  在webpack.config.dev.js页面进行相应的配置
  ![webpack](/images/webpack/clean_webpack.png)
+ 打包后的路径publicpath
