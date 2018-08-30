##获取配置文件中内容

在程序入口文件index.js 中可以在init方法中获取server对象，通过该server可以获取config,具体方式如下：
```
init(server, options) {
     const config = server.config();
     const url = config.get('elasticsearch.url');
    }
```

## 自定义配置
