# mysql 中in 和exists 的区别

当谈到 MySQL 中的 IN 和 EXISTS 时，它们都是用于查询和筛选数据的条件语句，但有一些重要的区别：

1. **IN关键字：**使用 IN 条件时，我们提供一个固定的值列表，然后将其与指定列的值进行比较。如果列中的值与列表中的任何一个值匹配，就会返回结果。IN 条件适合用于确定某个字段的值是否在给定的值列表中。

例如，SELECT * FROM table_name WHERE column_name IN (value1, value2, value3); 
如果 column_name 的值与 value1、value2 或 value3 中的任何一个相匹配，那么这条记录将会被返回。

2. **EXISTS关键字：**使用 EXISTS 条件时，我们需要指定一个子查询。查询的结果并不重要，而是判断子查询是否返回了至少一行结果。如果子查询返回了结果，EXISTS 条件就会被认为是满足的。EXISTS 条件适合用于判断某个条件是否至少存在于子查询的结果中。

例如，SELECT * FROM table_name WHERE EXISTS (SELECT * FROM another_table WHERE condition); 
如果子查询(SELECT * FROM another_table WHERE condition)返回了至少一行结果，那么主查询中的记录将会被返回。
**总结来说：**

- 使用 IN 条件时，比较的是指定列的值是否在给定的值列表中。
- 使用 EXISTS 条件时，判断的是子查询是否返回了至少一行结果。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/zkldg4rglqxytaf9>