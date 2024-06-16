# ZooKeeper 集群中服务器之间是怎样通信的


ZooKeeper集群中的服务器之间使用TCP协议进行通信，这个通信过程包括以下关键部分：

1. Leader和Follower：在ZooKeeper集群中，有一个服务器被选为领导者（Leader），其余服务器成为跟随者（Follower）。Leader负责处理所有客户端请求，而Followers主要用于接收Leader的数据更新。
2. 通信机制：每个服务器创建TCP连接，使用LearnerHandler实体来处理与其他服务器的网络通信。LearnerHandler的主要职责是接收来自其他服务器的数据更新，并将其传递给应用程序。
3. 客户端请求：客户端通过ZooKeeper客户端库连接到集群中的任一服务器，并向其中一个服务器发送请求。该服务器会将请求传递给Leader或直接处理请求。
4. 数据同步：Leader负责处理客户端请求，并将数据更新广播给所有Followers。Followers会应用这些更新以保持数据一致性。
5. 故障处理：如果Leader服务器发生故障，ZooKeeper使用选举机制来选举新的Leader，以确保集群的高可用性。

总之，ZooKeeper的通信原理是基于客户端/服务器模型的，客户端发送请求，服务器接收和处理请求，然后返回响应。这个通信过程确保了ZooKeeper集群中数据的一致性和高可用性。



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ulffm5acpxkut4bi>