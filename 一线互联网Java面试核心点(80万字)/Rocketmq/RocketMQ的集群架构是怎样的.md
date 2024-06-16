# RocketMQ的集群架构是怎样的

RocketMQ的集群架构包括四个主要角色：Name Server集群、Broker主从集群、Producer和Consumer客户端。

- Name Server集群是RocketMQ的一种轻量级的服务节点，负责注册和管理Broker的服务地址，提供服务的注册和发现功能。每个Broker节点都要跟所有的Name Server节点建立长连接，定义注册Topic路由信息和发送心跳。每个 NameServer 节点都会保存完整的 Broker 列表数据，并且 NameServer 个个节点之间不会同步数据。因此，NameServer 集群不会因为单个节点发生故障而停止服务。
- Broker 是 RocketMQ 的核心组件，负责存储和传输消息。一个 RocketMQ 集群通常包含多个 Broker 实例，共同协作来提高 RocketMQ 的可用性和吞吐量。其中，Master Broker，主节点，负责处理客户端的请求，并将消息存储到磁盘上，然后将消息同步复制给所有的从节点。而从节点，是Master Broker 的消息备份。
- 客户端包含 Producer 生产者和 Consumer 消费者。其中，Producer 负责将消息发送给 Broker。Producer 可以将消息发送到指定的 Topic，RocketMQ 会负责将消息存放到对应的 Broker 上。Consumer 可以订阅一个或多个 Topic，并从对应的 Broker 上接收消息进行处理。RocketMQ 的客户端提供了多种处理消息的方式，比如延迟消息、事务消息、集群消息、广播消息等。



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/whblnk2iu56i25po>