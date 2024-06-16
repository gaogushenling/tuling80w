# RocketMQ 延迟消息是如何实现的？

RocketMQ的延迟消息实现是通过在消息发送时设置一个延迟级别，然后消息会被存储到DelayMessageService中，等待达到指定的延迟时间后再被重新推送到Broker的commitLog服务中。
具体流程如下：

1. Producer 将消息投递到Broker的commitLog服务。
2. commitLog服务判断消息是否为延迟消息，如果是，则将实际的topic和queueId保存到消息的属性中，并将topic设置成延迟topic（SCHEDULE_TOPIC_XXXX），queueId对应的延迟级别和消息投递时间保存在tagCode中。
3. 消息延迟服务（DelayMessageService）从SCHEDULE_TOPIC_XXXX主题循环拉取消息。
4. DelayMessageService根据tagCode找到对应的延迟队列，并按照延迟级别进行排序。
5. 当达到指定的延迟时间后，DelayMessageService会将消息重新推送到commitLog服务。
6. commitLog服务将消息推到Producer 指定的目标 Topic 中。
7. Consumer从 目标 Topic 中拉取消息。

RocketMQ支持最多18个延迟级别，可以满足不同延迟时间的需求。
另外，在新版本的 RocketMQ 中，使用时间轮机制，提供了指定任意时间的延迟消息功能。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ottm7mn0vgxy7qua>