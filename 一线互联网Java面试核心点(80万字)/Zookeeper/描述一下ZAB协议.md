# 描述一下 ZAB 协议

ZAB协议（Zookeeper Atomic Broadcast）是Zookeeper中用于实现分布式一致性的协议。该协议旨在确保分布式系统中的数据一致性和可靠性，并具有以下特点：

1. 支持崩溃恢复和消息广播：ZAB协议能够在Leader节点崩溃或因其他原因导致Leader缺失时，自动进入崩溃恢复模式，重新选举Leader节点，并继续进行消息广播。
2. 原子性保证：ZAB协议确保消息的原子性，即所有的事务请求都会被成功执行或全部失败回滚，不会出现部分成功的情况。
3. 一致性保证：ZAB协议通过多副本同步和消息广播机制，确保所有节点数据的一致性，避免数据不一致导致的系统故障。

ZAB协议包括三个阶段：

1. 准备阶段（Prepare）：Leader节点准备数据并通知所有Follower节点。
2. 确认阶段（Confirm）：Follower节点接收准备消息并准备自己所在的服务，并回复确认消息。
3. 广播阶段（Broadcast）：Leader节点将数据广播给所有Follower节点。

如果在确认阶段，Follower节点没有收到确认消息，那么会进入崩溃恢复模式，重新选举Leader节点。ZAB协议是实现分布式一致性和协调服务的核心协议之一。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ce3q0d9387ohkimh>