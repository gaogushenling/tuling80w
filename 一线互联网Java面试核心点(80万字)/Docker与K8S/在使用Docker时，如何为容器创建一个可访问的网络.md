# 在使用Docker时，如何为容器创建一个可访问的网络

在使用Docker时，可以通过以下两种方式为容器创建一个可访问的网络：

1. **使用默认的网络**：Docker的默认网络模式是bridge模式，它会自动创建一个网络，并将容器连接到该网络。容器的网络配置可以在创建容器时通过--network参数指定。例如，使用以下命令创建一个使用默认网络的容器：
```bash
docker run --network=bridge -tid -p 8000:8000 image_name
```
这将在bridge网络中创建一个容器，并将容器的8000端口映射到主机的8000端口。

2. **创建自定义网络**：Docker还支持创建自定义的网络，以便容器可以连接到其他容器或外部网络。可以使用docker network create命令创建自定义网络。例如，使用以下命令创建一个名为my_network的自定义网络：
```bash
docker network create my_network
```
然后，在创建容器时使用--network参数指定要使用的网络。例如，使用以下命令创建一个使用my_network网络的容器：
```bash
docker run --network=my_network -tid -p 8000:8000 image_name
```
这将在my_network网络中创建一个容器，并将容器的8000端口映射到主机的8000端口。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/acs8ymfeddy9dpng>