---
title: "Github Pages with hugo"
date: 2018-08-30T01:37:56+08:00
lastmod: 2018-08-30T01:37:56+08:00
draft: false
tags: ["hugo", "github"]
categories: ["hugo"]
author: "knowno"

contentCopyright: '<a rel="license noopener" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh" target="_blank">署名-非商业性使用-相同方式共享 4.0 国际 (CC BY-NC-SA 4.0)</a>'

---

> Hugo是由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。

<!--more-->

# 安装 hugo

```bash
$ brew install hugo
```
# 生成站点
```bash
$ hugo new site personal_site
$ cd personal_site
$ hugo new about
$ hugo new post/first.md # 注意，这里是 post
$ git init 
```
# 安装主题
```bash
$ git submodule add https://github.com/olOwOlo/hugo-theme-even themes/even # 添加主题为子模块
$ cp themes/even/exampleSite/config.toml ./ # 拷贝theme config文件
$ cp -r themes/even/exampleSite/content/ ./ # 拷贝theme template
$ hugo server --theme=even --buildDrafts # 本地预览
```
# 部署到GitHub
```bash
# 登录 Github，创建 username.github.io 仓库
$ hugo --theme=even --baseUrl="http://username.github.io/" # 生成public目录
$ cd public 
$ git a .
$ git c -m "init commit"
$ git submodule add https://github.com/knownosee/knownosee.github.io.git public # 添加 public 为模块
$ git remote add origin git@github.com:username/username.github.io.git
$ git push -u origin master
```