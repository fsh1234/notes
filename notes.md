# 未分类的笔记

## 运行环境

[jdk下载]http://jdk.java.net/13/

## Linux

### 给与文件夹读写权限

```shell
$sudo chmod 777 [文件夹地址]
```

## 搜索

[Github-Demo](https://github.com/search/advanced)

### 重要

双引号，比如："GitNavi"
完全匹配搜索、准确搜索

减号，比如：GitNavi -百度
排除不想要的关键词

波浪号，比如：Java ~教程
同义词搜索

星号，比如：搜索*擎
通配符匹配搜索

### 扩展

site，比如：Java site:youmeek.com
站内搜索

OR（必须大写），比如：GitNavi OR YouMeek
一起找出两个关键词相关结果

filetype，比如：filetype:pdf Spring
找出 Spring 相关的 PDF 文件

related，比如：related:gitnavi.com
找出 gitnavi.com 有关联的内容（具体什么关系不知道）
link，比如：link:gitnavi.com
找出链接到 gitnavi.com 的内容

inurl，比如：inurl:cas/login
找链接中包含：cas/login

allinurl，比如：allinurl:cas/login service
找链接中既包含 cas/login，也包含 service 的内容

intitle，比如：intitle:GitNavi
找标题中包含：GitNavi

allintitle，比如：allintitle:Java 单元测试
找标题中既包含 Java，也包含 单元测试 的内容

intext，比如：intext
找正文中包含：GitNavi
