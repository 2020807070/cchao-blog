---
title: 💋嘴对嘴脸贴脸带你用Vuepress撸一个定制博客并发布
headimg: 'http://cchao.123hao123.top/%E6%9C%AA%E6%A0%87%E9%A2%98-4.png'
date: 2019/4/25
description: 👄对👄带你搭建一款静态博客，包含评论功能。
tags:
  - vuepress
  - blog
---

<!-- https://vuepress.vuejs.org/ -->
## vuepress 博客






## 基本配置

### 配置文件

### 主题配置



## 接入评论






## 发布github

 ### 使用github托管页面
 省去了买空间或者服务器的钱💰
首先登陆自己的github

右上角头像旁边的➕ --->  `New repository`

![](https://user-gold-cdn.xitu.io/2019/5/30/16b0659ea6a51e67?w=475&h=258&f=png&s=12313)

注意 要想页面出来 ！！
GitHub要站点的仓库名称必须是 用户名.github.io

比如我的是2020807070.github.io


然后把打包的dist文件拖出来

上传就可以了

然后访问用户名.github.io

想绑定自己的域名怎么办？ 请继续往下看

以阿里云为例：

登录-> 控制台 -> 域名

点击`解析`

![](https://user-gold-cdn.xitu.io/2019/5/30/16b066f6bfdece12?w=668&h=446&f=png&s=27319)

点击`添加记录`

![](https://user-gold-cdn.xitu.io/2019/5/30/16b0670444dfae17?w=428&h=405&f=png&s=20694)

记录类型选择`CNAME`

![](https://user-gold-cdn.xitu.io/2019/5/30/16b067161ebaa4cc?w=661&h=483&f=png&s=25358)



### 解析域名

创建`CNAME`文件夹放置与根目录

![](https://user-gold-cdn.xitu.io/2019/5/31/16b0b923807f573c?w=637&h=265&f=png&s=35435)

icon

































## 懒癌晚期患者请直接看这里


### 安装脚手架
```
$ npm i cchao-cli -g
```

### 输入命令
```
$ cchao-cli init
```


### 功能演示
![](https://user-gold-cdn.xitu.io/2019/5/15/16abab5f9703cec4?w=542&h=603&f=gif&s=40537)



### 下载依赖
```
$ npm install
```



### 运行项目
```
$ npm run start
```
