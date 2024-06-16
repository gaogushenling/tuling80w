# 当一个Docker容器运行异常时，如何通过Docker命令查看日志信息

当一个Docker容器运行异常时，你可以使用Docker命令查看容器的日志信息。有三种方法可以实现：

1. 使用docker logs命令。该命令可以查看容器的日志输出。例如，要查看名为"my-container"的容器的日志，可以运行以下命令：
```bash
docker logs my-container
```
默认情况下，docker logs命令将显示容器的全部日志内容。如果你只想查看最新的几行日志，可以使用-tail选项指定行数，如：
```bash
docker logs --tail 10 my-container
```
这会显示最新的10行日志。

2. 进入容器内部查看日志。首先使用docker ps命令找到容器的ID，然后运行以下命令进入容器的命令行界面：
```bash
docker exec -it [容器ID] /bin/bash
```
进入容器后，你可以使用cat或less等命令查看日志文件。日志文件通常位于/var/log/目录下。

3. 使用docker attach命令实时查看容器日志。该命令允许你实时跟踪容器的日志输出。例如，要查看名为"my-container"的容器的日志，可以运行以下命令：
```bash
docker attach my-container
```
这会附加到容器的标准输出和标准错误输出，实时显示容器的日志信息。注意，一旦你使用docker attach进入容器后，将无法再退出容器。如果要退出，可以按下Ctrl + C组合键强制中断容器运行。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/lg3thlrkpf2zi6kx>