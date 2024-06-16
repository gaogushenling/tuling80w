# String，Stringbuffer，StringBuilder的区别

三者均是Java中用来处理字符串的类，它们之间的主要区别如下：

1. **可变性：**
   - String是不可变的类，一旦创建就不能被修改。每次对String进行操作时，都会创建一个新的String对象。
   - StringBuffer和StringBuilder是可变的类，可以动态修改字符串内容。
2. **线程安全性：**
   - String是线程安全的，因为它是不可变的。多个线程可以同时访问同一个String对象而无需担心数据的修改问题。
   - StringBuffer是线程安全的，它的方法使用了synchronized关键字进行同步，保证在多线程环境下的安全性。
   - StringBuilder是非线程安全的，不使用synchronized关键字，所以在多线程环境下使用时需要手动进行同步控制。
3. **性能：**
   - 由于String是不可变的，每次对String进行操作都会创建一个新的String对象，频繁的字符串拼接会导致大量的对象创建和内存消耗。
   - StringBuffer是可变的，对字符串的修改是在原有对象上进行，不会创建新的对象，因此在频繁的字符串拼接场景下比String更高效。
   - StringBuilder与StringBuffer类似，但不保证线程安全性，因此在单线程环境下性能更高。

综上，如果在单线程环境下进行字符串操作，且不需要频繁修改字符串，推荐使用String；如果在多线程环境下进行字符串操作，或者需要频繁修改字符串，优先考虑使用StringBuffer；如果在单线程环境下进行频繁的字符串拼接和修改，推荐使用StringBuilder以获取更好的性能。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/maogc2ulwzntgc6q>