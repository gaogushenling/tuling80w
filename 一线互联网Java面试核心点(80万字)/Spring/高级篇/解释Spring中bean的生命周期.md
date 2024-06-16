# 解释Spring中bean的生命周期

Bean生命周期：指定的就是Bean从创建到销毁的整个过程: 分4大步：

1. 实例化
   1. 通过反射去推断构造函数进行实例化
   2. 实例工厂、 静态工厂
2. 依赖注入（DI）
   1. 解析自动装配（byname bytype constractor none @Autowired）
3. 初始化
   1. 调用很多Aware回调方法
   2. 调用BeanPostProcessor.postProcessBeforeInitialization
   3. 调用生命周期回调初始化方法
   4. 调用BeanPostProcessor.postProcessAfterInitialization, 如果bean实现aop则会在这里创建动态代理
4. 销毁
   1. 在spring容器关闭的时候进行调用
   2. 调用生命周期回调销毁方法


这4大步组成了Bean的生命周期



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/xp7igarg3iivvs54>