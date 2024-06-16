# Zookeeper 的通知机制是什么

Zookeeper的机制可以感知某些事件的发生，并将这些事件通知给客户端。这种通知机制是异步的，也就是说，当事件发生时，Zookeeper会选择一种方式将事件通知给客户端，而不需要等待客户端的回应。
具体来说，Zookeeper允许客户端向服务端的某个Znode注册一个Watcher监听，当这个Znode的一些指定事件（如数据改变、节点删除、子节点状态变更等）发生时，Zookeeper就会通知客户端。这种Watcher机制使得Zookeeper能够实现分布式锁、发布订阅等功能。
另外，Zookeeper的机制也允许客户端在每个Znode节点上设置一个观察，如果被观察的Znode节点有变更，那么这个观察就会被触发，然后Zookeeper就会将这个观察所属的客户端接收一个通知包，告知节点已经发生了什么事件。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/sair4hkilvqh9i8g>