# 说一下 spring 的事务隔离级别？

Spring的事务隔离级别是指在并发环境下，事务之间相互隔离的程度。Spring框架支持多种事务隔离级别，可以根据具体的业务需求来选择适合的隔离级别。以下是常见的事务隔离级别：

1. DEFAULT（默认）：使用数据库默认的事务隔离级别。通常为数据库的默认隔离级别，如Oracle为READ COMMITTED，MySQL为REPEATABLE READ。
2. READ_UNCOMMITTED：最低的隔离级别，允许读取未提交的数据。事务可以读取其他事务未提交的数据，可能会导致脏读、不可重复读和幻读的问题。
3. READ_COMMITTED：保证一个事务只能读取到已提交的数据。事务读取的数据是其他事务已经提交的数据，避免了脏读的问题。但可能会出现不可重复读和幻读的问题。
4. REPEATABLE_READ：保证一个事务在同一个查询中多次读取的数据是一致的。事务期间，其他事务对数据的修改不可见，避免了脏读和不可重复读的问题。但可能会出现幻读的问题。
5. SERIALIZABLE：最高的隔离级别，保证事务串行执行，避免了脏读、不可重复读和幻读的问题。但会降低并发性能，因为事务需要串行执行。

通过@Transactional注解的isolation属性来指定事务隔离级别。
```java
@Transactional(isolation = Isolation.READ_COMMITTED)
public void method1() {
    // ...
}

@Transactional(isolation = Isolation.REPEATABLE_READ)
public void method2() {
    // ...
}
```
需要根据具体的业务需求和并发情况来选择合适的事务隔离级别，以确保事务的隔离性和数据一致性。同时，需要注意不同数据库对事务隔离级别的支持可能有所差异，需要进行适当的测试和验证。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gqehgmn2p30ia031>