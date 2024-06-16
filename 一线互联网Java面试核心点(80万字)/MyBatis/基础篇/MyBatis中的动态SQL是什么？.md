# MyBatis中的动态SQL是什么？

MyBatis是一个流行的Java持久化框架，它允许你将数据库查询语句与Java代码分离，使得代码更加清晰易读。动态SQL是MyBatis中一个强大的特性，它允许你根据不同的条件在运行时构建不同的SQL查询语句。

举个例子来说明动态SQL的概念。假设你有一个搜索页面，用户可以根据不同的条件来搜索商品，比如商品名、价格范围和分类。使用动态SQL，你可以构建一个灵活的查询语句，只在用户提供相关条件时包含这些条件。
在MyBatis中，你可以使用`<if>`、`<choose>`、`<when>`、`<otherwise>`等标签来构建动态SQL。以下是一个简单的例子，假设你要根据用户的选择来动态构建查询语句：
```xml
<select id="searchProducts" resultType="Product">
  SELECT * FROM products
  <where>
    <if test="productName != null">
      AND name = #{productName}
    </if>
    <if test="minPrice != null">
      AND price >= #{minPrice}
    </if>
    <if test="maxPrice != null">
      AND price <= #{maxPrice}
    </if>
    <if test="category != null">
      AND category = #{category}
    </if>
  </where>
</select>
```
在这个例子中，如果用户输入了商品名、价格范围或分类，对应的条件会被包含在查询语句中。如果用户没有提供某个条件，那么相应的`<if>`块就会被忽略，从而构建出适合的查询语句。
动态SQL使得构建灵活的、适应不同情况的查询变得非常方便。这可以减少重复代码，提高代码的可维护性和可读性。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ctl9lgqlu10lae7n>