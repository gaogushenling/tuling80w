# final，finally，finalize的区别

在Java中，final、finally和finalize是三个不同的关键字，它们具有不同的作用和用法。

1. **final：**
   - final是一个修饰符，可以用于修饰类、方法和变量。
      - 用于修饰类时，表示该类不能被继承，即为最终类。
      - 用于修饰方法时，表示该方法不能被子类重写。
      - 用于修饰变量时，表示该变量是一个常量，其值不能被修改。
2. **finally：**
   - finally是一个关键字，用于定义一个代码块，通常与try-catch结构一起使用。
   - finally块中的代码无论是否抛出异常，都会被执行。
   - finally块通常用于释放资源、关闭连接或执行必要的清理操作。
3. **finalize：**
   - finalize是Object类中的一个方法，被用于垃圾回收机制。
   - finalize方法在对象被垃圾回收之前被调用，用于进行资源释放或其他清理操作。
   - 通常情况下，我们不需要显式地调用finalize方法，而是交由垃圾回收器自动调用。

总结：

- final是修饰符，用于限定类、方法和变量的性质。
- finally是一个关键字，用于定义一个代码块，在异常处理中用于确保特定代码无论如何都会被执行。
- finalize是一个Object类中的方法，用于对象的垃圾回收前的清理操作。

请注意，finalize方法已被废弃，不推荐使用。在现代Java中，可以使用try-with-resources语句或手动释放资源的方式来替代finalize方法的功能。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/cuwys8d1r3gki8dv>