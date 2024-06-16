# BeanFactory 和FactoryBean有什么区别？

- `**BeanFactory**`是Spring框架的核心接口之一，用于管理和获取Bean对象亦陈为bean的容器。使用了简单工厂模式，提供getBean方法用来获取bean。 
- `**FactoryBean**`是一个bean，但是它是一个特殊的bean。

它是一个接口，**他必须被一个bean**去实现。
FactoryBean接口定义了两个方法：`getObject()`和`getObjectType()`。
getObjectType()方法用于返回创建的Bean对象的类型。
getObject()方法用于返回创建的Bean对象，最终该Bean对象会进行注入，MyBatis集成Spring时的那个SqlSessionFactoryBean就实现了FactoryBean， 最终通过`getObject()`将SqlSessionFactory注入到Ioc容器中。
所以FactoryBean不是一个普通的Bean，它会表现出工厂模式的样子,可以自定义创建Bean对象的逻辑，可以在创建Bean对象之前进行一些额外的处理。
如果要获得FactoryBean类本身而非getObject()返回的Bean可以通过在BeanName前加“&”进行获取。

        所以他们直接没有什么关系， 实在要扯上点关系那就是BeanFactory管理了FactoryBean，



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/hhw8tg1drwp3yczn>