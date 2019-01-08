---
layout: post
title: '一个你说不上来的URL详解'
date: 2018-12-19
categories:
  - JavaScript
tags:
  - URL
  - HTTP
---

# url

> `统一资源定位符`（或程统一资源定位器/定位位置/URL 等）[Unifrom Reasource Locator, 缩写：URL]，有时也称作是网页地址（网址）。

1. 统一资源定位符的标准格式如下：
   > `协议类型：[//[访问资源需要的凭证信息@]服务器地址[:端口号]][/资源层级UNIX文件]文件名[?查询][#片段ID]`
 > http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument

- 传输协议，例如 HTTP
- 层级 URL 标记傅好（为[//],固定不改变）
- 访问资源需要的凭证信息（可以省略）
- 服务器（通常域名，有时间为 IP 地址）
- 端口号（以数字的形式表示，若为 HTTP 默认，“:80”可以省略）
- 路径（以'/'字符区别路径中的每一个目录名称）
- 参数： （GET 模式的窗体参数，以'？'字符为起点，每个参数以'&'隔开，再以=分开参数名称与数据，通常以 UTF-8 的 URL 编码，避开字符冲突的问题）
- 片段： 以#字符为起点是资源本身的另一部分的锚点. 锚点表示资源中的一种“书签”，给浏览器显示位于该“加书签”位置的内容的方向。例如，在 HTML 文档上，浏览器将滚动到定义锚点的位置;在视频或音频文档上，浏览器将尝试转到锚代表的时间。值得注意的是，＃后面的部分（也称为片段标识符）从来没有发送到请求的服务器。

##### linTo

[什么是 URL？](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/What_is_a_URL)
