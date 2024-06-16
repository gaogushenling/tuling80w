# 简述Kubernetes中的Deployment、StatefulSet、DaemonSet的区别

Kubernetes中的Deployment、StatefulSet和DaemonSet有以下区别：

1. **应用场景**：
   - **Deployment适用于无状态的应用场景**。也就是说，即使一个Pod失败，也不需要从这个Pod中恢复数据。一般来说，开发一个有状态的应用程序需要更多的工作，因此无状态的应用程序更为常见。
   - **StatefulSet适用于有状态的应用场景**，例如需要持久化存储的应用程序，每个实例都需要有明确且不变的唯一标识。
   - **DaemonSet适用于在每个节点都需要运行一个或多个Pod的场景**，例如系统监控、日志采集等任务。
2. **副本控制和调度**：
   - Deployment的副本可以动态增加或减少，调度和回滚等操作也适用于Deployment。
   - StatefulSet在启动和停止Pod时需要按照一定的顺序，不能动态地增加或减少Pod副本。
   - DaemonSet会确保每个节点都有一个Pod运行，且这个Pod不会离开该节点。
3. **存储**：
   - Deployment不需要特别的存储支持。
   - StatefulSet需要为每个Pod提供独立的存储，这可以通过后端存储完成。
   - DaemonSet的每个Pod需要挂载到特定的存储。

总的来说，根据应用场景和需求，可以选择合适的Kubernetes控制器来部署和管理应用程序。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ico570y8ntee40ng>