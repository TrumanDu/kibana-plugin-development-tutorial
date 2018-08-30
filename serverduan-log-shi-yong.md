## Server 端log使用

在开发过程中，log的使用非常关键，那么如何在kibana后端使用log?在本章中我会介绍到

在server 端，程序可以获得server对象，查看kibana源码，我发现，官方使用的 是server.log。这个文档中的内容是根据我自己的开发经验发现的，可能后期无效，如果有官方文建议首先参考官方文档

- info

  ```server.log(['info', 'cleaner'], 'delete index success .');```
- error

  ```server.log(['error', 'cleaner'], 'delete  index unsuccessful .', response);```
  
  期中第一个参数是log级别，第二个参数是plugin名称。