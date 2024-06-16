# ShardingSpehre 的分库分表功能是如何工作的？

ShardingSphere 的分库分表功能主要通过如下几个步骤完成：

1. 配置管控：ShardingSphere 需要解析复杂的配置信息，并且支持将配置信息上传到第三方注册中心。
2. SQL 解析：将要执行的 SQL 语句解析成抽象语法树。
3. SQL 路由：根据解析上下文匹配数据库和表的分片策略，并生成 SQL 的路由路径。
4. SQL 优化：用户只需要面向逻辑库和逻辑表来写SQL，最终由ShardigSphere的改写引擎将SQL改写为在真实数据库中可以正确执行的语句。SQL改写分为正确性改写和优化改写。
5. SQL 执行：ShardingSphere 采用一套自动化的执行引擎，负责将路由和改写完成之后的真实 SQL 安全且高效发送到底层数据源执行。
6. 结果归并：将从各个数据节点获取的多数据结果集，组合成为一个结果集并正确的返回至请求客户端。ShardingSphere 内部实现了流式归并和内存归并两种方案。

ShardingSphere 的分库分表功能使得应用程序能够透明地访问分布式数据库，而无需关心具体的数据库分片细节。开发人员只需配置好数据源和分片规则，ShardingSphere会自动处理数据的分布和查询路由。这有助于提高系统性能、可扩展性和可用性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/llezowetw2ia6qkc>