# Spring Bean 容器的生命周期是什么样的

在Spring中，Bean容器的生命周期经历以下阶段：

1. 实例化：当Bean容器加载配置文件时，将会创建Bean的实例。Spring容器会根据配置文件中的定义，通过反射机制创建Java对象，并存储在容器中。
2. 属性设置：在Bean实例化后，Spring容器会通过setter或直接字段注入的方式，将配置文件中的属性值注入到Bean实例中。
3. 初始化：在属性设置完成后，Spring容器会调用Bean的初始化方法，可以通过实现InitializingBean接口或在配置文件中指定init-method来定义初始化方法。在这个阶段，可以进行一些额外的初始化操作。
4. 使用：初始化完成后，Bean实例可以被容器使用。可以通过容器获取Bean的引用，并在应用中使用。
5. 销毁：当应用关闭或者手动从容器中移除Bean时，Spring容器会调用Bean的销毁方法进行一些资源释放等清理工作。可以通过实现DisposableBean接口或在配置文件中指定destroy-method来定义销毁方法。

需要注意的是，Spring容器对于单例的Bean是默认进行管理的，而对于原型（Prototype）作用域的Bean，容器只负责创建和属性设置，不负责销毁。
总结：Spring Bean容器的生命周期包括实例化、属性设置、初始化、使用和销毁等阶段。通过实现相应的接口或在配置文件中指定方法，可以对Bean的生命周期进行管理和定制。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ohzsk6cmoapblpg3>