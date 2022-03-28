---
title: Hexo的安装与使用
date: 2022-03-28 16:41:50
categories:
- others
---
#### Hexo
[Hexo](https://hexo.io/zh-cn) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

本篇文章基于Hexo + Next + Github Page搭建自己的博客网站。

#### Hexo的安装
Hexo的安装依赖nodejs(版本不低于10.13 建议大于12.13)，Github相关资源依赖git
```sh
#确保nodejs和npm正确安装
node -v; npm -v
#确保git已安装
git --version
#安装hexo
npm install -g hexo-cli
#查看hexo版本
hexo -v
```

#### Hexo的部署
Hexo生成的静态网页可使用[Github Pages免费部署](../github_pages)<br/>
* clone Github资源库到本地，然后初始化hexo: ```hexo init```<br/>
* 安装npm依赖：```npm install```
* 本地启动服务验证：```hexo server/hexo s```
* 部署到远程：
  * [配置远程git地址](#git)
  * 安装npm部署插件：```npm install hexo-deployer-git -save"
  * 生成本地静态文件：```hexo generate/hexo g```
  * 推送到远程：```hexo deploy/hexo d```
#### Hexo常用命令
```sh
#初始化Hexo
hexo init
#清除静态文件和缓存
hexo clean
#部署博客网站（将生成的静态文件推送到远程仓库）
hexo deploy
#本地启动hexo服务
hexo server
#新建文章（位于source/_posts/test.md）
hexo new "test"
#新建一个页面（位于source/test/index.md）
hexo new page "test"
```

#### Hexo常见配置
###### <span id="git">git地址配置</span>
修改hexo目录下的_config.yaml
```yaml
deploy:
  type: git
  repo: git@github.com:gegeza/gegeza.github.io.git
  branch: blog
```
###### 主题配置
github上有很多hexo的主题，下载对应主题的hexo/themes目录下；然后修改hexo目录下的_config.yaml即可启用主题
```yaml
theme: next
```
###### 自定义样式配置
在theme/source/css下新建_custom文件夹，然后新建样式文件custom.styl；然后编辑theme/source/css/main.styl，新增以下代码块
```styl
//Custom css
// --------------------------------------------------
@import "_custom/custom"
```
###### 首行缩进配置
在自定义css文件中添加以下样式即可
```styl
.post-body p { text-indent: 2em; }
```
###### algolia搜索配置
待续
###### 其它官方配置
    详见[官网文档](https://hexo.io/zh-cn/docs/configuration)