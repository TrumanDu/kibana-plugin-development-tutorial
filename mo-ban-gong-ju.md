最新信息，6.3+版本 kibana官方已经在内部集成模板生成工具，新版插件开发推荐使用kibana源码中自带工具。

本教程中介绍的方法依然可用，下面介绍一下版本模板工具的使用

```
git checkout 6.x
yarn kbn bootstrap
node scripts/generate_plugin my_plugin_name
```


## 参考
1. [template-kibana-plugin](https://github.com/elastic/template-kibana-plugin)
2. [kbn-plugin-generator](https://github.com/elastic/kibana/tree/master/packages/kbn-plugin-generator#quick-start)