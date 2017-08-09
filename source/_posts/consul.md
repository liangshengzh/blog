title: consul
date: 2017-07-30 20:02:30
tags:
---

* Agent

  Agent 就是后台运行的一个consul进程，Agent可以以server或者client模式运行。

* Client

  客户端就是把所有的RCP请求转发到server的agent, client是无状态的。


* Server

  Server是带有一些扩展功能的agent。包括维护集群的状态，RPC请求的响应，数据中心间数据的交换。以及转发请求到Leader或者远程的数据中心

* Datacenter

  低延迟 高带宽

* Consensus

  选举Leader

* Gossip

  Consul是在Serf基础上构建的，Serf实现了完整的gossip协议

* LAN Gossip

  所有的节点都是在本地局域网或者同一个数据中心

* WAN Gossip




consul tempalte:

model:

* Once Mode
>consul template 会等待所有的依赖都渲染完成

* Exec Mode
>

* De-Duplication Mode
