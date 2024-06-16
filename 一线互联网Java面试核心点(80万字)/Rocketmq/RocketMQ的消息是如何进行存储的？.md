# RocketMQ 的消息是如何进行存储的？

RocketMQ是采用分布式存储的方式来存储消息的。每个Broker的存储结构主要包括：CommitLog、ConsumeQueue和IndexFile。

- CommitLog是消息存储的物理文件，存储了所有消息的主题、标签、时间戳等基本信息和消息体。每个Broker上的CommitLog被当前机器上的所有ConsumeQueue共享。
- ConsumeQueue是消息的逻辑队列，存储了具有相同属性（如Topic、队列ID等）的消息。每个Broker上有多个ConsumeQueue，每个Topic的消息都对应一个ConsumeQueue。Consu meQueue采用顺序写入、随机读取的方式存储消息，同时支持高效的预写日志和刷盘策略。
- IndexFile是消息索引文件，存储了消息在CommitLog中的偏移量和消息物理偏移量对应关系，采用Hash索引方式加速定位。

RocketMQ通过这种分布式存储方式可以高效地存储和访问大量消息，同时也具有良好的可扩展性和可靠性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ac2mebudgnn2genu>