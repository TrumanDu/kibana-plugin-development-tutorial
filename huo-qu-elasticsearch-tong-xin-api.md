# 与Elasticserach 通信

## 官方文档推荐
Kibana在服务器和浏览器上公开两个客户端，以与Elasticserach进行通信。有一个管理客户端用于管理集群的状态，以及一个数据客户端

### 服务器客户端

在服务器端可以通过以下方式获取：

```
  const adminCluster = server.plugins.elasticsearch.getCluster('admin');
  const dataCluster = server.plugins.elasticsearch.getCluster('data');

  //ping as the configured elasticsearch.user in kibana.yml
  adminCluster.callWithInternalUser('ping');

  //ping as the user specified in the current requests header
  adminCluster.callWithRequest(req, 'ping');
```

### 浏览器客户端

浏览器客户端可以通过AngularJS services获取：

```
uiModules.get('kibana')
.run(function (es) {
  es.ping()
  .catch(err => {
    console.log('error pinging servers');
  });
});
```

## 非官方文档推荐


### 服务器客户端

首先引入依赖包
```
const elasticsearch = require('elasticsearch');
```
server 端初始化调用文件中可以按如下使用：
```
  const client = new elasticsearch.Client({
    host: config.get('elasticsearch.url'),
    requestTimeout: 120000
    //log: 'trace'
  });
client.indices.stats({
  human: true,
  fields: ['docs', 'store']
  }, function (err, response) {
  console.log(response);
  });
}
```



