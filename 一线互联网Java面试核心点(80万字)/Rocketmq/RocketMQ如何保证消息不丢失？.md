# RocketMQ 如何保证消息不丢失？

RocketMQ 可以通过一系列措施保证全链路消息不丢失。

- producer 发送消息时，使用消息确认机制，确保消息被成功发送。例如，不要使用 oneway 发送方式。使用异步机制发送消息时，发送消息后要等待一段时间再停止 Producer。使用事务消息机制保证消息正常发送到 Broker。
- Broker 端将刷盘方式(FlushDiskType)配置为 Sync 同步刷盘，保证消息尽快写入到磁盘中，防止 Broker 出现故障造成内存中没有及时刷如到硬盘的那一部分消息丢失。
- 为了防止 Broker 端硬盘出现故障造成消息丢失，给 Broker 配置一个或多个 Slave 从节点，进行消息冗余。同时将消息同步方式配置为 Sync 同步同步。
- Consumer 端消费消息时，尽量不要异步处理消息。防止处理消息过程中出现错误，造成消息丢失。
- 最后，为了防止 RocketMQ 服务整体崩溃造成消息无法重复投递，可以在 RocketMQ 之外设定一个降级缓存，比如 Redis。当 RocketMQ 服务出现故障时，Producer 可以将消息写入到降级缓存中。等 RocketMQ 服务回复后，再从 Redis 中将消息重新写入 RocketMQ。

需要注意的是，这一系列方式可以保证 RocketMQ 全链路消息不丢失，但是，这其中每一个措施都会降低 RocketMQ 的服务性能。因此在实际应用时，还需要根据具体场景进行配置和管理，在服务的可靠性和高性能之间进行权衡。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/vg1tvfm5z3u9cggv>