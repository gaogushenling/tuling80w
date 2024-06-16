# 模糊查询 like 语句该怎么写?

在MyBatis中，要执行模糊查询（使用LIKE语句），你可以使用SQL语句的字符串拼接或使用动态SQL来构建查询语句。下面我将为你展示两种常用的方式。
假设你要在一个查询中执行模糊查询，搜索用户的用户名包含特定关键字的情况。

1. **字符串拼接方式**：
```xml
<select id="searchUsers" resultMap="userResultMap">
    SELECT * FROM users
    WHERE username LIKE CONCAT('%', #{keyword}, '%')
</select>
```
在这个例子中，`#{keyword}`是参数占位符，表示要搜索的关键字。`CONCAT('%', #{keyword}, '%')`用于构建模糊匹配的字符串。

2. **动态SQL方式**：
```xml
<select id="searchUsers" resultMap="userResultMap">
    SELECT * FROM users
    <where>
        <if test="keyword != null">
            AND username LIKE CONCAT('%', #{keyword}, '%')
        </if>
    </where>
</select>
```
在这个例子中，使用了`<if>`标签来创建动态条件。只有在`keyword`参数不为null时，才会添加`AND username LIKE CONCAT('%', #{keyword}, '%')`这个条件到查询语句中。
无论哪种方式，你都可以在SQL语句中使用`LIKE`关键字来实现模糊查询，然后通过`#{}`语法或动态SQL的方式将参数值插入到查询语句中。选择哪种方式取决于你的项目需求和团队的偏好。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/nb59wacg7gadhdak>