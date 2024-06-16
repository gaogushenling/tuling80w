# ConcurrentHashMap的存储结构是怎样的

ConcurrentHashMap在Java7 中使用的**分段锁**，也就是每一个 **Segment** 上同时只有一个线程可以操作，每一个 Segment 都是一个类似 **HashMap 数组**的结构，它可以扩容，它的冲突会转化为链表。但是Segment 的个数一但初始化就不能改变，默认 Segment 的个数是 **16 个**。 
Java8 中的 ConcurrnetHashMap 使用的 **Synchronized 锁加 CAS **的机制。结构也由Java7 中的**Segment 数组 + HashEntry 数组 + 链表 **进化成了 **Node 数组 + 链表 / 红黑树**，Node 是类似于一个 HashEntry 的结构。它的冲突在达到一定大小时会转化成红黑树，在冲突小于一定数量时又会退回链表。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/wokovmo4oc1h0qf2>