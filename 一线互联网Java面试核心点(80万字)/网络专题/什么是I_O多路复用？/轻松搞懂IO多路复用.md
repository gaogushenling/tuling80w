# 轻松搞懂IO多路复用


## 什么是 IO 多路复用？
先说结论，IO 多路复用是一种在单个线程中管理多个 IO 操作的技术。它允许一个进程或线程监视多个文件描述符，并且在其中任何一个文件描述符就绪（可读、可写或异常）时执行相应的操作，而无需阻塞其他操作。

---

这样可能不太好理解，我们看看没有 IO 多路复用时，BIO NIO 是怎么处理的。
如果现在有 1W 个文件描述符：

- **BIO 的处理逻辑**
   - 服务端采用单线程，当 accept 一个请求后，在 recv 或 send 调用阻塞时，将无法 accept 其他请求（必须等上一个请求处 recv 或 send 完），无法处理并发。
   - 服务端采用多线程，当 accept 一个请求后，开启线程进行 recv，可以完成并发处理，但随着请求数增加需要增加系统线程，大量的线程占用很大的内存空间，并且线程切换会带来很大的开销，1W 个线程真正发生读写事件的线程数不会超过20%，每次  accept 都开一个线程也是一种资源浪费
- **NIO 的处理逻辑**
   - 服务器端当 accept 一个请求后，加入 fds 集合（文件描述符集合），每次轮询一遍 fds 集合 recv (非阻塞) 数据，没有数据则立即返回错误，每次轮询所有 fd（包括没有发生读写事件的 fd ）会很浪费 cpu 资源
- **IO多路复用处理逻辑**
   - 服务器端采用单线程通过 select/epoll 等系统调用获取 fd 列表，遍历有事件的 fd 进行accept/recv/send，使其能支持更多的并发连接请求。
   - 相比于 BIO、NIO，IO 多路复用最大的区别就是**获取有事件的文件描述符方式发生了转变**，BIO，NIO 都是主动去轮询获取 fd，多路复用是将 **fd 都交给内核去监控**，当某个 fd 能够读写时由内核告知应用程序处理，这样就从**主动轮询变成了清闲的被动**了，通过这种方式现在就可以一次处理多路 IO 了**。**

---

accept 用于建立连接，recv 用于接收客户端发送的数据，send 用于向客户端发送数据

---

刚刚我们提到的 I/O 操作都是针对文件描述符的，那什么是文件描述符呢？

## 什么是文件描述符？
很简单，文件描述符其实就是一个数字而已，又或者可以理解为指针。
提到 I/O 操作就逃不过文件这个概念，在 Linux 中有一个很经典的说法 everything is file，一切皆文件，比如：文件IO、网络IO、管道IO 等等。那我们在进行 I/O 操作的时候，是怎么知道从哪个文件读数据，往哪个文件写数据的呢？这时候就是通过文件描述符来找到确切的文件。**有了文件描述符，进程可以对文件一无所知**，比如文件在磁盘的什么位置、加载到内存中又是怎样管理的等等，这些信息统统交由操作系统打理，进程无需关心，操作系统只需要给进程一个文件描述符就足够了。



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/aeavstmrg00qgmeu>