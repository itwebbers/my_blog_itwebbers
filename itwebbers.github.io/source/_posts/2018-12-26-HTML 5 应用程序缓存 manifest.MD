---
title: HTML5 应用程序缓存 manifest
categories:
  - HTML5
date: 2018-12-26
type: 'tags'
tags:
  - HTML5
---

# 概念

> 应用程序缓存： web 应用可进行缓存，并在没有因特网连接时进行访问

## 应用程序缓存的三大优势

- 离线浏览： 用户可以在没有网络的情况下使用它们
- 速度： 页面读取本地缓存加载更加的快
- 减少服务器负荷： 浏览器将只从服务器下载更新过或者更改过的资源

## Cache Manifest 使用

> 如需启动应用程序缓存，请在 html 的标签中包含 manifest 属性

```html
<!DOCTYPE html manifest='index.appcache'>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>manifest</title>
  </head>

  <body>
    <h1>manifest</h1>
  </body>
</html>
```

> - 这里特殊说明一下： 如果要使用缓存的话，建议使用 HTTPs，因为以 chrome 为例，会有这样的提示：
>   `[Deprecation] Application Cache is restricted to secure contexts. Please consider migrating your application to HTTPS, and eventually shifting over to Service Workers. See https://goo.gl/rStTGz for more details.`

> - 如果出现了一下的报错
>   `Application Cache Error event: Manifest fetch failed (404)`
>   只要的原因就是因为 manifest 文件需要使用配置正确的 MINI-type，即'text/cache-manifest'.必须在 web 服务器上进行配置

## manifest 文件

> manifest 文件可以分为三部分：

- cache manifest: 在此标题下列出的文件将在首次下载后进行缓存
- network： 此标题下列的文件需要与服务器的连接，且不会被缓存
- fallback 在此标题下列出的文件规定当页面无法访问时的回退页面（一般是 404 页面）

## cache manifest

> 第一行 cache manifest 是必须的， 下面的三个文件，无论是用户是否断开因特网，这些资源依然可以访问：

```JavaScript
  CACHE MANIFEST
  index.css
  main.js
  login.svg
```

## network

> 下面的 NETWORK 小节规定文件'login.html'永远不会被缓存，且离线时是不可以使用的

```JavaScript
  NETWORK
  login.html
```

> `注意： 可以使用 * 来指示所有其他资源/文件都需要因特网连接`

```JavaScript
 NETWORK
 *
```

## fallback

> 无法建立因特网连接的时候，则用'offline.html'替代/src/目录中的所有文件

```JavaScript
  FALLBACK
  /src/  /404.html
```

## 更新缓存

> 以下情况会更更新缓存

- 用户清空浏览器缓存
- manifest 文件被修改
  > 在完整的 manifest 文件中，以 # 开头的是注释，应用的缓存会在 manifest 文件更改时被更新
- 由程序来更新应用缓存

```JavaScript
$(document).on("mobileinit", function () {
  //register event to cache site for offline use
cache = window.applicationCache;
cache.addEventListener('updateready', cacheUpdatereadyListener, false);
cache.addEventListener('error', cacheErrorListener, false);
function cacheUpdatereadyListener (){
    window.applicationCache.update();
    window.applicationCache.swapCache();
    }
    function cacheErrorListener() {
        alert('site not availble offline')
    }
}
```
