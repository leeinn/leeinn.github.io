---
title: 搭建实记
date: 2022-03-09 21:21:47
tags: code
excerpt: 为什么需要个人Blog？
index_img: https://blog-img-1309919152.cos.ap-nanjing.myqcloud.com/blog1-%E6%90%AD%E5%BB%BA%E5%AE%9E%E8%AE%B0/hexo%E9%BB%98%E8%AE%A4%E4%B8%BB%E9%A2%98.png?imageMogr2/format/webp
---
# WHY
用户更喜欢算法推荐的各种内容待在信息茧房自娱，且也不会有刷不完的时候
这是Blog概念冷却后新信息平台的优势

Blog的记录属性是要大于分享的，可以没有观众面向自己定格当时的idea
纵使要自己搭图床传图片做压缩，极差的SEO
但不用担心文章消失平台跑路
关键关键由于是个人搭建，所有的内容UI都可以自定义，让页面变成自己的形状（大雾）
> 在互联网里拉点自己的屎

# 前置准备
1. git环境
2. node环境
3. github新仓库
命名要求:  `{{username}}.github.io`

# 安装hexo
全局安装hexo
```powershell
npm i -g hexo-cli
```
<br>

初始化博客文件夹
```powershell
hexo init {{folder}}
npm i
```
进入文件夹后
```powershell
hexo server
```
默认启动在 localhost:4000 就已经有第一个页面啦

![默认主题](https://blog-img-1309919152.cos.ap-nanjing.myqcloud.com/blog1-%E6%90%AD%E5%BB%BA%E5%AE%9E%E8%AE%B0/hexo%E9%BB%98%E8%AE%A4%E4%B8%BB%E9%A2%98.png?imageMogr2/format/webp)

(默认主题landspace如上，后面再提其他主题配置)

# 部署到 GitHub
这里默认已经有了命名好的仓库

## Step1. 安装 Git 部署相关插件
```powershell
$ npm i hexo-deployer-git --save
```

## Step2. 修改配置
修改根目录 _config.yml 文件中 deploy 字段
```json
deploy:
  type: 'git'
  repo:  https://github.com/username/username.github.io.git
  branch: main
```
- repo: 改为自己的仓库地址
- branch: 选择部署分支，默认main

> 从 2020 年 10 月 1 日开始，GitHub 上的所有新库都将用中性词「main」命名，取代原来的「master」，因为后者是一个容易让人联想到奴隶制的术语。（笑

## Step3. 指令部署
用以下指令部署到网站上
```powershell
hexo deploy
```

！然后就可以访问线上域名惹
`https://username.github.io`

# 常用命令
- hexo new 新建文章
- hexo server 启动本地服务器
- hexo clean 清除缓存文件和已生成的静态文件
- hexo generate 生成静态文件 (public文件夹)
- hexo deploy 部署网站

通常在完成每次修改后，会依次执行 clean -> generate -> deploy 避免更新不完全


以上指令都可以首字母缩写
```powershell
hexo n
hexo s
hexo g
hexo d 
```

# 结
不知道能坚持多久)