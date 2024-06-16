# 如何在NGINX中实现基于IP的访问控制（IP黑白名单）？

在NGINX中，你可以使用`ngx_http_access_module`模块来实现基于IP的访问控制，包括IP黑名单和IP白名单。这允许你限制或允许特定IP地址的访问。以下是如何在NGINX中配置基于IP的访问控制的步骤：

1.  打开NGINX配置文件（通常是`nginx.conf`或在`/etc/nginx`目录中的其他文件）。 
2.  在适当的位置，使用`allow`和`deny`指令来配置IP黑白名单。`allow`指定允许的IP地址，`deny`指定拒绝的IP地址。可以根据需要在`http`块、`server`块或`location`块中设置。例如： 
```nginx
http {
    server {
        location / {
            # 允许指定的IP地址访问
            allow 192.168.1.100;
            allow 10.0.0.0/24;
            # 拒绝其他IP地址访问
            deny all;
        }
    }
}
```
 

3.  保存配置文件并重新加载或重启NGINX，以使配置生效。 

上述配置将只允许`192.168.1.100`和`10.0.0.0/24`这些IP地址访问相应的位置，而拒绝其他IP地址的访问。

需要注意的是，`allow`和`deny`指令的顺序很重要。如果顺序颠倒，可能会导致预期之外的结果。在实际应用中，你可以根据需求配置更复杂的IP黑白名单规则，如使用正则表达式匹配特定IP地址范围等。

此外，为了确保安全性，可以使用防火墙或其他网络安全解决方案，以增加额外的层次的IP访问控制。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/cra9n2tgpb0777ak>