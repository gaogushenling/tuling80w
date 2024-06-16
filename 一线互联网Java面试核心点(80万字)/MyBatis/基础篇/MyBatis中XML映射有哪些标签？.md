# MyBatis中XML映射有哪些标签？

除了常见的`select`、`insert`、`update`和`delete`标签，MyBatis的XML映射文件中还有一些其他标签用于更复杂的操作和配置。以下是一些常见的额外标签：

1.  **resultMap：** 用于定义查询结果与Java对象之间的映射关系，可以在多个查询中重复使用。 
2.  **association和collection：** 用于在`resultMap`中定义关联关系，用于处理一对一和一对多的关系。 
3.  **discriminator：** 在`resultMap`中使用，根据不同的条件选择不同的映射规则，用于处理继承关系的映射。 
4.  **sql：** 可以定义可重用的SQL片段，然后在其他地方引用。主要用于减少重复编写SQL语句。 
5.  **include：** 用于在SQL语句中引入外部定义的SQL片段，提高可维护性。 
6.  **if、choose、when、otherwise：** 用于在SQL语句中进行条件判断和逻辑控制，用于动态SQL的构建。 
7.  **trim、where、set：** 用于在SQL语句中添加固定的SQL片段，如`where`和`set`关键字，用于动态的条件构建。 
8.  **foreach：** 用于在SQL语句中进行集合迭代，适用于生成IN语句等。 
9.  **bind：** 用于在SQL语句中声明并绑定一个变量，可以在查询中重复使用。 
10.  **cache：** 用于配置二级缓存。 
11.  **selectKey：** 用于在插入操作后获取生成的主键值。 
12.  **insert、update、delete的flushCache、useGeneratedKeys、keyProperty属性：** 用于配置插入、更新和删除操作的一些属性。 

这些标签和属性可以让你更灵活地配置和使用MyBatis，从而适应不同的需求和场景。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ha8ant9tvyi5hp2v>