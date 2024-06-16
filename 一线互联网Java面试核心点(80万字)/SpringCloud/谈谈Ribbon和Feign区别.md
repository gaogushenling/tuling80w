# 谈谈Ribbon和Feign区别

在分布式系统的微服务构建中，Ribbon和Feign都是Netflix开发的Java库。
**Ribbon是一个客户端负载均衡器**，作用在于多个微服务实例间分发请求，提升可用性和性能。它可与各种HTTP客户端如RestTemplate配合使用来发送HTTP请求并进行负载均衡。
**Feign则是一个声明式的HTTP客户端**，通过编写接口来定义对远程微服务的需求。Feign使用注解和模板方法简化了远程调用的编写，使得调用远程服务的代码更加清晰和简洁。它更注重简洁的声明式编程模型，你只需编写接口并使用注解描述HTTP请求，Feign会在运行时生成实现类来执行实际的HTTP请求。
Ribbon和Feign都用于构建分布式系统中的微服务，但两者在用途、编程模型和集成上存在差异。**Ribbon更注重负载均衡**，需要配合其他库如RestTemplate来发送http请求，而Feign则采用声明式编程模型，只需编写接口和注解即可。此外，Ribbon提供了自定义负载均衡策略的能力，而**Feign通常与Ribbon一起使用以实现负载均衡**。
总的来说，如果你需要更多的控制和自定义负载均衡策略，可以选择Ribbon；如果你更喜欢简洁的声明式编程模型，可以选择Feign。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/hlz5p0zurwcgag11>