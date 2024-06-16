# 讲讲你对CyclicBarrier的理解

CyclicBarrier是Java中的一个多线程协作工具，它可以让多个线程在一个屏障点等待，并在所有线程都到达后一起继续执行。与CountDownLatch不同，CyclicBarrier可以重复使用，并且可以指定屏障点后执行的额外动作。
CyclicBarrier的主要特点有三个。

- **首先，**它可以重复使用，这意味着当所有线程都到达屏障点后，屏障会自动重置，可以用来处理多次需要等待的任务。
- **其次，**CyclicBarrier可以协调多个线程同时开始执行，这在分阶段任务和并发游戏等场景中非常有用。
- **最后，**CyclicBarrier还提供了可选的动作，在所有线程到达屏障点时执行，可以实现额外的逻辑。

需要注意的是，在创建CyclicBarrier时需要指定参与线程的数量。一旦所有参与线程都到达屏障点后，CyclicBarrier解除阻塞，所有线程可以继续执行后续操作。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/rahv0rmraxvh9bn5>