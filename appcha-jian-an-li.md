# app案例之elasticsearch\_status

## 简介

在这个案例中，项目目标是实现一个elasticsearch\_status  
app插件，在插件中可以查看elasticsearch 所有的index,以及他们的status。在这个案例中主要讲解如何开发app插件，以及如何在kibana中与elasticsearch通信。

## 实践

### 准备

首先新建项目 elasticsearch\_status\([源码详见](https://github.com/TrumanDu/kibana_plugin/tree/master/elasticsearch_status)\)

然后利用[模板工具](https://github.com/elastic/template-kibana-plugin/)生成项目

### 1.修改index.js

这个文件主要是根据kibana api 定义该插件类型，本次demo 定义插件类型为app.修改内容如下：

```
const api =require('./server/routes');
export default function (kibana) {
  return new kibana.Plugin({
    require: ['elasticsearch'],

    uiExports: {
      // Register the app component of our plugin to uiExports
      app: {
        // The title of the app (will be shown to the user)
        title: 'Indices',
        // An description of the application.
        description: 'An awesome Kibana plugin',
        // The require reference to the JavaScript file for this app
        main: 'plugins/elasticsearch_status/app',
        // The require reference to the icon of the app
        icon: 'plugins/elasticsearch_status/icon.svg'
      }
    },

    // The init method will be executed when the Kibana server starts and loads
    // this plugin. It is used to set up everything that you need.
    init(server, options) {
      // Just call the api module that we imported above (the server/routes.js file)
      // and pass the server to it, so it can register several API interfaces at the server.
      api(server);
    }

  });
};
```

在上面代码中app{}按照kibana插件接口编写，没有什么好解释的。在init\(\){}方法可以在kibana启动的时候调用，在这里面可以做任意化的操作，这块是用作server端，提供路由查询elasticsearch功能。该方法中传入参数server,也很有用途，比较获取配置信息，创建路由等。

### 2.新增routes.js

在server目录新建routes.js文件，主要是用作提供server端查询elasticsearch数据。

```
export default function (server) {

  const call = server.plugins.elasticsearch.getCluster('admin').callWithRequest;
  server.route({
    path: '/api/elasticsearch_status/indices',
    method: 'GET',
    handler(req, reply) {
        call(req, 'cluster.state').then(function (response) {
          // Return just the names of all indices to the client.
          reply(
            Object.keys(response.metadata.indices)
          );
        });
    }
  });

  // Add a route to retrieve the status of an index by its name
  server.route({
    path: '/api/elasticsearch_status/index/{name}',
    method: 'GET',
    handler(req, reply) {
      call(req, 'cluster.state', {
        metric: 'metadata',
        index: req.params.name
      }).then(function (response) {
        reply(response.metadata.indices[req.params.name]);
      });
    }
  });

};
```

### 3.新增app.js

    const uiModules =require ('ui/modules');
    const uiRoutes =require ('ui/routes');

    require ('ui/autoload/styles');
    require ('./less/main.less');
    const overviewTemplate =require('./templates/index.html');
    const detailTemplate =require('./templates/detail.html');

    uiRoutes.enable();
    uiRoutes
    .when('/', {
      template: overviewTemplate,
      controller: 'elasticsearchStatusController',
      controllerAs: 'ctrl'
    })
    .when('/index/:name', {
      template: detailTemplate,
      controller: 'elasticsearchDetailController',
      controllerAs: 'ctrl'
    });

    uiModules
    .get('app/elasticsearch_status')
    .controller('elasticsearchStatusController', function ($http) {
      $http.get('../api/elasticsearch_status/indices').then((response) => {
        this.indices = response.data;
      });
    })
    .controller('elasticsearchDetailController', function($routeParams, $http) {
      this.index = $routeParams.name;

      $http.get(`../api/elasticsearch_status/index/${this.index}`).then((response) => {
        this.status = response.data;
      });
    });

该文件主要是提供controller,调用后台API,在页面展示数据

index.html

```
<div class="container">
  <div class="row">
    <div class="col-12-sm">
      <h1>Elasticsearch Status</h1>
      <ul class="indexList">
        <li ng-repeat="index in ctrl.indices">
          <a href="#/index/{{index}}">{{ index }}</a>
        </li>
      </ul>
    </div>
  </div>
</div>
```

显示所有index 列表  
detail.html

```
<div class="container">
  <div class="row">
    <div class="col-12-sm">
            <a href="#/">Index list</a>
      <h1>Index: {{ ctrl.index }}</h1>
            <pre>{{ ctrl.status | json }}</pre>
    </div>
  </div>
</div>
```

### 4.运行

在kibana 根目录下执行 npm start命令即可，效果如下：  
![](/assets/elasticsearch_status.gif)

### 5.总结

## 参考



