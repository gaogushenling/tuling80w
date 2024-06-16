# JAVA 中怎样唤醒一个阻塞的线程

在Java中，可以使用Thread类的interrupt()方法来唤醒一个阻塞的线程。
首先，需要获取到该线程的对象，然后调用interrupt()方法。例如：
```java
java复制代码



Thread thread = new Thread(new Runnable() {  
    @Override  
    public void run() {  
        // 线程执行代码  
    }  
});  
thread.start(); // 启动线程  
  
// 线程阻塞的情况下，调用interrupt()方法  
thread.interrupt();
```
当线程被中断后，会设置线程的中断状态为true。在代码中可以通过Thread.currentThread().isInterrupted()方法来检查线程的中断状态。如果线程检测到自己被中断，那么可以根据中断状态做出相应的处理。
在Java中，被中断的线程需要自己编写代码去响应中断，否则线程仍然会一直阻塞。因此，在实际应用中，需要根据具体的业务逻辑编写相应的中断处理代码。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/tanyoblbtrbxy9gx>