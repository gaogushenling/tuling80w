# RocketMQ 的 Broker 有哪几种集群模式？

RocketMQ的Broker有三种集群模式：

1. 单Master模式：只有一个Master节点，其他都是Slave节点。Master节点负责响应客户端的请求并存储消息，Slave节点只同步Master节点的消息，也会响应部分客户端的读请求。这种模式的优点是简单易部署，但是存在单点故障的问题，如果Master节点宕机，会导致整个服务不可用。
2. Master-Slave模式（经典双集群部署）：一个Master节点对应多个Slave节点，Master和Slave都是独立的NameServer。Master节点负责响应客户端请求并存储消息，Slave节点只同步Master节点的消息，也会响应部分客户端的读请求。这种模式的优点是高可用性，即使Master节点宕机，Slave节点可以自动升级为Master节点，继续提供服务。但是，如果只有一个Master节点，存在单点故障的问题。
3. Dledger模式（高可用集群部署）：在Master-Slave模式的基础上增加了Raft协议，实现了自动脑裂后的数据高可靠性。即使某个节点从网络上掉下来或者宕机后，仍然能够保证所有的消息不会丢失。这种模式的优点是高可用性和高可靠性，即使某个节点出现故障，也能保证服务的可用性。

总的来说，单Master模式适合测试和开发环境，Master-Slave模式适合生产环境，而Dledger模式适合需要高可靠性的生产环境。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/fd2dzyhds20dtezg>