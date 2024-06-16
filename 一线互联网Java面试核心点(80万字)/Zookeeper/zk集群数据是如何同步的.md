# zk集群数据是如何同步的

Zookeeper集群的数据同步过程如下：

1. 集群启动时，会先进行领导者选举，确定哪个节点是Leader，哪些节点是Follower和Observer。
2. Leader会和其他节点进行数据同步，采用发送快照和发送Diff日志的方式。
3. 集群在工作过程中，所有的写请求都会交给Leader节点来进行处理，从节点只能处理读请求。
4. Leader节点收到一个写请求时，会通过两阶段提交机制来处理。
5. Leader节点会将该写请求对应的日志发送给其他Follower节点，并等待Follower节点持久化日志成功。
6. Follower节点收到日志后会进行持久化，如果持久化成功则发送一个Ack给Leader节点。
7. 当Leader节点收到半数以上的Ack后，就会开始提交，先更新Leader节点本地的内存数据。
8. 然后发送commit命令给Follower节点，Follower节点收到commit命令后也会更新本地内存中的数据。

这样，Zookeeper集群的数据同步就完成了。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/go0qlst8dskomdnh>