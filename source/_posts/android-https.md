title: Android之SSLException
date: 2016-06-08 17:50:40
tags:
 - Android
 - SSL
---

一开始Android是使用HTTP协议和后台API进行数据交互。在切换到HTTPS之后，发现在低版本的Android
设备上会出现下面的异常信息。
```java
javax.net.ssl.SSLException: SSL handshake aborted Connection reset by peer while calling webservice Android
```

经过一番搜索，发现是因为server在启用HTTPS协议的时候并没有加入对TLSv1协议的支持,在server添加TLSv1协议支持后问题就解决了。
而从Android的官方文档
我们可以看出虽然从Jelly Bean	4.1.x（API level 16）开始已经开始支持TLSv1.1，但是在API LEVEL16 －20默认
还是使用的TLSv1，如果你要在这些设备上使用TLSv1.1， 可以参考[这里](http://blog.dev-area.net/2015/08/13/android-4-1-enable-tls-1-1-and-tls-1-2/)。

![Android SSL](/post_images/android-ssl.png)

另外在解决问题的过程中发现一个很好用的网站[SSL Server Test](https://www.ssllabs.com/ssltest/index.html)，可以检查你的服务器对各个版本的SSL协议支持的情况。

Reference:
1. [Android SSLSocket](https://developer.android.com/reference/javax/net/ssl/SSLSocket.html)
2. [Android Build Numbers](https://source.android.com/source/build-numbers.html)
3. [http://stackoverflow.com/questions/20741405/javax-net-ssl-sslexception-ssl-handshake-aborted-connection-reset-by-peer-while](http://stackoverflow.com/questions/20741405/javax-net-ssl-sslexception-ssl-handshake-aborted-connection-reset-by-peer-while)
