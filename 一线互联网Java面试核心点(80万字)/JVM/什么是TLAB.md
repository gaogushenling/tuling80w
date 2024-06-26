# 什么是TLAB

TLAB是Java虚拟机中的一种优化技术，用于提高对象分配的效率。它是一种线程本地的内存分配缓冲区，每个线程在堆上都有自己独立的TLAB。
在Java中，对象的分配通常是通过在堆上分配内存来完成的。为了提高对象分配的效率，Java虚拟机引入了TLAB机制。TLAB会为每个线程预先分配一块内存空间，线程在分配对象时，会从自己的TLAB中进行分配，而不是直接在堆上进行分配。
TLAB的优点有以下几个：

1. 减少线程同步：由于每个线程都有自己的TLAB，因此不需要进行线程同步操作，可以减少线程竞争和锁的开销。
2. 提高分配速度：由于对象分配是在TLAB中进行的，而不是在堆上进行，因此可以减少对象分配的开销，提高分配速度。
3. 提高局部性：由于每个线程都有自己的TLAB，对象分配在TLAB中进行，可以提高局部性，减少对共享内存的访问，提高缓存命中率。

需要注意的是，TLAB的大小是可以配置的，可以根据实际应用的需求进行调整。过小的TLAB可能会导致频繁的垃圾回收，而过大的TLAB可能会浪费内存空间。
总结来说，TLAB是Java虚拟机中的一种优化技术，用于提高对象分配的效率。每个线程都有自己的TLAB，对象分配在TLAB中进行，可以减少线程同步、提高分配速度和提高局部性。TLAB的大小可以配置，需要根据实际需求进行调整。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/aguvt5qgg40m3s27>