# SpringBoot为什么要禁止循环依赖

循环依赖大家都知道，也被折磨过，在 SpringBoot**2.6.0**的版本默认禁止了循环依赖，如果程序中出现循环依赖就会报错。
当然并没有一锤子打死，也提供了开启允许循环依赖的配置，只需要在配置文件中开启即可：
```
spring:
  main:
    allow-circular-references: true
```
那SpringBoot为什么要要禁止呢？我们都知道Spring解决循环依赖的方式是通过三级缓存，光学这个三级缓存我们就煞费苦心，其实说白了他是一种给程序员擦屁股的行为.
 其实对象之间的关系如果是互相依赖是一种不合理的设计，避免你做出这种不合理的依赖，SpringBoot进而禁止循环依赖。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/fab361bxoeyy7vvg>