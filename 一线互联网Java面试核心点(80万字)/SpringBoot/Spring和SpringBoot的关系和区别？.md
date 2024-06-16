# Spring和SpringBoot的关系和区别？

他们的关系是：

1. **Spring是框架，Spring Boot是个脚手架：** Spring是一个全功能的Java应用程序框架，旨在帮助开发人员构建各种类型的应用程序，包括Web应用、企业级应用、批处理应用等。Spring提供了大量的组件和功能，但需要开发人员进行详细的配置和集成。Spring Boot则是一个**脚手架**工具，它基于Spring框架，旨在简化Spring应用程序的初始配置和开发过程，提供了自动化配置和约定优于配置的特性。
2. **Spring Boot构建在Spring之上：** Spring Boot不是一个独立的框架，而是建立在Spring框架之上的工具。它使用了Spring的核心功能，如依赖注入、面向切面编程、事务管理等。因此，Spring Boot项目可以充分利用Spring框架的功能，但更容易启动和运行。

**他们的区别是：**

1. **配置方式：** Spring通常需要大量的XML配置或Java注解来定义应用程序的配置。相比之下，Spring Boot采用了"约定优于配置"的原则，大部分配置都可以通过默认值和自动配置来完成，从而减少了配置的复杂性。
2. **开发速度：** Spring Boot旨在提高开发速度，因此它降低了开发人员的学习曲线，并提供了内置的Starter和自动配置，使开发更加快速和高效。Spring需要更多的手动配置和集成工作。
3. **内置Web容器：** Spring Boot内置了多个内嵌式Web容器，如Tomcat、Jetty、Undertow等，可以轻松创建独立的可执行JAR文件或WAR文件，而不需要外部Web服务器。Spring通常需要外部Web服务器的部署。

总的来说，Spring是一个全功能的Java应用程序框架，而Spring Boot是一个用于简化Spring应用程序开发的工具。Spring Boot通过自动化配置、约定优于配置的原则、内置Web容器等功能，使得开发和部署Spring应用程序变得更加快速和便捷，特别适用于微服务和快速原型开发。开发人员可以根据项目的需求选择使用Spring框架、Spring Boot，或两者结合使用。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gw6q0qvx4ofur4tz>