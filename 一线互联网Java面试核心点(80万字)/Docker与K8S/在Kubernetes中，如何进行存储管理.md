# 在Kubernetes中，如何进行存储管理

在Kubernetes中，**存储管理是通过Volume和Persistent Volume（PV）进行的**。Volume是提供持久化存储的抽象概念，映射到Pod内的容器。Kubernetes提供了多种Volume类型，如emptyDir、hostPath、NFS和Ceph等。另一种抽象概念是**Persistent Volume Claim（PVC），用于向Pod提供持久化存储资源**。用户可以创建一个PVC，指定所需的Volume类型和大小，然后Kubernetes会自动创建相应的PV并将其绑定到PVC。这样，Pod可以使用PVC来获取持久化存储资源。总之，Kubernetes通过Volume和PV提供了一种灵活的存储管理机制，可以满足不同应用程序的存储需求，提高了应用程序的可移植性和可复用性。



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/tns9fz0trvise04a>