---
title: 如何使用http-server启用https的服务
categories:
  - node
type: 'tags'
data: 2018-12-26
tags:
  - node
  - http
---

> 有些时候你开发环境总是会有各种蛋疼的 https 需求，为了让自己更独立，小编进行了以下探险，如果不合格之处，还请指正和批评

1. 我们要在本地生成 key.pem 和 cert.pem 文件，命令如下：

```linux
openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
```

> 成功的话，会在当前目录生成两个文件（key.pem 和 cert.pem）这将生成一个证书密钥对，他将有效约 10 年（确切的说是 3650 天）

2. 然后进行 http-erver 的安装，建议全局

```linux
 npm install -g http-server
```

3. 以命令行的形式运行 http-server 并启用 SSL

```linux
http-server -S -C cert.pem -o
```

4. 如果出现以下的输出，就表明成功了

```linux
  $ http-server -S -C cert.pem -o
  Starting up http-server, serving ./ through https
  Available on:
    https://192.168.3.203:8080
    https://192.168.137.1:8080
    https://127.0.0.1:8080
  Hit CTRL-C to stop the server

```
