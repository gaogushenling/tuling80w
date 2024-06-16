# 为什么SpringBoot的jar可以直接运行？

Spring Boot的可执行JAR文件之所以可以直接运行，原因如下：

1. **第一个关键点：** Spring Boot提供了一个Maven插件（spring-boot-maven-plugin），用于将应用程序打包成可执行的JAR文件。通过执行**mvn clean package**等命令，可以轻松生成可执行JAR。
2. **第二个关键点：** 打包生成的JAR文件通常是"Fat JAR"或"Uber JAR"，这意味着它包含了应用程序的所有依赖项，包括第三方库和Spring Boot框架本身。这样，JAR文件就成了一个自包含的单一文件。
3. **第三个关键点：** JAR文件包含一个名为**MANIFEST.MF**的清单文件，其中包含了关于JAR文件的元数据信息。其中，主要的信息是**Main-Class**，它指定了启动应用程序的主类。
4. **第四个关键点：** Spring Boot的可执行JAR文件通常由**JarLauncher**类启动。**JarLauncher**负责创建一个类加载器（**LaunchedURLClassLoader**），加载**boot-lib**目录下的JAR文件，包括Spring Boot loader相关的类。然后，它在一个新线程中启动应用程序的Main方法，实现应用程序的启动。、
5. 第五**个关键点：**当执行Main方法最终会加载Spring容器、进而创建内嵌Tomcat进行阻塞线程使我们jar包完成web应用的启动

 


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/xu6s6dz8wgfl6ex4>