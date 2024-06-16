# Nacos、Eureka、Zookeeper注册中心的区别

Nacos、Eureka和Zookeeper都是常用的注册中心，它们在功能和实现方式上存在一些不同。

- Nacos除了作为注册中心外，还提供了配置管理、服务发现和事件通知等功能。Nacos默认情况下采用AP架构保证服务可用性，CP架构底层采用Raft协议保证数据的一致性。Nacos适合作为微服务注册中心和配置管理中心，支持快速发现、配置管理和服务治理等功能。
- Eureka是只提供注册中心功能的工具，它的设计理念是AP，即保证服务的可用性，不保证一致性。Eureka的各个节点之间相互注册，只要有一台Eureka节点存在，整个微服务就可以通讯。
- 而Zookeeper相比前两者，除了注册中心的功能，还提供了分布式协调服务，比如通知、公告、配置管理等。Zookeeper采用CP设计，可以保证数据的一致性，但是牺牲了一部分服务的可用性。Zookeeper适用于需要分布式协调服务的场景，如配置管理、命名服务等。







> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/spfvu14fptvuc6un>