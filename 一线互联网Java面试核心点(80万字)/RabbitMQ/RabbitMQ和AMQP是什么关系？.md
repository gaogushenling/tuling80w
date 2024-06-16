# RabbitMQ 和 AMQP 是什么关系？

RabbitMQ 和 AMQP 有着非常密切的关系，但是他们是属于完全不同的两个概念。

- AMQP： AMQP 不是一个具体的消息中间件产品，而是一个协议规范。他是一个开放的消息产地协议，是一种应用层的标准协议，为面向消息的中间件设计。AMQP 提供了一种统一的消息服务，使得不同程序之间可以通过消息队列进行通信。 SpringBoot 框架默认就提供了对 AMQP 协议的支持。
- RabbitMQ：RabbitMQ则是一个开源的消息中间件，是一个具体的软件产品。RabbitMQ 使用 AMQP 协议来实现消息传递的标准，但其实他也支持其他消息传递协议，如 STOMP 和 MQTT。RabbitMQ 基于 AMQP 协议定义的消息格式和交互流程，实现了消息在生产者、交换机、队列之间的传递和处理。

总之，AMQP 本质上是一个开放的标准，他不光可以被 RabbitMQ 实现，也可以被其他产品实现。通过这种标准的协议，实际上是可以在不同的消息中间件系统之间进行灵活的消息传递。只不过，目前具体实现这种标准的产品目前并不多，RabbitMQ 则是最有影响力的一个产品。因此，RabbitMQ 成了 AMQP 协议事实上的代表。SpringBoot 框架默认提供的 AMQP 协议支持底层也是基于 RabbitMQ 产品实现的。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/pg030f9y8fmsuvbd>