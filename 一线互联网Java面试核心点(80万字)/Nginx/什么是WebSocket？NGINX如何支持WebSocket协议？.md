# 什么是WebSocket？NGINX如何支持WebSocket协议？

WebSocket是一种在单个TCP连接上实现全双工通信的协议，它允许服务器和客户端之间进行双向通信，而无需通过多次HTTP请求和响应来完成。与传统的HTTP请求-响应模式不同，WebSocket连接保持打开状态，可以在连接建立后随时进行双向数据交换，这对于实时通信应用非常有用，如在线聊天、实时游戏等。

NGINX可以通过适当的配置来支持WebSocket协议。以下是在NGINX中支持WebSocket的一些配置步骤：

1.  **安装更新的版本**：
确保你正在使用更新的NGINX版本，因为WebSocket支持在较早的版本中可能不太完善。建议使用NGINX 1.3.13及更高版本。 
2.  **配置HTTP请求头部**：
WebSocket连接需要一些特定的HTTP头部字段来协商和建立连接。在客户端发起WebSocket连接时，它会发送一个升级请求，包括`Upgrade`头部和`Connection`头部。服务器需要适当地响应这些头部，以指示连接已升级为WebSocket连接。 
```nginx
location /ws-endpoint {
    proxy_pass http://backend_server;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
}
```
 

3.  **启用WebSocket模块**：
确保已在编译NGINX时启用WebSocket模块。在配置文件中，你可以使用`proxy_set_header`指令来设置Upgrade和Connection头部，以及其他可能需要的头部。 
4.  **后端服务器设置**：
如果WebSocket连接需要与后端服务器进行通信，确保后端服务器能够正确处理WebSocket连接，包括协商和处理WebSocket数据帧。 
5.  **测试连接**：
在配置完成后，可以使用WebSocket客户端工具或浏览器的开发工具来测试WebSocket连接，以确保连接已成功建立。 

总之，在配置NGINX以支持WebSocket时，关键是正确处理升级请求和响应头部，以及在后端服务器上正确处理WebSocket连接。通过合适的配置，NGINX可以用作WebSocket代理，实现WebSocket连接的转发和负载均衡。


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/co8nsw9wletch16k>