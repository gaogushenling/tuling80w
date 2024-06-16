# 反射中，Class.forName和ClassLoader的区别

Class.forName和ClassLoader是Java反射中用于加载类的两种不同方式。
**Class.forName是一个静态方法**，通过提供类的完全限定名，在运行时加载类。此方法还会执行类的静态初始化块。如果类名不存在或无法访问，将抛出ClassNotFoundException异常。
**ClassLoader是一个抽象类，用于加载类的工具**。每个Java类都有关联的ClassLoader对象，负责将类文件加载到Java虚拟机中。ClassLoader可以动态加载类，从不同来源加载类文件，如本地文件系统、网络等。
两者区别如下：

- Class.forName方法由java.lang.Class类调用，负责根据类名加载类，并执行静态初始化。
- ClassLoader是抽象类，提供了更灵活的类加载机制，可以自定义类加载过程，从不同来源加载类文件。

一般情况下，推荐使用**ClassLoader**来加载和使用类，因为它更灵活，并避免执行静态初始化的副作用。**Class.forName**主要用于特定场景，如加载数据库驱动程序。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/hyzhgg3366rb7q1h>