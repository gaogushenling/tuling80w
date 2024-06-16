# RabbitMQ 支持哪些消息模式？

RabbitMQ 支持多种消息传递模式，这些模式允许应用程序在不同的场景下进行灵活的消息交流。以下是几种最常见的消息分发机制：

- workQueue 工作序列机制： Producer 将消息发送到 queue，多个 Consumer 同时消费Queue 上的消息。消息会均匀的分配给多个 Consumer 处理。
- Publish/Subscribe 订阅发布机制： Producer 只负责将消息发送到exchange交换机上。Exchange 将消息转发到所有订阅的 Queue，并由对应的 Consumer 去进行消费
- Routing 基于内容路由机制：在订阅发布机制的基础上，增加一个routingKey，并根据routingKey判断 Exchange 将消息转发到哪些 Queue 上。
- Topic 基于话题路由机制：在基于内容路由的基础上，对routingKey增加了模糊匹配的功能。

另外，RabbitMQ 还支持双向同步的 RPC 机制，不过一般用得比较少。这些消息模式允许开发者根据应用程序的需求选择合适的消息通信方式，以满足不同的业务场景和可靠性要求。不同的模式可以用于构建各种类型的分布式系统和应用程序。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/tptbdrpcqfgqairx>