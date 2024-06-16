# UNION 与UNION ALL 的区别？

UNION和UNION ALL是在SQL中用于合并查询结果集的操作符，它们之间存在以下区别：

1. **UNION：**UNION用于合并两个或多个查询结果集，并去除重复的行。它将多个查询的结果**合并为一个结果集，并自动去除重复的行。**在执行UNION操作时，数据库会进行额外的去重操作，这可能会带来一定的性能开销。
2. **UNION ALL：**UNION ALL同样**用于合并查询结果集，但不去除重复的行。**它将多个查询的结果简单地合并在一起，包括重复的行。相比于UNION，UNION ALL不进行去重操作，因此执行效率更高。

**总结来说：**在使用时，可以根据具体的需求来选择合适的操作符。如果需要去除重复的行，可以使用UNION；如果不需要去重，或者对性能要求较高，可以使用UNION ALL。需要注意的是，使用UNION或UNION ALL时，要求被合并的查询结果的列数和列类型保持一致。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/nttmmftsi3uchf8s>