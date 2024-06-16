# 常用的JVM启动参数有哪些

JVM（Java虚拟机）的启动参数用于配置和调整Java应用程序的运行时行为。以下是一些常用的JVM启动参数：

1. **-Xmx**：指定Java堆内存的最大限制。例如，**-Xmx512m** 表示最大堆内存为512兆字节。
2. **-Xms**：指定Java堆内存的初始大小。例如，**-Xms256m** 表示初始堆内存为256兆字节。
3. **-Xss**：指定每个线程的堆栈大小。例如，**-Xss256k** 表示每个线程的堆栈大小为256千字节。
4. **-XX:MaxPermSize**（对于Java 7及之前的版本）或 **-XX:MaxMetaspaceSize**（对于Java 8及以后的版本）：指定永久代（Java 7及之前）或元空间（Java 8及以后）的最大大小。
5. **-XX:PermSize**（对于Java 7及之前的版本）或 **-XX:MetaspaceSize**（对于Java 8及以后的版本）：指定永久代（Java 7及之前）或元空间（Java 8及以后）的初始大小。
6. **-Xmn**：指定年轻代的大小。例如，**-Xmn256m** 表示年轻代大小为256兆字节。
7. **-XX:SurvivorRatio**：指定年轻代中Eden区与Survivor区的大小比例。例如，**-XX:SurvivorRatio=8** 表示Eden区与每个Survivor区的大小比例为8:1。
8. **-XX:NewRatio**：指定年轻代与老年代的大小比例。例如，**-XX:NewRatio=2** 表示年轻代和老年代的比例为1:2。
9. **-XX:MaxGCPauseMillis**：设置垃圾回收的最大暂停时间目标。例如，**-XX:MaxGCPauseMillis=100** 表示垃圾回收的最大暂停时间目标为100毫秒。
10. **-XX:ParallelGCThreads**：指定并行垃圾回收线程的数量。例如，**-XX:ParallelGCThreads=4** 表示使用4个线程进行并行垃圾回收。
11. **-XX:+UseConcMarkSweepGC**：启用并发标记清除垃圾回收器。
12. **-XX:+UseG1GC**：启用G1（Garbage First）垃圾回收器。
13. **-Dproperty=value**：设置Java系统属性，可以在应用程序中使用 **System.getProperty("property")** 来获取这些属性的值。

这些是一些常见的JVM启动参数，可以根据应用程序的需求和性能调优的目标进行调整。JVM启动参数的使用可以显著影响应用程序的性能和行为，因此在设置这些参数时需要谨慎。同时，JVM支持的启动参数因不同的JVM版本和供应商而有所不同，建议查阅相关文档以获取更详细的信息。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/rwvqepaazk74extg>