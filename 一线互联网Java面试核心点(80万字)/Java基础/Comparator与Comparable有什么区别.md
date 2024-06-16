# Comparator与Comparable有什么区别

Comparator和Comparable都是Java中用于对象排序的接口，它们之间有一些关键的区别。
**Comparable接口是在对象自身的类中实现的**，它定义了对象的自然排序方式。一个类实现了Comparable接口后，可以使用compareTo方法来比较当前对象和其他对象的大小关系。这个接口只能在对象自身的类中实现，不需要额外的比较器。
**Comparator接口是一个独立的比较器**，它可以用于对不同类的对象进行排序。Comparator接口允许在对象类之外创建一个单独的比较器类或匿名类，并使用它来定义对象的排序规则。比较器通过实现compare方法来比较两个对象的大小关系。
因此，主要区别如下：

- Comparable接口是在对象自身的类中实现，定义了对象的自然排序方式。
- Comparator接口是一个单独的比较器，定义了用于排序的规则，可以用于不同类的对象排序。
- Comparable是内部排序，对象的类必须实现Comparable接口才能进行排序。
- Comparator是外部排序，可以独立定义排序规则，并与任何类的对象一起使用。

在使用时，如果需要对对象的默认排序进行操作，可以实现Comparable接口。如果需要对不同类的对象进行排序，或者需要定义多种不同的排序规则，可以使用Comparator接口。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/rihz8qgxpcbgkdam>