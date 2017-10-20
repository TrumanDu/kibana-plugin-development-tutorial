# app案例之elasticsearch_status

## 简介

在这个案例中，项目目标是实现一个elasticsearch_status
app插件，在插件中可以查看elasticsearch 所有的index,以及他们的status。在这个案例中主要讲解如何开发app插件，以及如何在kibana中与elasticsearch通信。

## 实践

### 准备

首先新建项目 elasticsearch_status\([源码详见](https://github.com/TrumanDu/kibana_plugin/tree/master/clock)\)

然后利用[模板工具](https://github.com/elastic/template-kibana-plugin/)生成项目

### 1.修改index.js

这个文件主要是根据kibana api 定义该插件类型，本次demo 定义插件类型为visTypes.修改内容如下：

```

```

### 2.新增clock.js


### 3.新增页面文件



### 4.运行

在kibana 根目录下执行 npm start命令即可，效果如下：


### 5.总结



## 参考

[Writing Kibana 4 Plugins – Simple Visualizations](https://www.timroes.de/2015/12/02/writing-kibana-4-plugins-simple-visualizations/)

