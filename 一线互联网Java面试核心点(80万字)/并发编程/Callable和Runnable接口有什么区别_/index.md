# Callable和Runnable接口有什么区别?

Callable和Runnable接口都是用于在Java中实现多线程的接口，但它们之间有一些区别：

1. 返回值：
   - Runnable接口的run()方法没有返回值，它通常用于执行一些不需要返回结果的任务。
   - Callable接口的call()方法可以返回一个结果，它允许线程执行任务并返回结果，可以通过Future对象获取。
2. 抛出异常：
   - Runnable接口的run()方法不能抛出受检异常，只能抛出未检查异常。
   - Callable接口的call()方法可以抛出受检异常。
3. 泛型：
   - Callable接口使用了泛型，可以指定call()方法的返回类型。
   - Runnable接口没有使用泛型。
4. 线程池支持：
   - Callable接口通常与Executor框架一起使用，可以提交给ExecutorService的线程池执行。
   - Runnable接口同样可以与Executor框架一起使用，但是Callable接口提供了更丰富的功能，如取消任务、获取执行结果等。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/gsli5vyplgdsgh33>