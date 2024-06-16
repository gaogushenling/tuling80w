# 简述Kubernetes的工作流程

Kubernetes的工作流程可以分为以下几个步骤：

1. 创建一个包含应用程序的Deployment的yml文件，然后通过kubectl客户端工具发送给ApiServer。
2. ApiServer接收到客户端的请求并将资源内容存储到数据库(etcd)中。
3. Controller组件(包含scheduler、replication、endpoint)监控资源变化并作出反应。
4. ReplicaSet检查数据库变化，创建期望数量的pod实例。
5. Scheduler再次检查数据库变化，发现尚未被分配到具体执行节点(Node)的Pod，然后根据一组相关规则将Pod分配到可以运行它们的节点(Node)上，并更新数据库，记录Pod分配情况。
6. Kubelet监控数据库变化，管理后续Pod的生命周期，发现被分配到它所在的节点上运行的那些Pod。如果找到新Pod，则会在该节点上运行这个新Pod。例如当有数据发送到主机时，将其路由到正确的pod或容器。

Kubernetes通过以上步骤实现了自动化容器应用的管理和协调，使得容器部署更加简单、可靠和高效。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/aynuopfh38rslxms>