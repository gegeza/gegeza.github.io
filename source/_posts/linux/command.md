---
title: Linux常见命令
date: 2022-03-30 19:59:04
categories:
- linux
tags:
---
###### 防火墙相关命令
```sh
#查看防火墙状态
systemctl status firewalld
#查看防火墙规则
cat /etc/firewalld/zones/public.xml
#添加防火墙规则
firewall-cmd --add-port=8080/tcp --permanent
#移除防火墙规则
firewall-cmd --remove-port=8080/tcp --permanent
#reload防火墙规则
firewall-cmd --reload
```