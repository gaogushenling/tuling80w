# ArrayList和LinkedList有什么区别

ArrayList和LinkedList是Java集合框架中List接口的两个常见实现类，它们在底层实现和性能特点上有以下几点区别：

1. **底层数据结构：**ArrayList使用数组来存储元素，而LinkedList使用双向链表来存储元素。
2. **随机访问性能：**ArrayList支持高效的随机访问（根据索引获取元素），因为它可以通过下标计算元素在数组中的位置。而LinkedList在随机访问方面性能较差，获取元素需要从头或尾部开始遍历链表找到对应位置。
3. **插入和删除性能：**ArrayList在尾部添加或删除元素的性能较好，因为它不涉及数组的移动。而在中间插入或删除元素时，ArrayList涉及到元素的移动，性能相对较低。LinkedList在任意位置进行插入和删除操作的性能较好，因为只需要调整链表中的指针即可。
4. **内存占用：**ArrayList在每个元素都需要存储一个引用和一个额外的数组空间，因此内存占用比较高。而LinkedList由于需要存储前后节点的引用，相对于ArrayList占用的内存更多。

综上所述，如果需要频繁进行随机访问操作或在尾部进行插入和删除操作，可以选择ArrayList。如果需要频繁进行中间位置的插入和删除操作，或者对内存占用有一定限制，可以选择LinkedList。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/wcdss8mhkqiohbkg>