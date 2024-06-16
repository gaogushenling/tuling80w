# 在Kubernetes中，如何实现滚动升级和回滚

在Kubernetes中，滚动升级和回滚可以通过以下步骤实现：
滚动升级：

1. 创建一个新的Replica Set（RS），它包含新的Pod模板，该模板定义了新的Pod配置。
2. 通过增加Replica Set的副本数量，逐渐将流量从旧的Pod转移到新的Pod上。
3. 当所有流量都转移到新的Pod上后，可以删除旧的Pod。

回滚：

1. 创建一个新的Replica Set（RS），它包含旧的Pod模板，该模板定义了旧的Pod配置。
2. 通过减少Replica Set的副本数量，逐渐将流量从新的Pod转移到旧的Pod上。
3. 当所有流量都转移到旧的Pod上后，可以删除新的Pod。

在这些过程中，Kubernetes会根据Pod的状态和所需的副本数量进行自动调度和平衡。通过这种方式，滚动升级和回滚可以在不影响应用程序服务的情况下进行。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/cgcwk65bnovnkxfy>