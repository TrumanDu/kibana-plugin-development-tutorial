这里的前后端通信指的是kibana插件server端与client端通信。一般都是http请求，本章讲解angulajs与react两种模式下通信如何编写。

## server端
在index.js初始化server端代码
### 初始化
```
    import serverRoute from './server/routes/server';
    init(server, options) {
      // Add server routes and initialize the plugin here
      serverRoute(server, options);
  });
```
### 构建路由


## angularjs

## react