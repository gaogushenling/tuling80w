# 如何在 MyBatis 中进行分页查询？

在 MyBatis 中进行分页查询是一个常见的需求，特别是在处理大量数据时。下面我会向你解释如何进行分页查询，并提供一些常用的分页插件和技巧。

**基本的分页查询：**

MyBatis 提供了一个简单的方式来实现分页查询，主要涉及到两个参数：`offset` 和 `limit`。`offset` 表示从结果集的哪一行开始取数据，而 `limit` 则表示每页显示多少条数据。在 SQL 语句中，你可以使用类似于 `LIMIT offset, limit` 的语法来实现分页查询。

下面是一个示例 SQL 查询，展示如何在 MyBatis 中进行分页查询：

```xml
<select id="getPagedData" resultType="YourResultType">
  SELECT *
  FROM your_table
  LIMIT #{offset}, #{limit}
</select>
```

在 Java 代码中，你需要为 `offset` 和 `limit` 参数提供值。`offset` 可以通过公式 `(pageNum - 1) * pageSize` 计算得出，其中 `pageNum` 表示页码，从 1 开始，`pageSize` 表示每页显示的记录数。

**常用的分页插件和技巧：**

1.  **PageHelper 插件：** PageHelper 是一个流行的 MyBatis 分页插件，它简化了分页查询的操作。你只需要在查询方法前调用 `PageHelper.startPage(pageNum, pageSize)`，然后执行查询语句，PageHelper 就会自动处理分页逻辑。 
2.  **使用 RowBounds：** 在 MyBatis 中，你还可以使用 `RowBounds` 对象来实现分页查询。通过在查询方法中传递一个 `RowBounds` 对象，你可以指定从哪一行开始取数据，以及每页显示多少条数据。 
3.  **自定义分页插件：** 如果你有特殊的分页需求，你可以编写自己的分页插件。这可能涉及到在 MyBatis 的拦截器链中插入你自己的逻辑，以实现定制化的分页处理。 

总之，MyBatis 中的分页查询并不复杂，你可以选择基本的分页方式，也可以利用一些分页插件和技巧来简化操作。记得考虑好性能问题，避免在分页查询时产生过多的数据库查询操作。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gvc338obfnod0s94>