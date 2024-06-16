# RabbitMQ 如何实现消息的持久化？

RabbitMQ 允许消息的持久化，以确保即使在 RabbitMQ 服务器重新启动后，消息也不会丢失。RabbitMQ 可以通过以下方式实现消息的持久化：

1. 消息持久化：在 RabbitMQ 中，只需要在发送消息时，将delivery_mode属性设置为 2，就可以将消息标记为持久化。
2. 队列持久化：在 RabbitMQ 中声明队列时，也可以将队列声明为持久化。RabbitMQ 中的队列分为三种不同类型经典队列，仲裁队列和流式队列。其中，经典队列需要将durable属性设置为true。而仲裁队列和流式队列默认必须持久化保存。
3. 交换机持久化：与经典队列类似，RabbitMQ 也可以在声明交换机时，将交换机的 durable 属性设置为true，这样就可以将交换机标记为持久化。

RabbitMQ 的持久化机制会对其性能产生影响。因此，需要根据具体的业务场景和需求来权衡是否需要持久化以及需要哪种类型的持久化。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/sgow0uv2g78f96yb>