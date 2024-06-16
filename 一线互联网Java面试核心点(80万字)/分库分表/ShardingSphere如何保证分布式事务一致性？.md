# ShardingSphere如何保证分布式事务一致性？

ShardingSphere 保证分布式事务一致性的方式主要有两种：XA事务和柔性事务。

- XA事务通过在准备阶段和提交阶段进行两阶段锁，来保证分布式事务的一致性。在准备阶段，ShardingSphere 会对所有的数据库节点进行锁定，保证在事务执行过程中不会有其他操作干扰。在提交阶段，ShardingSphere 会对所有的数据库节点进行提交或者回滚操作，以保证事务的一致性。
- 柔性事务则是通过BASE理论来实现的。BASE理论包括基本可用（Basically Available）、软状态（Soft State）和最终一致性（EventualConsistency）。在柔性事务中，ShardingSphere 采用了柔性状态和最终一致性的理念，允许短时间内不同步，最终保证数据的一致性。

另外，ShardingSphere 还提供了接入分布式事务的 SPI，并针对性能要求较高、一致性要求较低的业务提供了基于柔性事务的方案。在整合Seata AT事务时，ShardingSphere 通过扩展服务间的传输机制，将Seata的全局事务上下文传递到分片执行引擎中，从而保证了分布式事务的一致性。
总之，ShardingSphere 通过XA事务和柔性事务两种方式来保证分布式事务的一致性。在实现过程中，ShardingSphere 还提供了相应的工具类和抽象类，方便开发者进行相关操作。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/zakekhrmhx7xkx5u>