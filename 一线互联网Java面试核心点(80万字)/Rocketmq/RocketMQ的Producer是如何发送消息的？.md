# RocketMQ 的 Producer 是如何发送消息的？

RocketMQ的Producer有三种消息发送模式：

1. 同步发送（Sync Send）：这是默认的发送模式。在同步发送模式下，发送者发送一条消息后会等待 Broker 的响应，直到 Broker 确认收到消息并返回结果。如果发送失败，将会抛出异常。这种模式下，Producer 可以确保消息成功发送到了 Broker，消息安全性更高。但是，由于需要等待 Broker 的响应，可能会引起较大的发送消息延迟。
2. 异步发送（Async Send）：这种模式下，Producer发送消息后不会等待Broker的响应，而是继续执行后续操作。Producer可以注册回调函数，在消息发送完成后Broker会异步调用回调函数。这种模式可以提高 Producer 的吞吐量和响应速度，但是，Producer 需要在回调函数中自行处理 Broker 的消息响应，对客户端代码要求较高。并且，在这种模式下，如果消息发送出现问题，Producer 只能通过回调函数处理，这样 Producer 处理消息错误的时机是有延迟的。
3. 单向发送（Oneway Send）：这种模式下，Producer 发送消息后不关心消息是否被 Broker 成功接收和存储，也不等待 Broker 的响应。这样，Producer 发送消息的效率是最高的。但是，消息的安全性就无法保证。这种模式通常适用于那些强调消息吞吐量而不关心消息可靠性的场景，例如日志消息。

通常，RocketMQ允许在不同的场景下使用不同的消息发送模式，以满足不同的业务需求。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ws61ctgxr8kv3378>