# Springboot的自动配置原理？

1. **引入@EnableAutoConfiguration：** 在Spring Boot应用程序的主配置类（通常是带有@SpringBootApplication注解的类）中，通常会引入@EnableAutoConfiguration注解，该注解负责启动自动配置功能。
2. **@EnableAutoConfiguration引入了@Import：** @EnableAutoConfiguration注解实际上是通过@Import注解引入的。这意味着它会导入其他配置类，这些配置类包含了Spring Boot自动配置的逻辑。
3. **解析@Import注解：** 当Spring容器启动时，会解析@Import注解，并加载相应的配置。
4. **deferredImportSelector：** 通过@Import导入的配置类中可能包含了一个deferredImportSelector，它的作用是确保Spring Boot的自动配置类在最后加载，以便方便扩展和覆盖。
5. **读取META-INF/spring.factories文件：** Spring Boot通过SPI（Service Provider Interface）机制，读取类路径下的META-INF/spring.factories文件，该文件包含了各种自动配置类的配置。
6. **过滤出AutoConfigurationClass：** 从spring.factories文件中，Spring Boot会过滤出所有AutoConfigurationClass类型的类，这些类包含了自动配置的具体实现。
7. **条件化加载：** 最后，Spring Boot会根据条件（@ConditionalXXX注解）来排除或包含特定的自动配置类。这些条件会根据应用程序的环境和配置动态生效。

总结起来，Spring Boot的自动配置原理是通过@EnableAutoConfiguration注解引入自动配置逻辑，然后解析@Import注解，加载各种配置类，包括deferredImportSelector和自动配置类。通过SPI机制读取spring.factories文件，过滤出自动配置类，并根据条件化配置来动态加载这些类，从而实现自动配置的功能。这种机制使得Spring Boot应用程序可以根据环境和需求自动配置，极大地简化了开发和部署的工作。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/kd461pbgggzbd0xc>