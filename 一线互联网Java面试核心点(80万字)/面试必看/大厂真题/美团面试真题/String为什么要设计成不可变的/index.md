# String 为什么要设计成不可变的

String被设计成不可变的有以下几个原因：

1. 线程安全：由于String是不可变的，多个线程可以同时访问同一个String对象而无需担心数据被修改。这使得String在多线程环境下是线程安全的。
2. 缓存Hash值：由于String是不可变的，它的hashCode可以缓存，将String用作Key在哈希表中查找时，由于hashCode不变，可以加快查找速度。
3. 安全性：String在很多安全框架和API中广泛使用，如密码学中的加密操作。如果String是可变的，攻击者可以修改String中的值，对应用程序的安全性造成潜在的风险。
4. Hash值不变性：当拥有对String对象的引用时，无法更改String对象的内容，这意味着String对象可以被安全地用作哈希表中的Key，而保持哈希值的不变性。
5. 效率：由于String是不可变的，可以在多个地方共享相同的String对象，避免了重复创建字符串对象的开销，提高了Java程序的性能和效率。

尽管String是不可变的，但在实际使用中如果需要频繁地进行字符串拼接等操作，可以使用StringBuilder或StringBuffer类来提高效率，因为它们可以修改字符串内容。但在多线程环境下，应优先考虑使用StringBuffer而非StringBuilder，因为StringBuffer是线程安全的。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ei6txm9nlv9ldlgm>