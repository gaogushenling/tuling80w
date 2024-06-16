# 什么是Docker Swarm？请简述其作用和使用场景

**Docker Swarm是Docker公司推出的用于管理Docker集群的工具**，可以将多个Docker节点组织成一个单一的虚拟主机，实现对Docker资源的统一管理和调度。
Docker Swarm的作用主要有以下几点：

1. 集群管理：Docker Swarm可以将多个Docker节点组织起来，形成一个统一的虚拟主机，用户可以通过一个入口统一管理这些节点上的Docker资源。
2. 服务编排：Docker Swarm提供了一套丰富的API，可以通过定义声明式配置文件，自动完成复杂的服务部署、扩缩容和升级等操作。
3. 跨主机网络：Docker Swarm内置了对Docker网络插件的支持，用户可以很方便地部署跨主机的容器集群服务。
4. 负载均衡：Docker Swarm可以自动实现负载均衡，根据容器的负载情况自动调整实例数量。

使用Docker Swarm的场景包括但不限于以下情况：

1. 需要快速扩展容器规模，以满足业务需求。
2. 需要高可用性，要求容器服务不中断。
3. 需要跨多个主机运行容器，以实现负载均衡和容灾。
4. 需要自动化部署和管理容器服务，以提高效率。



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/bens87u0rux44l4t>