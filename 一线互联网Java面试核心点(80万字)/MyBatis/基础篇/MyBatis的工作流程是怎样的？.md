# MyBatis的工作流程是怎样的？

首先，你要配置 MyBatis，就是告诉它怎么干活。你得创建一个配置文件，里面得写上数据库怎么连接，还有映射文件在哪，还有其他的一些设置。
然后，你得写映射文件，这个东西定义了咱们的 Java 对象和数据库表是怎么对应的。就是告诉 MyBatis，怎么把查询结果映射到我们的 Java 对象里面去。
接下来，你得在 Java 代码里面弄一个数据访问的接口。这个接口里面定义了跟数据库打交道的方法，咱们在映射文件里面配置好对应的 SQL 语句。
咱们的应用启动的时候，MyBatis 会读咱们的配置文件和映射文件，然后它会用这些信息创建一个 SqlSessionFactory，这玩意挺重要的，是用来产生 SqlSession 实例的。
然后就是 SqlSession，咱们用 SqlSessionFactory 来创建这个东西。SqlSession 就是用来跑 SQL 操作的，你可以用它来查啊插入啊更新啊删除啊，啥都行。
然后，咱们就可以用 SqlSession 执行咱们之前写的数据访问接口里面的方法。MyBatis 会根据配置找到对应的 SQL 语句然后执行。
查询的结果会被 MyBatis 映射回咱们的 Java 对象里面。它会根据映射文件的设置，把查询结果的列和我们 Java 对象的属性对应起来，就是把数据变成对象。
最后别忘了，操作完了得关掉 SqlSession，这样数据库的连接等资源就能被释放了。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/nzu2vt1n8rcew03m>