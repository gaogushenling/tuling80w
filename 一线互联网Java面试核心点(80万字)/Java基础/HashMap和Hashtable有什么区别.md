# HashMap和Hashtable有什么区别

HashMap和Hashtable都是Java集合框架中Map接口的实现类，它们有以下几个区别：

1. **线程安全性：**Hashtable是线程安全的，而HashMap是非线程安全的。Hashtable通过在每个方法前加上synchronized关键字来保证线程安全性，而HashMap则没有实现这种机制。
2. **null值：**Hashtable不允许键或值为null，否则会抛出NullPointerException异常。而HashMap可以存储key和value为null的元素。
3. **继承和接口实现：**Hashtable继承自Dictionary类，而HashMap则继承自AbstractMap类并实现了Map接口。
4. **初始容量和扩容机制：**Hashtable在创建时必须指定容量大小，且默认大小为11。而HashMap可以在创建时不指定容量大小，系统会自动分配初始容量，并采用2倍扩容机制。
5. **迭代器**：迭代器 Iterator 对 Hashtable 是安全的，而 Iterator 对 HashMap 不是安全的，因为迭代器被设计为工作于一个快照上，如果在迭代过程中其他线程修改了 HashMap，则会抛出并发修改异常。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/sh7mkz2o95ng1n1g>