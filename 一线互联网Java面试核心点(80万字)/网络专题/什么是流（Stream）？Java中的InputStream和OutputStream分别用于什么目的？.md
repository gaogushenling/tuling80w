# 什么是流（Stream）？Java中的InputStream和OutputStream分别用于什么目的？

在Java中，有两种主要类型的流：输入流（InputStream）和输出流（OutputStream）。

-  **InputStream（输入流）**：这就像是一个数据的“水龙头”，它允许你从数据源（比如文件、网络连接等）读取数据。你可以把它想象成把数据从源头流进来的管道。比如，你可以用InputStream来读取文件中的内容，或者从网络连接中接收数据。 
-  **OutputStream（输出流）**：这就像是一个数据的“水龙头”，它允许你把数据写入到目的地（比如文件、网络连接等）。你可以把它想象成把数据从管道流出去的工具。比如，你可以用OutputStream来把数据写入文件，或者发送数据到网络连接。 

总之，InputStream用于读取数据，而OutputStream用于写入数据。它们就像是连接你的程序与外部数据源或目的地的管道，让你可以方便地进行数据传输和处理。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/spb2raphmgdxbqd4>