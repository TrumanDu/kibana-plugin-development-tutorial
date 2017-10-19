# visTypes案例之clock

## 简介

在这个案例中，项目目标是实现一个clock插件，在插件中可以设置时间格式。在这个案例能讲解如何定义一个visType 插件，在visType 插件有哪些特性可以使用。

## 实践

在 开始写项目之前，先说一下kibana插件对于kibana版本绑定，官方给的已知kibana plugin ,可能大家下载下来在自己 的版本中无法运行，这个时候需要修改一下package.json中的version,该成自己需要使用的版本即可。

在开发之前，先说一下，由于本人不是专业的前端开发人员，对于es6,angular.js经验为零，只能边看教程，边学习，难免存在一些旧思想，欢迎大家指正交流。

## 准备

首先新建项目clock

然后利用[模板工具](https://github.com/elastic/template-kibana-plugin/)生成项目

    PS E:\github\kibana\kibana\plugins\clock> sao kibana-plugin
    ? Name of your plugin? clock
    ? Provide a short description An awesome Kibana plugin for clock !
    ? What Kibana version are you targeting? master
    ? Should an app component be generated? No
    ? Should translation files be generated? No
    ? Should an hack component be generated? No
    ? Should a server API be generated? No
    Initialized empty Git repository in E:/github/kibana/kibana/plugins/clock/.git/

    > spawn-sync@1.0.15 postinstall E:\github\kibana\kibana\plugins\clock\node_modules\spawn-sync
    > node postinstall


    > clock@0.0.0 postinstall E:\github\kibana\kibana\plugins\clock
    > plugin-helpers postinstall

    npm notice created a lockfile as package-lock.json. You should commit this file.
    npm WARN clock@0.0.0 No repository field.
    npm WARN clock@0.0.0 No license field.

    added 361 packages in 32.334s
    success Your plugin has been created, use `npm start` to run it

## 参考



