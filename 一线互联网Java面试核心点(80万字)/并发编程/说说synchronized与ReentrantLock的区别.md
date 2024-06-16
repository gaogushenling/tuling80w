# 说说synchronized与ReentrantLock的区别

- **用法不同**：synchronized 可以用于修饰普通方法、静态方法以及代码块，而 ReentrantLock 仅适用于代码块。
- **获取锁和释放锁方式不同：**Synchronized 是隐式锁，可以自动加锁和释放锁，当进入 synchronized 修饰的代码块之后会自动加锁，当离开 synchronized 的代码段之后会自动释放锁。ReentrantLock 是显式锁，需要手动加锁和释放锁， 在使用之前需要先创建 ReentrantLock 对象，然后使用 lock 方法进行加锁，使用完之后再调用 unlock 方法释放锁。
- **锁类型：**默认情况下，synchronized 是非公平锁，而 ReentrantLock 也是非公平锁，但可以手动将 ReentrantLock 配置为公平锁，允许线程按照它们请求锁的顺序获取锁。
- **中断响应**： synchronized 无法直接响应中断，可能导致线程在锁上无限期地等待。ReentrantLock 具有响应中断的能力，可以在等待锁的过程中响应线程的中断请求，从而避免潜在的死锁情况。
- **底层实现**：synchronized 是一个关键字，是在JVM层面通过监视器实现的，而 ReentrantLock 是基于AQS实现的。




> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/siagvwuiuod0c9w1>