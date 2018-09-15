##获取配置文件中内容

在程序入口文件index.js 中可以在init方法中获取server对象，通过该server可以获取config,具体方式如下：
```
init(server, options) {
     const config = server.config();
     const url = config.get('elasticsearch.url');
    }
```

## 自定义配置

### 1.配置校验与默认值

在index.js new kibana.Plugin中可以传入config方法，如下：
```
    config(Joi) {
      return Joi.object({
        enabled: Joi.boolean().default(true),
        scheduleTime: Joi.number().default(60),
        mergePattern: Joi.string().default('[^a-z]+$'),
      }).default();
    },
```
这里使用的Joi,通过它可以设置配置参数的数据类型，以及默认值。参数默认格式是[pluginName].enabled等。
