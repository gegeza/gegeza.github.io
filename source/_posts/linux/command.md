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
#添加/移除 防火墙规则  --permanent(永久的) --add/remove-port(添加/移除端口)
firewall-cmd --permanent --add-port=8080/tcp
#重新加载permanent防火墙规则，非permanent的规则将被丢失 
firewall-cmd --reload
#允许192.168.1.1访问本机8080端口 --add/remove(添加/移除) 
firewall-cmd --permanent --add-rich-rule="rule family=ipv4 source address=192.168.1.1 port port=80 protocol=tcp accept"
#本地80端口转发到192.168.1.1的8080端口
firewall-cmd --permanent --zone=public --add-forward-port=port=80:proto=tcp:toport=8080:toaddr=192.168.1.1
```
###### 进程/端口相关命令
```sh
#查看相关进程
ps -ef|grep java
#杀掉相关进程
ps -ef|grep java|grep -v "grep"|awk '{print$2}'|xargs kill [-9]
#查看进程占用的端口
cat /etc/services|grep mysql
#查看8080端口被哪些进程占用
lsof -i:8080
cat /etc/services|grep -w 80
netstat -anp|grep -w 80
```
###### 硬盘/目录相关命令
```sh
#查看硬盘及分区情况
lsblk
#查看当前文件夹大小 du:https://www.runoob.com/linux/linux-comm-du.html
du -sh
#查看当前目录下各文件大小（MB） 并按大小排序
du -am --max-depth=1|sort -rn
```
###### ssh免密登录
```sh
#生成本地公私钥
ssh-keygen -t rsa
#将本地id_rsa.pub的内容写入到远程~/.ssh/authorized_keys下
#如果免密登录无效 确认远程.ssh文件夹权限
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/authorized_keys
```
###### 后台启动服务
```sh
nohup sh xxx.sh > xxx.log 2>&1 &
```
