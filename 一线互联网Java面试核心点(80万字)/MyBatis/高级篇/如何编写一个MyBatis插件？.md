# 如何编写一个MyBatis插件？

编写一个MyBatis插件可以让你在执行SQL语句前后进行自定义的操作，比如日志记录、性能监控等。下面我将演示一个简单的MyBatis插件，它会在执行查询SQL语句前打印一条日志。
首先，你需要实现一个MyBatis的拦截器（Interceptor）。一个拦截器需要实现MyBatis的`Interceptor`接口，其中最重要的是`intercept`方法，它会在执行SQL语句前后被调用。
```java
import org.apache.ibatis.executor.statement.StatementHandler;
import org.apache.ibatis.plugin.*;

import java.sql.Statement;
import java.util.Properties;

@Intercepts({@Signature(type = StatementHandler.class, method = "query", args = {Statement.class, org.apache.ibatis.session.ResultHandler.class})})
public class LoggingInterceptor implements Interceptor {
    @Override
    public Object intercept(Invocation invocation) throws Throwable {
        System.out.println("Before executing query...");
        Object result = invocation.proceed(); // 执行原来的方法
        System.out.println("After executing query...");
        return result;
    }

    @Override
    public Object plugin(Object target) {
        return Plugin.wrap(target, this);
    }

    @Override
    public void setProperties(Properties properties) {
        // 可以在这里设置一些属性
    }
}
```
在这个例子中，`LoggingInterceptor`实现了`Interceptor`接口，重写了`intercept`方法，在执行查询SQL语句前后打印日志。
接下来，你需要在MyBatis的配置文件中注册这个插件：
```xml
<plugins>
    <plugin interceptor="com.example.LoggingInterceptor">
        <!-- 这里是插件的属性配置，如果有的话 -->
    </plugin>
</plugins>
```
在配置中，`interceptor`属性指定了插件的完全限定名，即`LoggingInterceptor`的类名。你还可以在插件标签内设置插件的属性，这些属性会在插件的`setProperties`方法中被接收。
最后，当你执行查询操作时，插件会自动拦截并执行你在`intercept`方法中定义的逻辑。
需要注意的是，这只是一个简单的插件示例。MyBatis插件可以实现更复杂的逻辑，比如性能分析、自定义SQL改写等。编写插件时要确保逻辑正确，不影响系统稳定性和性能。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/znduwo5ybo3mck75>