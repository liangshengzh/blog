title: Chrome的跨域问题
date: 2016-06-11 22:36:24
tags:
 - Chrome
 - CORS
---

由于安全性原因，现在所有支持Javascript的浏览器都实现了[同源策略](https://developer.mozilla.org/zh-CN/docs/Web/Security/Same-origin_policy)，
默认都会禁用跨域去加载资源。有时候我们用Chrome调适前端页面，需要跨域去请求服务器上面的数据是，就会遇到跨域的问题。

一种方法是我们临时用命令启动一个Chrome窗口，在启动的时候可以给它加上--disable-web-security 来禁用所有的安全策略。但是这需要你每次都要用命令行来启动Chrome, 稍显麻烦。如果把这个参数加到你快捷方式的启动参数中，又会降低你浏览器的安全性。

另外一种是我们可以安装一个非常好用的[Chrome插件](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en)， 当我们需要启用跨域访问时，只需要点击enable即可，比较方便。

![Chrome CORS](/post_images/chrome-cors.png)
