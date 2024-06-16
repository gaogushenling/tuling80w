# JDK22新特性-非长期支持版本

 没想到 21 还没升上去，Java 22版本正式发布了！这次更新包括了12项功能增强，其中有7项预览功能和1项孵化器功能。这些更新涉及Java语言、API、性能以及JDK中包含的工具的改进。
让我们一起来了解一下这个版本都新增了哪些新特性吧！

## JEP 423 - G1 的区域固定
通过在 G1 中实现区域固定来减少延迟，以便在 Java 本机接口 (JNI) 关键区域期间无需禁用垃圾收集。
**目标**
使用 JNI 时，Java 线程无需在 G1 GC 操作完成之前等待，从而提高开发人员的工作效率。
通过固定特定区域中的关键对象，可以确保在关键区域期间不会移动这些对象，而无需禁用垃圾收集。这一改进可以帮助**避免由于GC操作而导致的线程等待和延迟**，从而**提高应用程序的性能和稳定性**。

## JEP 454 - 外部函数和内存 API
引入一个API，Java程序可以通过该API与Java运行时以外的代码和数据进行互操作。通过有效地调用外部函数（即JVM外部的代码）并安全地访问外部内存（即JVM未管理的内存），API使Java程序**可以调用本机库并处理本机数据，而不会出现JNI的脆弱性和危险，解决很多 JNI 的很多问题。**
**目标**

- **生产力 ：**用简洁、可读且纯 Java API 取代脆弱的本机方法和 Java 本机接口 (JNI)。
- **性能 ：**提供对外部函数和内存的访问，其开销与JNI和 sun.misc.Unsafe 相当。
- **广泛的平台支持 ：**允许在JVM运行的每个平台上发现和调用本机库。
- **统一性 ：**提供在多种内存（例如本机内存，持久内存和托管堆内存）中无限大小的结构化和非结构化数据上进行操作的方法。
- **健全性 ：**确保没有使用后的错误，即使跨多个线程分配和取消分配内存。
- **诚信 ：**允许程序使用本机代码和数据执行不安全的操作，但默认情况下会警告用户此类操作。

## JEP 456 - 未命名变量和模式
**当需要但未使用变量声明**或**嵌套模式**时，提高了可读性。两者都由下划线字符表示。
简单来说就是需要使用，但是我们没用上的变量可以用 下划线 替代减少代码的冗长，提高可读性。
```java
...stream.collect(Collectors.toMap(String::toUpperCase，
                                   _ -> "NODATA")) 
```
```java
try { ... }
catch (Exception _) { ... }               
catch (Throwable _) { ... }
```
```java
sealed abstract class Ball permits RedBall， BlueBall， GreenBall { }
final  class RedBall   extends Ball { }
final  class BlueBall  extends Ball { }
final  class GreenBall extends Ball { }

Ball ball = ...
switch (ball) {
    case RedBall   _   -> process(ball);
    case BlueBall  _  -> process(ball);
    case GreenBall _ -> stopProcessing();
}

Queue<Integer> q = ... // x1， y1， z1， x2， y2， z2， ...
while (q.size() >= 3) {
   var x = q.remove();
   var y = q.remove();
   var _ = q.remove();        
   ... new Point(x， y) ...

   var a = q.remove();
   var _ = q.remove();
   var _ = q.remove(); 
    ... new Point(a， 0) ...
}
```
**目标**

- 捕获开发人员的意图，即未使用给定的绑定或 lambda 参数，并强制执行该属性以澄清程序并减少出错的机会。
- 通过识别必须声明（例如，在 catch 子句中）但未使用的变量，提高所有代码的可维护性。
- 允许多个模式出现在单个 case 标签中，如果它们都没有声明任何模式变量。
- 通过消除不必要的嵌套类型模式来提高记录模式的可读性。

## JEP 458 - 启动多文件源代码程序
允许用户运行作为多个 Java 源代码文件提供的程序，而无需先进行编译。
允许 Java 启动器编译和启动多个源代码文件，这个是对 JEP330 启动单文件源代码程序的改进
```java
// Prog.java
class Prog {
    public static void main(String[] args) { pkg.Helper.run(); }
}

// pkg/Helper.java
package pkg;
class Helper {
    static void run() { System.out.println("Hello!"); }
}
```
**目标**

- 通过使从小程序到大型程序的过渡更加渐进，提高开发人员的工作效率，使开发人员能够选择是否以及何时配置构建工具。
- 请注意，预览功能已完全指定并完全实现了 Java SE 平台的语言或 VM 功能，但它们是暂时的。它们在 JDK 功能版本中提供，以便开发人员根据实际使用情况提供反馈，然后再在未来版本中永久保留。这也为工具供应商提供了在最终确定为 Java SE 标准之前致力于支持功能的机会。
- 孵化器模块中的 API 将非最终 API 和非最终工具交给开发人员和用户，以收集反馈，最终提高 Java 平台的质量。
- 除了 JEP 中描述的更改之外，发行说明中还列出了许多较小的更新，许多应用程序开发人员和系统管理员都会对此感兴趣。其中包括弃用过时的 API 和删除以前弃用的 API。

## JEP 447 - sueper(...) 之前的语句（预览）
在构造函数中，允许不引用正在创建的实例的语句出现在显式构造函数调用之前。
```java
public class PositiveBigInteger extends BigInteger {
    
    public PositiveBigInteger(long value) {  
        if (value <= 0)
            throw new IllegalArgumentException("non-positive value");
        super(value);     
    }

}
```
**目标**

- 给开发人员更大的自由度来表达构造函数的行为，从而使当前必须纳入辅助静态方法，辅助中间构造函数或构造函数参数的逻辑更加自然地放置。
- 保留现有的保证，即构造函数在类实例化期间以自上而下的顺序运行，从而确保子类构造函数中的代码不会干扰超类实例化。
- 不需要对Java虚拟机进行任何更改。此Java语言功能仅依赖于JVM当前验证和执行解码的能力，该能力出现在构造函数中的显式构造函数调用之前。

## JEP 457 - 类文件 API（预览）
提供用于解析、生成和转换 Java 类文件的标准 API。
**目标**
该API允许依赖它的框架和程序自动支持最新JDK中的最新类文件，以便可以快速、轻松地采用以类文件表示的新语言和VM功能。

## JEP 461 - 流收集器（预览） 
增强了 Stream API 以支持自定义中间操作。这将允许流管道以现有内置中间操作不易实现的方式转换数据。
**目标**
通过使流中的常见自定义操作更加灵活和富有表现力，提高开发人员的工作效率和代码可读性。尽可能允许中间操作操作无限大小的流。
```java
source.gather(a).gather(b).gather(c).collect(...)
等于
source.gather(a.andThen(b).andThen(c)).collect(...)
```

## JEP 463 - 隐式声明的类和实例主要方法（第二预览）
学生可以编写他们的第一个 Java 程序，而无需了解为大型程序设计的语言功能。学生无需使用单独的语言方言，而是可以为单类程序编写简化的声明，然后随着技能的增长无缝扩展他们的程序以使用更高级的功能。
```java
class HelloWorld {
    void main() {
        System.out.println("Hello, World!");
    }
}
```
**目标**

- 加速 Java 学习
- 为 Java 编程提供了一个平滑的入门通道，以便教师可以循序渐进地介绍概念。
- 帮助学生以简洁的方式编写基本程序，并随着他们的技能增长而优雅地扩展他们的代码。
- 减少编写简单程序（例如：脚本和命令行实用程序）的方式。
- 不引入单独的初学者工具链；学生程序应该使用与编译和运行任何 Java 程序相同的工具来编译和运行。

## JEP 459 - 字符串模板（第二预览）
String Templates 提供了一种更简洁、更直观的方式来动态构建字符串。通过使用占位符${}，我们可以将变量的值直接嵌入到字符串中，而不需要手动处理。在运行时，Java 编译器会将这些占位符替换为实际的变量值。并且，表达式支持局部变量、静态/非静态字段甚至方法、计算结果等特性。
```java
//concatenation
message = "Greetings " + name + "!";

//String.format()
message = String.format("Greetings %s!"， name);  //concatenation

//MessageFormat
message = new MessageFormat("Greetings {0}!").format(name);

//StringBuilder
message = new StringBuilder().append("Greetings ").append(name).append("!").toString();
```
```java
String message = STR."Greetings \{name}!";
```
在上面的模板表达式中：

- STR 是模板处理器。
- \{name}为表达式，运行时，这些表达式将被相应的变量值替换。

Java 目前支持三种模板处理器：

- STR：自动执行字符串插值，即将模板中的每个嵌入式表达式替换为其值（转换为字符串）。
- FMT：和 STR 类似，但是它还可以接受格式说明符，这些格式说明符出现在嵌入式表达式的左边，用来控制输出的样式
- RAW：不会像 STR 和 FMT 模板处理器那样自动处理字符串模板，而是返回一个 StringTemplate 对象，这个对象包含了模板中的文本和表达式的信息
```java
String name = "Lokesh";

//STR
String message = STR."Greetings \{name}.";

//FMT
String message = STR."Greetings %-12s\{name}.";

//RAW
StringTemplate st = RAW."Greetings \{name}.";
String message = STR.process(st);
```
除了 JDK 自带的三种模板处理器外，你还可以实现 StringTemplate.Processor 接口来创建自己的模板处理器。
我们可以使用局部变量、静态/非静态字段甚至方法作为嵌入表达式：
```java
//variable
message = STR."Greetings \{name}!";

//method
message = STR."Greetings \{getName()}!";

//field
message = STR."Greetings \{this.name}!";
```
还可以在表达式中执行计算并打印结果：
```java
int x = 10， y = 20;
String s = STR."\{x} + \{y} = \{x + y}";  //"10 + 20 = 30"
```
**目标**

- 通过轻松表达包含运行时计算值的字符串，简化了 Java 程序的编写。
- 增强混合文本和表达式的表达式的可读性，无论文本适合单个源行（如字符串文字）还是跨越多个源行（如文本块）。
- 通过支持模板及其嵌入表达式的值的验证和转换，提高 Java 程序的安全性，这些程序从用户提供的值组成字符串并将其传递到其他系统（例如，构建数据库查询）。
- 通过允许 Java 库定义字符串模板中使用的格式化语法来保留灵活性。
- 简化了接受非 Java 语言（例如 SQL、XML 和 JSON）编写的字符串的 API 的使用。
- 允许创建根据文字文本和嵌入表达式计算的非字符串值，而无需通过中间字符串表示形式进行传输。

## JEP 462 - 结构化并发（第二预览）
 简化并发编程。结构化并发将在不同线程中运行的相关任务组视为单个工作单元，从而简化错误处理和取消、提高可靠性并增强可观察性。
**目标**
通过推广一种编程风格来简化并发代码的开发，这种编程风格可以消除因取消和关闭而产生的常见风险（例如线程泄漏和取消延迟），并提高并发代码的可观察性。

## JEP 464 - 范围值（第二预览）
实现线程内和线程间不可变数据的高效共享。
**目标**

- 易于使用 - 提供一个编程模型来在线程内以及与子线程共享数据，以简化有关数据流的推理。
- 可理解性：：使共享数据的生命周期从代码的语法结构中可见。
- 鲁棒性：：确保调用者共享的数据只能由合法的被调用者检索。
- 性能：：将共享数据视为不可变，以允许大量线程共享，并实现运行时优化。

## JEP 460 - 矢量 API（第七次孵化器）
一个用于表达向量计算的 API，可在运行时可靠地在支持的 CPU 架构上编译为最佳向量指令，从而实现优于等效标量计算的性能。
**目标**

- 提供清晰简洁的 API，能够清晰简洁地表达各种向量计算，这些向量计算由循环内组成的向量运算序列组成，并且可能还包含控制流。
- 该 API 设计为与 CPU 架构无关，可在支持向量指令的多种架构上实现。
- 在 x64 和 AArch64 架构上提供可靠的运行时编译和性能。

这是对数组元素的简单标量计算：
```java
void scalarComputation(float[] a， float[] b， float[] c) {
    for (int i = 0; i < a.length; i++) {
        c[i] = (a[i] * a[i] + b[i] * b[i]) * -1.0f;
    }
}
```
这是使用 Vector API 进行的等效向量计算：
```java
static final VectorSpecies<Float> SPECIES = FloatVector.SPECIES_PREFERRED;

void vectorComputation(float[] a， float[] b， float[] c) {
    int i = 0;
    int upperBound = SPECIES.loopBound(a.length);
    for (; i < upperBound; i += SPECIES.length()) {
        // FloatVector va， vb， vc;
        var va = FloatVector.fromArray(SPECIES， a， i);
        var vb = FloatVector.fromArray(SPECIES， b， i);
        var vc = va.mul(va)
        .add(vb.mul(vb))
        .neg();
        vc.intoArray(c， i);
    }
    for (; i < a.length; i++) {
        c[i] = (a[i] * a[i] + b[i] * b[i]) * -1.0f;
    }
}
```


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/ublwgsw407g5bgqo>