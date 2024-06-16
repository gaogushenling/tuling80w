# 如果 Sentinel 的异常处理规则不满足需求，应该怎么办？

如果 Sentinel 的默认异常处理机制无法满足您的需求，您可以选择自定义异常处理规则。
Sentinel 允许您通过自定义实现 BlockedExceptionHandler 接口，然后将自定义的异常处理器对象交给 Spring 容器进行管理。
您可以根据实际业务需求，定制化异常处理策略，例如全局兜底处理、日志打印、空指针检查等。
同时，您还可以在处理器中加入自定义的业务逻辑，例如对异常进行分类、统计和反馈等。
这样，您可以根据具体的应用场景和业务需求，灵活地扩展 Sentinel 的异常处理能力。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/iq3xku3g91gkg06n>