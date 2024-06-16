# 请简述Docker和LXC的区别

Docker和LXC在以下四个方面存在差异：

1. 镜像管理：Docker将应用的所有配置打包到一个容器中，具有可移植性。LXC仅仅实现了进程沙盒化，并不能在不同机器上进行移植。
2. 范围和规模：Docker不仅可以运行在Linux环境，还可以运行在Windows和macOS等其他操作系统上，适用范围广泛。而LXC仅能在Linux环境下运行。
3. 流行程度：Docker由于其简洁的API、用户友好的界面和文档以及社区的积极采用，所以在开发人员和管理员中更受欢迎。相比之下，LXC在开发人员和管理员中并不那么流行。
4. 工具支持：Docker拥有大量的工具和库，可以轻松地与其他容器技术集成，而LXC在这方面相对较弱。

总结来说，Docker和LXC在镜像管理、使用范围、流行程度和工具支持方面存在差异。Docker更适用于大规模的容器管理，而LXC更适合于对性能要求极高的场景。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/fgoq0axgqgnhp77o>