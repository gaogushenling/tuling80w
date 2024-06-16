# ShardingSphere的核心模块有哪些？他们是如何工作的？

ShardingSphere 是一个分布式数据库中间件，它由多个核心模块组成，包括 Sharding-JDBC、Sharding-Proxy 和 Sharding-Sidecar。

1. Sharding-JDBC 是 ShardingSphere 的核心模块之一，它提供了一个轻量级的 Java 框架，在 Java 的 JDBC 层提供额外的服务。使用客户端直连数据库，以 jar 包形式提供服务，无需额外部署和依赖，可理解为增强版的 JDBC 驱动，完全兼容 JDBC 和各种 ORM 框架。Sharding-JDBC主要用于嵌入到应用程序中，使应用程序能够透明地使用分片和读写分离功能，而无需对应用程序进行大规模修改。
2. Sharding-Proxy 是 ShardingSphere 的另一核心模块，它以代理的形式部署在应用程序与数据库之间，实现了对 SQL 的解析和改写以及请求的转发。用户无需修改任何应用程序代码，只需通过配置文件或 API 接口进行分片规则设置，即可实现数据分片和读写分离等功能。Sharding-Proxy主要用于需要将数据库访问透明地分片化的情况，而不想在应用程序中引入Sharding-JDBC的情况。它也可以用于监控和审计数据库操作。
3. Sharding-Sidecar 是 ShardingSphere 的规划中的第三个模块，它将作为一个独立的微服务，为用户提供更为灵活和强大的数据分片、分布式事务和数据治理等功能。Sarding-SideCar 主要用于云原生环境。

总体来说，ShardingSphere 的三个核心模块通过相互配合，共同实现了数据库的分片和分布式事务等功能的解决方案。开发人员可以根据其应用程序的要求选择合适的模块来集成ShardingSphere。这些模块共同为分布式数据库操作提供了更好的性能、可扩展性和可用性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/so4v2s0gb1eqv4la>