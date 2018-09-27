## 实践
在本篇实现一个app 插件demo,在demo页面可以显示服务器端时间。
### 插件入口
在 在该文件中定义插件名，描述，以及插件前端和后端入口，配置。
```
export default function (kibana) {
  return new kibana.Plugin({
    require: ['elasticsearch'],
    name: 'demo',
    uiExports: {
      app: {
        title: 'Demo',
        description: 'An awesome Kibana plugin',
        main: 'plugins/demo/app',
        styleSheetPath: require('path').resolve(__dirname, 'public/app.scss'),
      },
    },

    config(Joi) {
      return Joi.object({
        enabled: Joi.boolean().default(true),
      }).default();
    },

    init(server, options) { // eslint-disable-line no-unused-vars
      // Add server routes and initialize the plugin here
      exampleRoute(server);
    }
  });
}
```
### 插件前端

### 服务端

```
export default function (server) {

  server.route({
    path: '/api/Demo/example',
    method: 'GET',
    handler(req, reply) {
      reply({ time: (new Date()).toISOString() });
    }
  });

}
```

### 效果
![](/assets/demo.png)