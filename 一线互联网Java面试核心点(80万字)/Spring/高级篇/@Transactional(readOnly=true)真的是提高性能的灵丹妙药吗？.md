# @Transactional(readOnly=true) 真的是提高性能的灵丹妙药吗？

今天，我想谈谈 Spring 提供的@Transactional(readOnly = true)。
 很多同学都说@Transactional(readOnly = true)提高了性能。那我们不得不思考：

- @Transactional(readOnly = true) Spring对它做了什么？真的提高了性能吗？ 

 

## @Transactional(readOnly = true)是如何工作的 ？Spring对它做了什么
```java
/**
	 * Prepare the transactional {@code Connection} right after transaction begin.
	 * <p>The default implementation executes a "SET TRANSACTION READ ONLY" statement
	 * if the {@link #setEnforceReadOnly "enforceReadOnly"} flag is set to {@code true}
	 * and the transaction definition indicates a read-only transaction.
	 * <p>The "SET TRANSACTION READ ONLY" is understood by Oracle, MySQL and Postgres
	 * and may work with other databases as well. If you'd like to adapt this treatment,
	 * override this method accordingly.
	 * @param con the transactional JDBC Connection
	 * @param definition the current transaction definition
	 * @throws SQLException if thrown by JDBC API
	 * @since 4.3.7
	 * @see #setEnforceReadOnly
	 */
	protected void prepareTransactionalConnection(Connection con, TransactionDefinition definition)
			throws SQLException {

		if (isEnforceReadOnly() && definition.isReadOnly()) {
			try (Statement stmt = con.createStatement()) {
				stmt.executeUpdate("SET TRANSACTION READ ONLY");
			}
		}
	}
```
          

所以， 实际上就是利用数据库的SET TRANSACTION READ ONLY， 开启只读事务，那只读事务对数据库意味着什么呢？

1.  通过执行 **SET TRANSACTION READ ONLY**，将当前事务设置为只读事务。这意味着在此事务内部，任何修改数据的操作（如 **INSERT**、**UPDATE**、**DELETE**）都将被禁止，只能执行读取操作（如 **SELECT**）。
2. 只读事务依然会运用上隔离级别（MVCC），需要事务隔离级别需要一定性能开销。


## 所以很多人一直纠结查询到底要不要设置只读，不设置是不是一样的？


一般情况下，执行查询时不开启事务的性能可能会稍微优于开启只读事务。这是因为不开启事务的查询操作不会涉及事务管理和隔离级别的开销，因此可能更为轻量级和高效。
当执行查询操作时，如果不需要事务的隔离级别和一致性保证，并且不需要使用事务管理的功能，那么不开启事务可能是更为合适的选择。这种情况下，查询操作将立即执行并返回结果，不会受到事务管理和隔离级别的开销影响。
然而，需要注意的是，如果应用需要保证数据的一致性和隔离性，并且希望查询操作与其他事务的修改行为相互独立，那么开启只读事务是必要的。在这种情况下，虽然可能会有一些额外的性能开销，但可以保证数据的一致性和隔离性，避免了并发操作可能引起的数据不一致问题。
综上所述，选择是否开启只读事务还是不开启事务，取决于具体的应用场景和需求。如果应用需要保证数据的一致性和隔离性，那么开启只读事务是必要的；如果不需要这些保证，并且追求查询操作的性能优化，那么不开启事务可能更为合适。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/of3lxcsm6h9rc8wd>