# 什么是缓存？在NGINX中如何配置缓存以提升性能？

缓存是一种在计算机系统中常用的技术，用于存储临时数据副本，以便在将来的请求中更快地访问这些数据。缓存可以显著提升应用程序和网站的性能，因为它可以减少对后端服务器或数据库的重复请求，从而减少响应时间并降低资源消耗。

在Web服务器中，缓存通常用于存储已经生成的页面、资源或数据，以便下次请求时可以直接提供这些内容，而无需重新生成或从原始数据源获取。这可以减少处理时间，降低服务器负载，并提高用户体验。

在NGINX中，你可以使用以下方法配置缓存以提升性能：

1.  **代理缓存**：
NGINX作为反向代理服务器时，可以通过`proxy_cache`和相关指令来设置代理缓存。你可以在`http`块内配置缓存路径、缓存键、缓存有效期等，然后在`location`块中使用`proxy_cache`指令来启用代理缓存。例如： 
```nginx
http {
    proxy_cache_path /path/to/cache levels=1:2 keys_zone=my_cache:10m max_size=10g;
    server {
        location / {
            proxy_pass http://backend_server;
            proxy_cache my_cache;
            proxy_cache_valid 200 1h;
        }
    }
}
```
 

2.  **FastCGI缓存**：
如果你使用FastCGI来处理动态内容，可以使用`fastcgi_cache`模块来设置FastCGI缓存。类似于代理缓存，你需要配置缓存路径、缓存键、缓存有效期等，然后在`location`块中使用`fastcgi_cache`指令启用缓存。 
3.  **静态文件缓存**：
使用`expires`和`add_header`指令，你可以设置静态文件的缓存过期时间和缓存控制头部。这可以让客户端（浏览器）在一段时间内缓存静态资源，从而减少重复下载。 
4.  **内存缓存**：
如果服务器有足够的内存，你可以考虑使用`proxy_cache_path`指令中的`keys_zone`参数来设置内存缓存区，以加快缓存访问速度。 
5.  **条件缓存**：
使用条件缓存，你可以在缓存数据的同时，使用`proxy_cache_revalidate`和`proxy_cache_use_stale`等指令设置条件，以决定何时使用缓存，何时重新验证源服务器。 

以上只是一些NGINX缓存的基本配置示例。在实际应用中，你还可以根据具体的需求和网站特点进行更详细的配置，以提升性能并优化缓存策略。不同的应用场景可能需要不同的缓存设置，因此建议根据实际情况进行调整。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/zih7cmkd3cixron7>