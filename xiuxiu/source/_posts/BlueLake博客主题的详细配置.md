---
title: BlueLake博客主题的详细配置
date: 2018-05-08 16:21:50
tags:
---
### [](#开始之前 "开始之前")开始之前

[BlueLake主题](https://github.com/chaooo/hexo-theme-BlueLake)写了有一段时间了，经常会有朋友发消息给我问一些配置的问题，这篇博文主要也是为了解决这些问题。主题以简洁轻量自居(实则简陋)，去掉了Jquery和Fancybox,用原生JS实现站内搜索功能和回到顶部效果。这个主题只是一个小小的雏形，期待您来帮助它成长。

在阅读本文之前，假定您已经成功安装了[Hexo](https://hexo.io/zh-cn/)，并使用 Hexo 提供的命令创建了一个静态博客。Hexo是一个快速、简洁且高效的博客框架。Hexo基于Node.js ，使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

> 需要特别注意的是Hexo有两个`_config.yml`配置文件，一份位于站点根目录下，主要包含 Hexo 站点本身的配置，下文中会称为**`根_config.yml`**；另一份位于主题目录下（themes/主题名/_config.yml），这份配置由主题作者提供，主要用于配置主题相关的选项,下文中会称为**`主题_config.yml`**。

### [](#1-安装 "1. 安装")1. 安装

您可以直接到[BlueLake发布页](https://github.com/chaooo/hexo-theme-BlueLake)下载，然后解压拷贝到`themes`目录下，修改配置即可。
不过我还是推荐使用`GIT`来checkout代码，之后也可以通过`git pull`来快速更新。

#### [](#1-1-安装主题 "1.1 安装主题")1.1 安装主题

在根目录下打开终端窗口：

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line">$ git <span class="built_in">clone</span> https://github.com/chaooo/hexo-theme-BlueLake.git themes/BlueLake</div></pre></td></tr></tbody></table></figure>

#### [](#1-2-安装主题渲染器 "1.2 安装主题渲染器")1.2 安装主题渲染器

BlueLake是基于`jade`和`stylus`写的，所以需要安装`hexo-renderer-jade`和`hexo-renderer-stylus`来渲染。

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div></pre></td><td class="code"><pre><div class="line">$ npm install hexo-renderer-jade@0.3.0 --save</div><div class="line">$ npm install hexo-renderer-stylus --save</div></pre></td></tr></tbody></table></figure>

#### [](#1-3-启用主题 "1.3 启用主题")1.3 启用主题

打开`根_config.yml`配置文件，找到theme字段，将其值改为`BlueLake`(先确认主题文件夹名称是否为BlueLake)。

<figure class="highlight yml"><figcaption><span>根_config.yml</span>[_config.yml](https://hexo.io/zh-cn/docs/configuration.html)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line"><span class="attr">theme:</span> BlueLake</div></pre></td></tr></tbody></table></figure>

#### [](#1-4-验证 "1.4 验证")1.4 验证

首先启动 Hexo 本地站点，并开启调试模式：

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line">$ hexo s --debug</div></pre></td></tr></tbody></table></figure>

在服务启动的过程，注意观察命令行输出是否有任何异常信息，如果你碰到问题，这些信息将帮助他人更好的定位错误。 当命令行输出中提示出：`INFO  Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.`
此时即可使用浏览器访问 `http://localhost:4000`，检查站点是否正确运行。

#### [](#1-5-更新主题 "1.5 更新主题")1.5 更新主题

今后若主题添加了新功能正是您需要的，您可以直接`git pull`来更新主题。

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div></pre></td><td class="code"><pre><div class="line"><span class="built_in">cd</span> themes/BlueLake</div><div class="line">git pull</div></pre></td></tr></tbody></table></figure>

### [](#2-配置 "2. 配置")2. 配置

#### [](#2-1-配置网站头部显示文字 "2.1 配置网站头部显示文字")2.1 配置网站头部显示文字

打开`根_config.yml`，找到：

<figure class="highlight yml"><figcaption><span>根_config.yml</span>[_config.yml](https://hexo.io/zh-cn/docs/configuration.html)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div></pre></td><td class="code"><pre><div class="line"><span class="attr">title:</span> </div><div class="line"><span class="attr">subtitle:</span> </div><div class="line"><span class="attr">description:</span> </div><div class="line"><span class="attr">author:</span></div></pre></td></tr></tbody></table></figure>

`title`和`subtitle`分别是网站主标题和副标题，会显示在网站头部；`description`在网站界面不会显示，内容会加入网站源码的`meta`标签中，主要用于SEO；`author`就填写网站所有者的名字，会在网站底部的`Copyright`处有所显示。

#### [](#2-2-设置语言 "2.2 设置语言")2.2 设置语言

该主题目前有七种语言：简体中文（zh-CN），繁体中文（zh-TW），英语（en），法语（fr-FR），德语（de-DE），韩语 （ko）,西班牙语（es-ES）；例如选用简体中文，在`根_config.yml`配置如下：

<figure class="highlight yml"><figcaption><span>根_config.yml</span>[_config.yml](https://hexo.io/zh-cn/docs/configuration.html)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line"><span class="attr">language:</span> zh-CN</div></pre></td></tr></tbody></table></figure>

#### [](#2-3-设置菜单 "2.3 设置菜单")2.3 设置菜单

打开`主题_config.yml`，找到：

<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div><div class="line">8</div><div class="line">9</div><div class="line">10</div><div class="line">11</div><div class="line">12</div><div class="line">13</div></pre></td><td class="code"><pre><div class="line"><span class="attr">menu:</span></div><div class="line"><span class="attr">  - page:</span> home</div><div class="line"><span class="attr">    directory:</span> .</div><div class="line"><span class="attr">    icon:</span> fa-home</div><div class="line"><span class="attr">  - page:</span> archive</div><div class="line"><span class="attr">    directory:</span> archives/</div><div class="line"><span class="attr">    icon:</span> fa-archive</div><div class="line">  <span class="comment"># - page: about</span></div><div class="line">  <span class="comment">#   directory: about/</span></div><div class="line">  <span class="comment">#   icon: fa-user</span></div><div class="line"><span class="attr">  - page:</span> rss</div><div class="line"><span class="attr">    directory:</span> atom.xml</div><div class="line"><span class="attr">    icon:</span> fa-rss</div></pre></td></tr></tbody></table></figure>

主题默认是展示四个菜单，即`主页home`，`归档archive`，`关于about`，`订阅RSS`；about需要手动添加，RSS需要安装插件，若您并不需要，可以直接注释掉。
每个页面底部的`footer`中`联系博主`的三个图标分别是`邮箱`，`微博主页链接地址`，`GitHUb个人页链接地址`，直接使用`主题_config.yml`中`about页面`的配置，若不需要about页面，只需要如下配置就好：

<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div></pre></td><td class="code"><pre><div class="line"><span class="comment"># About page </span></div><div class="line"><span class="attr">about:</span></div><div class="line"><span class="attr">  email:</span> <span class="comment">## 个人邮箱 </span></div><div class="line"><span class="attr">  weibo_url:</span> <span class="comment">## 微博主页链接地址</span></div><div class="line"><span class="attr">  github_url:</span> <span class="comment">## github主页链接地址</span></div></pre></td></tr></tbody></table></figure>

##### [](#2-3-1-添加about页 "2.3.1 添加about页")2.3.1 添加about页

此主题默认page页面是关于我页面的布局，在根目录下打开命令行窗口，生成一个关于我页面：

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line">$ hexo new page <span class="string">'about'</span></div></pre></td></tr></tbody></table></figure>

打开`主题_config.yml`，补全关于我页面的详细信息：

<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div><div class="line">8</div></pre></td><td class="code"><pre><div class="line"><span class="comment"># About page </span></div><div class="line"><span class="attr">about:</span></div><div class="line"><span class="attr">  photo_url:</span> <span class="comment">## 头像的链接地址</span></div><div class="line"><span class="attr">  email:</span> <span class="comment">## 个人邮箱 </span></div><div class="line"><span class="attr">  weibo_url:</span> <span class="comment">## 微博主页链接地址</span></div><div class="line"><span class="attr">  weibo_name:</span> <span class="comment">## 微博用户名 </span></div><div class="line"><span class="attr">  github_url:</span> <span class="comment">## github主页链接地址</span></div><div class="line"><span class="attr">  github_name:</span> <span class="comment">## github用户名</span></div></pre></td></tr></tbody></table></figure>

当然您也可以自定义重新布局about页面，只需要修改`layout/page.jade`模板就好。

##### [](#2-3-2-安装-RSS-订阅-和-sitemap-网站地图-插件 "2.3.2 安装 RSS(订阅) 和 sitemap(网站地图) 插件")2.3.2 安装 RSS(订阅) 和 sitemap(网站地图) 插件

在根目录下打开命令行窗口：

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div></pre></td><td class="code"><pre><div class="line">$ npm install hexo-generator-feed --save</div><div class="line">$ npm install hexo-generator-sitemap --save</div><div class="line">$ npm install hexo-generator-baidu-sitemap --save</div></pre></td></tr></tbody></table></figure>

添加`主题_config.yml`配置：

<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div><div class="line">8</div><div class="line">9</div><div class="line">10</div><div class="line">11</div><div class="line">12</div><div class="line">13</div><div class="line">14</div></pre></td><td class="code"><pre><div class="line"><span class="attr">Plugins:</span></div><div class="line">  hexo-generator-feed</div><div class="line">  hexo-generator-sitemap</div><div class="line">  hexo-generator-baidu-sitemap</div><div class="line"></div><div class="line"><span class="attr">feed:</span></div><div class="line"><span class="attr">  type:</span> atom</div><div class="line"><span class="attr">  path:</span> atom.xml</div><div class="line"><span class="attr">  limit:</span> <span class="number">20</span></div><div class="line"></div><div class="line"><span class="attr">sitemap:</span></div><div class="line"><span class="attr">  path:</span> sitemap.xml</div><div class="line"><span class="attr">baidusitemap:</span></div><div class="line"><span class="attr">  path:</span> baidusitemap.xml</div></pre></td></tr></tbody></table></figure>

#### [](#2-4-添加本地搜索 "2.4 添加本地搜索")2.4 添加本地搜索

默认本地搜索是用原生JS写的，但还需要HEXO插件创建的JSON数据文件配合。安装插件[hexo-generator-json-content](https://github.com/alexbruno/hexo-generator-json-content)来创建JSON数据文件：

<figure class="highlight bash"><figcaption><span>git bash</span></figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line">$ npm install hexo-generator-json-content@2.2.0 --save</div></pre></td></tr></tbody></table></figure>

然后在`根_config.yml`添加配置：

<figure class="highlight yml"><figcaption><span>根_config.yml</span>[_config.yml](https://hexo.io/zh-cn/docs/configuration.html)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div><div class="line">8</div><div class="line">9</div><div class="line">10</div><div class="line">11</div><div class="line">12</div><div class="line">13</div><div class="line">14</div><div class="line">15</div><div class="line">16</div><div class="line">17</div><div class="line">18</div></pre></td><td class="code"><pre><div class="line"><span class="attr">jsonContent:</span></div><div class="line"><span class="attr">  meta:</span> <span class="literal">false</span></div><div class="line"><span class="attr">  pages:</span> <span class="literal">false</span></div><div class="line"><span class="attr">  posts:</span></div><div class="line"><span class="attr">    title:</span> <span class="literal">true</span></div><div class="line"><span class="attr">    date:</span> <span class="literal">true</span></div><div class="line"><span class="attr">    path:</span> <span class="literal">true</span></div><div class="line"><span class="attr">    text:</span> <span class="literal">true</span></div><div class="line"><span class="attr">    raw:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    content:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    slug:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    updated:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    comments:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    link:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    permalink:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    excerpt:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    categories:</span> <span class="literal">false</span></div><div class="line"><span class="attr">    tags:</span> <span class="literal">true</span></div></pre></td></tr></tbody></table></figure>

最后在`主题_config.yml`添加配置：

<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line"><span class="attr">local_search:</span> <span class="literal">true</span></div></pre></td></tr></tbody></table></figure>

#### [](#2-5-修改站点图标 "2.5 修改站点图标")2.5 修改站点图标

站点图标存放在主题的`Source`目录下，已经默认为您准备了两张图片。您也可以自己设计站点LOGO。
您需要准备一张ico格式并命名为** favicon.ico **，请将其放入hexo目录的`source`文件夹，建议大小：32px X 32px。
您需要为苹果设备添加网站徽标，请命名为** apple-touch-icon.png **的图像放入hexo目录的“source”文件夹中，建议大小为：114px X 114px。
(有很多网站都可以在线生成ico格式的图片。)

#### [](#2-6-添加站点关键字 "2.6 添加站点关键字")2.6 添加站点关键字

请在hexo目录的`根_config.yml`中添加keywords字段，如：

<figure class="highlight yml"><figcaption><span>根_config.yml</span>[_config.yml](https://hexo.io/zh-cn/docs/configuration.html)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div></pre></td><td class="code"><pre><div class="line"><span class="comment"># Site</span></div><div class="line"><span class="attr">title:</span> Hexo</div><div class="line"><span class="attr">subtitle:</span> 副标题</div><div class="line"><span class="attr">description:</span> 网站简要描述,如：Charles·Zheng<span class="string">'s blog.</span></div><div class="line">keywords: 网站关键字, key, key1, key2, key3</div><div class="line">author: Charles</div><div class="line">language: zh-CN</div></pre></td></tr></tbody></table></figure>

#### [](#2-7-其他配置 "2.7 其他配置")2.7 其他配置

`主题_config.yml`的其他配置

1.  `show_category_count`——是否显示分类下的文章数。
2.  `widgets_on_small_screens`——是否在小屏显示侧边栏，若`true`,则侧边栏挂件将显示在底部。<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml ](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div></pre></td><td class="code"><pre><div class="line"><span class="attr">show_category_count:</span> <span class="literal">true</span> </div><div class="line"><span class="attr">widgets_on_small_screens:</span> <span class="literal">true</span></div></pre></td></tr></tbody></table></figure>

### [](#3-集成第三方服务 "3.集成第三方服务")3.集成第三方服务

#### [](#3-1-添加评论 "3.1 添加评论")3.1 添加评论

目前主题集成六种第三方评论，分别是[多说评论](http://duoshuo.com)、[Disqus评论](https://disqus.com)、[来必力评论](https://livere.com)、[友言评论](http://www.uyan.cc/)、[网易云跟帖评论](https://gentie.163.com/info.html)、[畅言评论](http://changyan.kuaizhan.com)，多说马上就要停止服务了，友言好像也没怎么维护,目前我已把自己的博客评论从多说转移到畅言了，在国内目前`网易云跟帖`和`畅言`还不错。

1.  注册并获得代码。

        *   若使用[多说评论](http://duoshuo.com)，注册多说后获得short_name。
    *   若使用[Disqus评论](https://disqus.com)，注册Disqus后获得short_name。
    *   若使用[来必力评论](https://livere.com)，注册来必力,获得data-uid。
    *   若使用[友言评论](http://www.uyan.cc/)，注册友言,获得uid。
    *   若使用[网易云跟帖评论](https://gentie.163.com/info.html)，注册网易云跟帖,获得productKey。
    *   若使用[畅言评论](http://changyan.kuaizhan.com)，注册畅言，获得appid，appkey。

2.  配置`主题_config.yml`：<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div><div class="line">5</div><div class="line">6</div><div class="line">7</div><div class="line">8</div><div class="line">9</div><div class="line">10</div></pre></td><td class="code"><pre><div class="line"><span class="comment">#Cmments</span></div><div class="line"><span class="attr">comment:</span></div><div class="line"><span class="attr">  duoshuo:</span> <span class="comment">## duoshuo_shortname</span></div><div class="line"><span class="attr">  disqus:</span> <span class="comment">## disqus_shortname</span></div><div class="line"><span class="attr">  livere:</span> <span class="comment">## 来必力(data-uid)</span></div><div class="line"><span class="attr">  uyan:</span> <span class="comment">## 友言(uid)</span></div><div class="line"><span class="attr">  cloudTie:</span> <span class="comment">## 网易云跟帖(productKey)</span></div><div class="line"><span class="attr">  changyan:</span> <span class="comment">## 畅言需在下方配置两个参数，此处不填。</span></div><div class="line"><span class="attr">    appid:</span> <span class="comment">## 畅言(appid)</span></div><div class="line"><span class="attr">    appkey:</span> <span class="comment">##畅言(appkey)</span></div></pre></td></tr></tbody></table></figure>

#### [](#3-2-百度统计 "3.2 百度统计")3.2 百度统计

1.  登录[百度统计](http://tongji.baidu.com/)，定位到站点的代码获取页面。
2.  复制`//hm.baidu.com/hm.js?`后面那串统计脚本id(假设为：8006843039519956000)
3.  配置`主题_config.yml`:<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml ](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line"><span class="attr">baidu_analytics:</span> <span class="number">8006843039519956000</span></div></pre></td></tr></tbody></table></figure>
> 注意： `baidu_analytics`不是你的百度`id`或者百度统计`id`
> 如若使用谷歌统计，配置方法与百度统计类似。

#### [](#3-3-卜算子阅读次数统计 "3.3 卜算子阅读次数统计")3.3 卜算子阅读次数统计
<figure class="highlight yml"><figcaption><span>主题_config.yml</span>[themes/BlueLake/_config.yml](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/_config.yml)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div></pre></td><td class="code"><pre><div class="line"><span class="attr">busuanzi:</span> <span class="literal">true</span></div></pre></td></tr></tbody></table></figure>

若设置为`true`将计算文章的阅读量(Hits)，并显示在文章标题下的`小手图标`旁。

#### [](#3-4-微博秀 "3.4 微博秀")3.4 微博秀

微博秀挂件的代码放在`layout/_widget/weibo.jade`下，需要您去[微博开放平台](http://open.weibo.com/)获取您自己的微博秀代码来替换。

1.  登录[微博开放平台](http://open.weibo.com/)，选择微博秀。
2.  为了与主题风格统一，作如下配置

        *   基础设置：高`400px`；勾选宽度自适应；颜色选择`白色`；
    *   样式设置：主字色`#333`；链接色`#40759b`；鼠标悬停色`#f7f8f8`；
    *   模块设置：去掉`标题`、`边框`、`粉丝`的勾选框，只留`微博`。

3.  复制代码里`src=""`里引号包裹的内容，替换到`layout/_widget/weibo.jade`<figure class="highlight stylus"><figcaption><span>weibo.jade</span>[layout/_widget/weibo.jade](https://github.com/chaooo/hexo-theme-BlueLake/blob/master/layout/_widget/weibo.jade)</figcaption><table><tbody><tr><td class="gutter"><pre><div class="line">1</div><div class="line">2</div><div class="line">3</div><div class="line">4</div></pre></td><td class="code"><pre><div class="line marked"><span class="selector-class">.widget</span></div><div class="line">  <span class="selector-class">.widget-title</span></div><div class="line">    i(class=<span class="string">'fa fa-weibo'</span>)= <span class="string">' '</span> + __(<span class="string">'新浪微博'</span>)</div><div class="line">  iframe(<span class="attribute">width</span>=<span class="string">"100%"</span>,height=<span class="string">"400"</span>,class=<span class="string">"share_self"</span>,frameborder=<span class="string">"0"</span>,scrolling=<span class="string">"no"</span>,src=<span class="string">"http://widget.weibo.com/weiboshow/index.php?language=&amp;width=0&amp;height=400&amp;fansRow=2&amp;ptype=1&amp;speed=0&amp;skin=5&amp;isTitle=0&amp;noborder=0&amp;isWeibo=1&amp;isFans=0&amp;uid=1700139362&amp;verifier=85be6061&amp;colors=d6f3f7,ffffff,333,40759b,f7f8f8&amp;dpc=1"</span>)</div></pre></td></tr></tbody></table></figure>
这只是为了和主题的风格统一，当然您也可以自由随意发挥。> 注意：最主要是是要把`src`里`uid=`和`verifier=`后面的字段替换为您自己代码里的就好。