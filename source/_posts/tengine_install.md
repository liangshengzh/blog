title: tengine安装
date: 2017-08-05 20:02:30
tags:
---

下载tengine源码
http://tengine.taobao.org/download.html

安装

```shell
#解压缩
gunzip tengine-2.2.0.tar.gz
tar xvf tengine-2.2.0.tar

#安装PCRE
yum -y install pcre pcre-devel

#安装zlib
yum -y install zlib zlib-devel

#安装
yum -y install openssl openssl-devel

#编译安装

cd tengine-2.2.0
./configure
make
make install

```

下载lua 5.1
http://www.lua.org/ftp/lua-5.1.5.tar.gz
