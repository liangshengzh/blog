title: Linux网络s工具
date: 2017-08-09 22:02:30
tags:
  -Linux
  -network
---


##### nethogs

nethogs是由[Arnout Engelen](http://arnout.engelen.eu/)开发的一个网络分析工具，用来分析每个进程占用的网络带宽, 如果你想要查看当前哪个进程占用的带宽比较多，nethogs就是一个不错的选择。

Centos上安装：
```shell
yun install -y nethogs
```
安装之后只需要运行nethogs命令就可以看到每个进程使用的网络带宽
[图片]()

命令行参数：

-d 数据刷新的频率，比如nethogs -d 10即为每十秒刷新一次
-v 打印版本信息
-h 帮助信息

//TODO其他参数

交互式控制命令:

m 切换网速显示的单位
r 按接收流量排序
s 按法发送流量排序
q 退出

netstat
显示网络状态
netstat -anp

-a  显示所有连线中的Socket。
-n  直接使用IP地址，而不通过域名服务器
-p  显示正在使用Socket的程序识别码和程序名称


iftop
