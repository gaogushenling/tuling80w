# Spring 框架中都用到了哪些设计模式？

1. **简单工厂：**
   - **BeanFactory**：Spring的**BeanFactory**充当工厂，负责根据配置信息创建Bean实例。它是一种工厂模式的应用，根据指定的类名或ID创建Bean对象。
2. **工厂方法：**
   - **FactoryBean**：**FactoryBean**接口允许用户自定义Bean的创建逻辑，实现了工厂方法模式。开发人员可以使用**FactoryBean**来创建复杂的Bean实例。
3. **单例模式：**
   - **Bean实例**：Spring默认将Bean配置为单例，确保在容器中只有一个共享的实例，这有助于节省资源和提高性能。
4. **适配器模式：**
   - **SpringMVC中的HandlerAdapter**：SpringMVC的**HandlerAdapter**允许不同类型的处理器适配到处理器接口，以实现统一的处理器调用。这是适配器模式的应用。
5. **装饰器模式：**
   - **BeanWrapper**：Spring的**BeanWrapper**允许在不修改原始Bean类的情况下添加额外的功能，这是装饰器模式的实际应用。
6. **代理模式：**
   - **AOP底层**：Spring的AOP（面向切面编程）底层通过代理模式来实现切面功能，包括JDK动态代理和CGLIB代理。
7. **观察者模式：**
   - **Spring的事件监听**：Spring的事件监听机制是观察者模式的应用，它允许组件监听和响应特定类型的事件，实现了松耦合的组件通信。
8. **策略模式：**
   - **excludeFilters、includeFilters**：Spring允许使用策略模式来定义包扫描时的过滤策略，如在**@ComponentScan**注解中使用的**excludeFilters**和**includeFilters**。
9. **模板方法模式：**
   - **Spring几乎所有的外接扩展**：Spring框架的许多模块和外部扩展都采用模板方法模式，例如JdbcTemplate、HibernateTemplate等。
10. **责任链模式：**
   - **AOP的方法调用**：Spring AOP通过责任链模式实现通知（Advice）的调用，确保通知按顺序执行。

Spring框架的设计哲学是通过这些设计模式来提供强大的功能和可定制性。它的模块化、松耦合的设计使得开发人员能够更轻松地构建可维护、可扩展和灵活的应用程序。这些设计模式的应用有助于实现代码重用、降低开发成本，是Spring框架广受欢迎的原因之一。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/yc279v327deg3wvi>