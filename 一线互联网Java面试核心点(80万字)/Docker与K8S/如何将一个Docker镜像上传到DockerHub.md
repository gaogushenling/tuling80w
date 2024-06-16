# 如何将一个Docker镜像上传到Docker Hub

要将一个Docker镜像上传到Docker Hub，可以按照以下步骤进行操作：

1. 在Docker Hub中创建一个新的存储库。点击右上角"Create Repository"按钮，给存储库取一个名字，并选择是公有存储库还是私有存储库。
2. 在本地构建Docker镜像。进入包含Dockerfile的目录，使用以下命令构建镜像：
```bash

docker image build -t [username]/[repository]:[tag] .
```
这里的[username]是您的Docker Hub用户名，[repository]是您在Docker Hub上创建的存储库名称，[tag]是镜像的标签。例如：
```bash

docker image build -t fox666/tulingmall-product:0.0.1 .
```

3. 登录Docker Hub。在本地使用以下命令登录：
```bash


docker login
```
输入您的Docker Hub用户名和密码进行登录。

4. 将本地构建的Docker镜像推送到Docker Hub。使用以下命令：
```bash

docker push [username]/[repository]:[tag]
```
这里的[username]是您的Docker Hub用户名，[repository]是您在Docker Hub上创建的存储库名称，[tag]是镜像的标签。例如：
```bash

docker push fox666/tulingmall-product:0.0.1
```
上传过程中，Docker将会逐层上传镜像的每个层，并计算每个层的SHA256哈希值。在上传完成后，可以在Docker Hub上看到已上传的镜像。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/aikcw5e9saiqvo1y>