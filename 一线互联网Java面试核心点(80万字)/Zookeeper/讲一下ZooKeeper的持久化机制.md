# 讲一下 ZooKeeper 的持久化机制

Zookeeper的持久化机制主要涉及两种数据存储方式：内存存储和磁盘存储。

1. 内存存储：这是Zookeeper默认的数据存储方式。在内存存储中，Zookeeper将所有数据保存在内存中，而不是磁盘上。当Zookeeper关闭或发生故障时，内存中的数据会丢失。为了提高性能，Zookeeper采用了延迟写盘的策略，即将数据先写入内存，再异步地写入磁盘。这种方式可以减少磁盘I/O操作，提高系统的响应速度。
2. 磁盘存储：为了解决内存存储数据丢失的问题，Zookeeper提供了磁盘存储的持久化方式。在磁盘存储中，Zookeeper将数据保存在磁盘上，并在启动时从磁盘加载数据。为了提高写入性能，Zookeeper采用了两种机制：快照（snapshot）和事务日志（transaction log）。快照是Zookeeper数据树的一个完整拷贝，而事务日志记录了所有的数据更改操作。通过这两种机制，Zookeeper可以在系统故障时恢复数据。

Zookeeper的持久化机制可以根据实际需求进行选择和配置。对于需要高可用性和实时性的场景，可以选择内存存储；对于需要更可靠性和可恢复性的场景，可以选择磁盘存储。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ugbio6opgz73qh7w>