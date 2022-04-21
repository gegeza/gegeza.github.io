---
title: Go-1：Go语言简介与安装部署
date: 2022-04-21 18:58:48
categories:
- go
tags:
---
Go（又称Golang）时Google开发的一种静态强类型、编译型、并发性且具有垃圾回收功能的编程语言。
###### Go语言特点
* 作为编译型语言，运行效率高；
* 语法少，关键字少，开发高效且部署简单；
* 语言层面（关键字）即支持并发，利用多核失效高效并发；
* 类似于Java虚拟机的性能监控等，内置了Runtime；
* 拥有丰富的标准库与网络库，内置强大的工具（如gofmt等）；
* 可实现跨平台编译，内嵌C语言支持等

###### Go应用方向
* 服务器编程，如处理日志、数据打包、虚拟机处理、文件系统等；
* 分布式系统，数据库代理，分布式中间件等；
* 网络编程，Web应用或Api应用等；
* 云平台开发，Docker及K8s等都是Go语言开发
  
###### Go环境搭建

```shell
#方式一：yum安装（此时GOROOT=/usr/lib/golang;GOPATH=/root/go）
yum install -y golang;
#设置GOPATH到/adta/gopath
go env -w GOPATH=/data/gopath

#方式二：源码安装
#下载Golang安装包
cd /opt; wget https://golang.google.cn/dl/go1.18.1.linux-amd64.tar.gz;
#解压缩安装包到/usr/lib
tar zxvf go1.18.1.linux-amd64.tar.gz -C /usr/local
#设置GCROOT环境变量
echo 'export GOROOT=/usr/local/go' >> ~/.bash_profile
echo 'export PATH=$PATH:$GOROOT/bin' >> ~/.bash_profile
echo 'export GOPATH=/data/gopath' >> ~/.bash_profile
source ~/.bash_profile

#查看GO环境变量
go env
#修改go环境变量
go env -w GOPATH=/data/gopath
```
###### GO环境变量解析
* GOROOT：go官方标准文件的位置，该目录的bin下只有发行版的可执行文件，如go、gofmt等
* GO111MODULE：go module开发模式取代原有的GOPATH开发模式，1.16后默认为on
* GOPATH：src存放程序源码，bin存放可执行文件，pkg/mod存放通过通过``go get``下载的第三方包和依赖
* GOBIN：GOBIN=$GOPATH/bin，存放非go发行版的可执行文件，比如``go get/install``下载的非go发行版可执行文件

###### GO-hello world
创建一个hello.go
```go
package main

import "fmt"

func main(){
    fmt.Println("hello world")
}
```
可通过``go run hello.go``命令允许此go程序
也可以通过``go build hello.go``在当前目录下编译一个可执行二进制文件

###### GO开发模式
https://www.cnblogs.com/wjaaron/p/14797003.html