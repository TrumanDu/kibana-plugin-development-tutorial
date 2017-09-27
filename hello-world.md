# Hello World Demo
本章主要讲解如何开发一个简单的kibana插件，实现一个kibana app，在页面上输出hello world。

使用官方推荐的[模板工具](https://github.com/elastic/template-kibana-plugin/)生成

1. Install SAO
```
npm install -g sao
```
2. 创建工程目录

在kibana工程plugin 新建demo目录
3. 生成代码

在demo目录下执行：
```
sao kibana-plugin
```
tip：如果需要制定版本使用：```sao kibana-plugin@6.2.2```