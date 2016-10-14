---
layout: post
title: CentOS7 搭建git 服务器
date: 2016-10-13 15:32:24.000000000 +08:00
---
### install git
```bash
1.yum – y install git
```
### 创建一个裸仓库
```bash
$ cd srv
$ mkdir git
$ cd srv
$ cd git
$ git –init bare project.git #your project name
```
### 创建一个git用户
```bash
$ useradd git
$ passwd git
$ chown -R git:git project.git
```
### 添加ssh认证
#### 客户端
```bash
$ ssh-keygen -t rsa -C "your_email@example.com" #生成ssh key
$ cd ~.ssh
$ ls
$ vi id_rsa.pub #复制生成的key
```
#### 服务器
```bash
$ cd  /home/git/.ssh
$ vi authorized_keys #把收集到的id_rsa.pub文件内容 复制到这个文件中
```
### 仓库地址
仓库地址 git@ip_address:/srv/git/project.git
