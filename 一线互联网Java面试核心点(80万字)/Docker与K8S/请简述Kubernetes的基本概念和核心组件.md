# 请简述Kubernetes的基本概念和核心组件

Kubernetes（也称为k8s）是一个开源的容器编排系统，用于自动化应用程序容器的部署、扩展和管理。
Kubernetes的基本概念包括：

1. **节点（Node）**：节点是运行应用程序容器的计算实例。每个节点都运行Kubelet和Docker引擎，并由Master节点进行管理和协调。
2. **Master**：Master是Kubernetes的控制节点，负责管理整个集群，并协调节点的工作。它由三个组件组成：API Server（负责API服务）、Controller Manager（负责容器编排）和Scheduler（负责容器调度）。
3. **Pod**：Pod是Kubernetes的基本单位，包含一个或多个相关的容器。这些容器在同一个Node上运行，共享相同的网络命名空间、IP地址和端口。
4. **Service**：Service是一个抽象层，定义了Pod的逻辑集合，并提供了访问它们的策略（如IP地址和端口）。

Kubernetes的核心组件包括：

1. **APIServer**：负责API服务，处理所有集群级别的资源创建、调度和扩展等请求。
2. **Controller Manager**：负责管理集群的状态。例如，如果某个Node失效，Controller Manager会发现这个事实，并指导Kubelet重新启动在那上面运行的Pod。
3. **Scheduler**：负责在集群中找到适当的节点来运行Pod。它考虑了各种因素，如节点的处理能力、内存、磁盘容量等。
4. **Kubelet**：是Master节点在每个Node上的“眼线”。它定期向API Server汇报Node的状态，并接受Master的指令以采取适当的行动。

这些组件共同协作，使得Kubernetes能够以自动化的方式管理、调度和运行容器化应用程序。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/bn9wi3r3m9dpfeou>