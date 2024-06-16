# RocketMQ 如何保证消息顺序？

RocketMQ 提供了顺序消息机制，用来保证一组消息的局部有序性，具体实现步骤如下：

1. Producer 在发送消息时，通过设置一个 MessageQueueSelector 方法，将一组有顺序的消息，依次发送到对应 Topic 下的同一个 MessageQueue 上。而 MessageQueue 是能够保证 FIFO 先进先出的，这样就可以保证一组有顺序的消息在 Broker 上是有序的。
2. Consumer 在配置 MessageListener 时，需要指定为 MessageListenerOrderly 实现类。这样就能保证一组有序的消息可以按照发送时的顺序进入 Consumer 进行处理，从而保证这一组消息的顺序。

但是在使用顺序消息时，有几个需要注意的问题：

1. RocketMQ 的顺序消息机制只保证一组消息的局部有序性，而并不保证所有消息的全局有序性。应用需要自行定义消息中的一些标识符来确定消息的顺序。
2. 顺序消息机制会给 MessageQueue 添加线程锁，这会降低 Consumer 的消息吞吐量。
3. 如果 Consumer 消费消息出现错误，会将整个 MessageQueue 阻塞，而无法单独重试这一条消息。这样非常容易导致 Topic产生大量的消息积压，因此使用顺序消息要尽量保证 Consumer 的消息处理正确性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/dpli1grw8pt3tdhr>