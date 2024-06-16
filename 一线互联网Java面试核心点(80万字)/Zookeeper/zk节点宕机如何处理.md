# zk 节点宕机如何处理

Zookeeper 必须集群部署，推荐配置不少于 3 个节点。Zookeeper 自身也要保证当一个节点宕机时，其他节点会继续提供服务。

1. 如果是一个 Follower 宕机，还有 2 台服务器提供访问，因为 Zookeeper 上的数据是有多个副本的，数据并不会丢失。
2. 如果是一个 Leader 宕机，Zookeeper 会选举出新的 Leader。

因此，Zookeeper 可以容忍一部分节点的宕机，但前提是要保证超过一半的节点是正常工作的。在这种情况下，Zookeeper 集群仍然可以正常提供服务。如果 Zookeeper 节点挂得太多，只剩一半或不到一半节点能工作，集群就会失效。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/dgg9lt3fawbnq4ph>