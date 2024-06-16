# Zookeeper 是如何解决脑裂问题的

Zookeeper的解决方案是通过过半机制来避免脑裂问题的发生。
具体来说，在Zookeeper的领导者选举过程中，如果某台ZookeeperServer获得了超过半数的选票，则此ZookeeperServer就可以成为Leader。举个简单的例子，如果现在集群中有5台ZookeeperServer，那么过半数就是2.5，也就是说，领导者选举的过程中至少要有三台ZookeeperServer投了同一个ZookeeperServer，才会选出来一个Leader。
过半机制中是大于而不是大于等于，目的是为了防止脑裂。因为如果投票结果是大于等于2.5，那么只要有两台机器同时发生故障，就能导致过半数失效，从而引发脑裂问题。而如果是大于2.5，则必须有一台机器故障的同时，另外还有一台机器也故障，才能导致过半数失效，这样就能大大降低脑裂问题的发生概率。
因此，Zookeeper通过过半机制来保证在发生脑裂问题时，集群仍然能够正常工作，避免因为脑裂问题导致集群失效的问题。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/mpmccgit0zct3c8z>