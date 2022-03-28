---
title: Github Pages的部署与使用
date: 2022-03-28 19:08:52
categories:
- others
tags:
---
#### Github Pages
Github Pages是一个由Github提供的免费个人静态网站托管服务，可用于个人博客搭建、demo演示等等

注：本文章中``yourGithubName``指的是你在github网站上的用户名
#### 使用方法
###### 创建github repository
前往github官网New Repository；

如果资源名称为yourGithubName.github.io那么部署好之后即可通过https://yourGithubName.github.io 访问，否则要通过https://name.github.io/repositoryName访问
###### 开启Pages选项
* 进入repository首页 > Settings > Pages
* 选择branch作为网站目录
* 点击Save按钮保存配置即可

###### 访问地址展示效果
本地生成网站静态文件后，推送到上面选择的分支；然后访问对应的网站即可


#### 设置自定义域名
如果你拥有自己的域名 则可以将https://yourGithubName.github.io改成你自己的域名地址
* 在静态页面根目录创建一个CNAME文件，文件内容即为你的域名，比如：https://blog.muern.com
* 域名解析记录添加一个CNAME类型记录，记录值为yourGithubName.github.io
* 现在可以访问自己的域名试一下啦