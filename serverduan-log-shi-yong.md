## Server 端log使用

在开发过程中，log的使用非常关键，那么如何在kibana后端使用log?在本章中我会介绍到

在server 端，程序可以获得server对象，查看kibana源码，我发现，官方使用的 是server.log。这个文档中的内容是根据我自己的开发经验发现的，可能后期无效，如果有官方文建议首先参考官方文档

- info

  ```server.log(['info', 'cleaner'], 'delete index success .');```
- error

  ```server.log(['error', 'cleaner'], 'delete  index unsuccessful .', response);```
  
  期中第一个参数是log级别，第二个参数是plugin名称。
  
  
  ## log配置
  kibana 的log 配置都是在kibana.yml中配置的，这里仅说明如何显示自定义级别的log,更详细信息，详见[官网](https://www.elastic.co/guide/en/kibana/current/settings.html)

对于自定义级别的log可以通过```logging.events.response: ["error"]```





## 参考
1. [kibana-docker-log-issue](https://discuss.elastic.co/t/kibana-docker-log-issue/147647)