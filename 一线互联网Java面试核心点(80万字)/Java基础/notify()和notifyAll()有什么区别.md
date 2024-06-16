# notify()和 notifyAll()有什么区别

在Java中，notify()和notifyAll()都属于Object类的方法，用于实现线程间的通信。
**notify()方法**用于唤醒在当前对象上等待的单个线程。如果有多个线程同时在某个对象上等待（通过调用该对象的wait()方法），则只会唤醒其中一个线程，并使其从等待状态变为可运行状态。具体是哪个线程被唤醒是不确定的，取决于线程调度器的实现。
**notifyAll()方法**用于唤醒在当前对象上等待的所有线程。如果有多个线程在某个对象上等待，调用notifyAll()方法后，所有等待的线程都会被唤醒并竞争该对象的锁。其中一个线程获得锁后继续执行，其他线程则继续等待。
需要注意的是，notify()和notifyAll()方法只能在同步代码块或同步方法内部调用，并且必须拥有与该对象关联的锁。否则会抛出IllegalMonitorStateException异常。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/wg6cczzk8k7b71ug>