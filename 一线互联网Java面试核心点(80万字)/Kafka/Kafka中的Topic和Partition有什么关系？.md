# Kafka中的Topic和Partition有什么关系？

在Kafka中，Topic和Partition是两个密切相关的概念。

- Topic是Kafka中消息的逻辑分类，可以看作是一个消息的存储类别。它是按照不同的主题对消息进行分类，并且可以用于区分和筛选数据。每个Topic可以有多个Partition，每个Partition都是Topic的一个子集，包含了一部分特定的消息。
- Partition则是Kafka 中实际保存数据的单位。每个Topic可以被划分为多个Partition，而这些 Partition 会尽量平均的分配到各个 Broker 上。当一条消息发送到Kafka时，它会被分配到一个特定的Partition中，并最终写入 Partition 对应的日志文件里。这个分配过程是根据Partition的规则来完成的，比如可以按照消息的某个属性进行哈希或者按照时间戳进行排序等。

因此，Topic和Partition的关系是，Topic是消息的逻辑分类，用于区分和筛选数据，而Partition则是Topic的物理划分，用于将消息分配到不同的部分中以便于处理和存储。Topic 和 Partition 的设计对于高吞吐量和横向扩展非常有用。因为生产者和消费者只需要根据 Topic 进行具体的业务实现，而不用关心消息在集群内的分布情况。而在集群内部，这些 Partition 会尽量平均的分布在不同的 Broker节点上，从而提高了系统 整体的性能和可伸缩性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gy9dxx8cf1bgzw8o>