# 如何使用 ShardingSphere 进行数据加密？

ShardingSphere 的数据加密功能配置主要分为以下步骤：

1. 数据源配置：首先需要配置数据源信息，包括数据源的名称、连接池等信息。
2. 加密算法配置：在 ShardingSphere 中内置了一些常见的加密算法，例如 AES、MD5、RC4、SM3 和 SM4，用户可以选择其中一种或多种算法进行加解密操作。同时，用户也可以通过实现 ShardingSphere 提供的接口来自定义加密算法。
3. 加密表配置：该步骤主要用于配置数据表里哪个列为密文数据（cipherColumn）、使用什么算法进行加解密（encryptorName）、哪个列为辅助查询数据（assistedQueryColumn）、使用什么算法进行加解密（assistedQueryEncryptorName）、哪个列为明文数据（plainColumn）以及使用哪个列进行 SQL 编写（logicColumn）。

通过以上步骤，用户可以完成 ShardingSphere 数据加密功能的配置。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/is3fvga1r1saydzk>