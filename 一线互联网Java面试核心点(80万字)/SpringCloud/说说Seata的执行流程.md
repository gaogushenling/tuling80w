# 说说Seata的执行流程

Seata的整体执行流程设计为两阶段提交，其执行流程如下：
第一阶段：

1. 所有RM（Resource Manager，资源管理者，业务代码中被远程调用的部分）执行自己的本地事务。在执行本地事务时，seata使用数据源代理，在执行SQL前，对SQL进行解析，生成前置镜像SQL和后置镜像SQL，同时向undo log插入一条数据，方便后期出现异常做回滚，然后向TC（Transaction Coordinator，事务协调器）注册分支事务，提交本地事务，最后向TC提交它的分支事务状态。

第二阶段：

1. 所有RM本地事务执行成功，此时TM（Transaction Manager，事务管理器）会向TC发起全局事务提交，TC会立马释放全局锁然后异步驱动所有RM做分支事务的提交。
2. 存在一个RM本地事务不成功，此时TM会向TC发起全局事务回滚，TC会驱动所有的RM做回滚操作，等待所有的RM回滚成功后然后再释放全局锁。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gdty21t3kb0z1k0q>