# CHAR 和 VARCHAR 的区别？

CHAR和VARCHAR的区别可以总结如下：

1. **存储方式：**CHAR是固定长度的字符类型，而VARCHAR是可变长度的字符类型。
2. **占用空间：**CHAR会以固定的长度存储数据，不论实际存储的字符数目，而VARCHAR则根据实际需要的空间动态分配存储。
3. **尾随空格：**CHAR在存储时会用空格填充到指定长度，并在检索时需要删除尾随空格，而VARCHAR没有这个问题。
4. **长度限制：**CHAR的长度范围为1到255个字符，而VARCHAR的长度范围也是255个字符，但可以根据需求设定更长的长度。
5. **访问效率：**由于CHAR是固定长度的，它在某些情况下可能会比VARCHAR稍微快一些。

综上所述，CHAR适合存储长度固定且固定大小的数据，而VARCHAR适用于长度可变的数据。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/sifgcq659b34bzpz>