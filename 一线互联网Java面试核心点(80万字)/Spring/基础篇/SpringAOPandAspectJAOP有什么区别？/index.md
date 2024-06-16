# Spring AOP and AspectJ AOP 有什么区别？

**首先说下他们之间的关系：**

- 当在Spring中要使用@Aspect、@Before.等这些注解的时候， 就需要添加AspectJ相关依赖
```xml
<dependency>
  <groupId>org.aspectj</groupId>
  <artifactId>aspectjweaver</artifactId>
  <version>1.9.5</version>
</dependency>
```

- **Spring Aop主要用到了AspectJ的@PointCut 切点解析能力和切点匹配能力。 @Aspect、@Before.等这些注解都是由AspectJ 发明的，  **
-  AspectJ 能干很多 Spring AOP 干不了的事情，它是 **AOP 编程的完全解决方案**。Spring AOP 致力于解决的是企业级开发中最普遍的 AOP 需求（方法增强），而不是力求成为一个像 AspectJ 一样的 AOP 编程完全解决方案。

**区别：**
（1）AspectJ 主要通过在编译阶段生成代理类，也称为编译时增强，他会在编译阶段将AspectJ(切面)织入到Java字节码中，运行的时候就是增强之后的对象，通过这种方式实现AOP。
SpringAOP并没有使用AspectJ的织入Java字节功能来增强对象。而是使用的**动态代理**来增强对象。默认地，**如果使用接口的，用 JDK 提供的动态代理实现**，如果**没有接口，使用 CGLIB 实现**。**Spring AOP** 在容器启动的时候需要生成代理实例，在方法调用上也会增加栈的深度，使得 Spring AOP 的性能不如 AspectJ 那么好。 


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/pbf0dhm0spucdw85>