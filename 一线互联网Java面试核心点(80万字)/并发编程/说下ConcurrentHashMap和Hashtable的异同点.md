# 说下ConcurrentHashMap和Hashtable的异同点

**ConcurrentHashMap** 和 **Hashtable** 都是用于在多线程环境中存储和操作键值对的数据结构，但它们在实现和性能方面存在一些重要的异同点：
**相似点**：

1. **线程安全性：ConcurrentHashMap** 和 **Hashtable** 都是线程安全的，可以在多个线程同时访问它们而不需要额外的同步措施。
2. **键值对存储：** 两者都以键值对的方式存储数据，允许通过键来查找和访问值。

**不同点**：

1. **同步策略：**
   - **ConcurrentHashMap** 使用了更加精细的分段锁（Segment），每个分段可以看作一个小的独立的哈希表，不同分段之间可以并发操作，因此多线程访问不同分段的数据时不会阻塞。这使得在多线程环境中，**ConcurrentHashMap** 的性能更好，因为只有在访问相同分段的数据时才需要竞争锁。
   - **Hashtable** 使用了全局锁，也就是在任何时刻只能有一个线程访问 **Hashtable** 的数据，这导致了在高并发环境下性能较差。
2. **Null 键和值：**
   - **ConcurrentHashMap** 不允许存储 null 键或 null 值。如果尝试存储 null 键或值，会抛出 **NullPointerException**。
   - **Hashtable** 不允许存储 null 键和值。
3. **迭代器：**
   - **ConcurrentHashMap** 提供了更强大的迭代器支持，允许在遍历时对集合进行修改，而不会抛出 **ConcurrentModificationException** 异常。
   - **Hashtable** 在迭代时对集合进行修改会抛出 **ConcurrentModificationException** 异常。
4. **性能：**
   - **ConcurrentHashMap** 通常在高并发环境下性能更好，因为它使用了分段锁，允许多个线程同时读取和写入不同分段的数据。
   - **Hashtable** 的性能相对较差，因为它使用全局锁，只允许一个线程操作整个数据结构。

总的来说，**ConcurrentHashMap** 是在多线程环境中更常用的选择，因为它提供了更好的性能和灵活性，同时避免了 **Hashtable** 中的一些限制和性能瓶颈。然而，在某些情况下，如果不需要特定的高并发性能要求，**Hashtable** 仍然可以用作线程安全的数据结构。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/cazo0ro75gxuh49k>