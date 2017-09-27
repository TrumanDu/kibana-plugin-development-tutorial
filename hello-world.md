# Hello World Demo
本章主要讲解如何开发一个简单的kibana插件，实现一个kibana app，在页面上输出hello world。

使用官方推荐的[模板工具](https://github.com/elastic/template-kibana-plugin/)生成

## 1. Install SAO
```
npm install -g sao
```
## 2. 创建工程目录

在kibana工程plugin 新建demo目录
## 3. 生成代码

在demo目录下执行：
```
sao kibana-plugin
```
tip：如果需要制定版本使用：```sao kibana-plugin@6.2.2```

然后根据提示输入自定义选项，我这边运行效果如下：
```
PS E:\github\kibana\kibana\plugins\demo> sao kibana-plugin
> Installing template-kibana-plugin with npm...
? Name of your plugin? demo
? Provide a short description Hello World
? What Kibana version are you targeting? 5.5.1
? Should an app component be generated? Yes
? Should translation files be generated? Yes
? Should an hack component be generated? Yes
? Should a server API be generated? Yes
Initialized empty Git repository in E:/github/kibana/kibana/plugins/demo/.git/
> spawn-sync@1.0.15 postinstall E:\github\kibana\kibana\plugins\demo\node_modules\spawn-sync
> node postinstall

> demo@0.0.0 postinstall E:\github\kibana\kibana\plugins\demo
> plugin-helpers postinstall

npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN demo@0.0.0 No repository field.
npm WARN demo@0.0.0 No license field.

added 361 packages in 30.126s
success Your plugin has been created, use `npm start` to run it
```
## 4. 运行

在kibana工程目录下执行：```npm start```

## 5. 效果
![](/assets/搜狗截图20170927182812.jpg)
