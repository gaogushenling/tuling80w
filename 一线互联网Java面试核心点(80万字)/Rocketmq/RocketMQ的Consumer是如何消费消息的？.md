# RocketMQ 的 Consumer 是如何消费消息的？

RocketMQ的Consumer消费消息的方式有两种：Push方式和Pull方式。

1. 在 Push 推模式下，RocketMQ 的 Broker 会主动将消息推送给对应的 Consumer。而 Consumer 会注册一个 MessageListener 回调函数，并在接收到消息后立即触发回调函数。
2. 在 Pull 拉模式下，Consumer 需要主动向 Broker 定期发送拉取消息的请求，自行完成处理消息，以及向 Broker 返回 ack 信息等步骤。

这两种模式都有各自的优缺点，适合不同的业务场景。其中：

1. Push 模式的优点是，实现比较简单，客户端只要注册回调方法，专心处理业务就可以了。并且消息到达 Broker 后立即会被推送到 Consumer，消息处理比较及时。缺点也比较明显，消费者需要与 Broker保持长时间的连接，对网络要求比较高。
2. Push 模式的有点是，Consumer 有更大的控制权，可以根据自身处理能力来调整拉取消息的频率，避免消息积压。并且拉模式只需要在拉取消息时与 Broker 保持短暂的网络连接，比较适合那些网络连接不是很稳定的环境。而对应的缺点则是，Pull 模式下，Consumer 需要自行调整消息拉取的频率，处理消息就没有 Push 模式那么及时。另外，Push 模式下，Consumer 的实现相对比较复杂，容易产生消息积压。

不论是Push方式还是Pull方式，从Broker获取消息后，Consumer都会进行消费处理。RocketMQ还提供了多种消费策略，如集群消费、广播消费、并行消费和顺序消费等，以满足不同的业务需求。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/vxnpfud2c295wer5>