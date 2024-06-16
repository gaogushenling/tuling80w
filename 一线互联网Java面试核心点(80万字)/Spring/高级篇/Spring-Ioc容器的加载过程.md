# Spring-Ioc容器的加载过程

Spring 的 IOC 容器工作的过程，其实可以划分为两个阶段：**配置解析阶段**和**Bean 的创建段**。
其中

- **配置解析阶段**主要做的工作是加载和解析配置文件，将配置的bean解析成 BeanDefinition。
   - 整个过程是： 
1. 读取配置：通过BeanDefinitionReader读取配置文件或配置类
2. 解析配置信息：如ComonentScan、Bean配置等
3. 扫描类注解：根据ComonentScan扫描@Component、@Bean、@Configuration、@Import等注解... 
4. 将符合的bean注册为BeanDefinition
- **Bean的创建过程主要做的工作是根据 BeanDefinition创建Bean。**
   - 大概过程：
1. 实例化Bean：容器根据配置文件中的Bean定义，实例化Bean对象。可以通过构造函数实例化、工厂方法实例化、静态工厂方法实例化等方式来创建Bean对象。
2. 注入Bean属性：容器会为实例化的Bean对象设置属性值，可以通过setter方法注入属性值，也可以通过构造函数注入属性值。
3. 处理依赖关系：容器会处理Bean之间的依赖关系，将依赖的Bean注入到需要的地方 。
4. 执行初始化方法：容器会调用Bean的初始化方法，可以通过实现InitializingBean接口或在配置文件中指定初始化方法来定义Bean的初始化逻辑。
5. 注册Bean：容器会将实例化、属性设置和初始化完成的Bean对象注册到容器中，以便后续的使用和管理。
6. 完成加载：容器完成所有Bean的加载和初始化后，即完成了IoC容器的加载过程。此时，可以通过容器调用getBean获取Bean对象。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/mngu0f2geg1u2e53>