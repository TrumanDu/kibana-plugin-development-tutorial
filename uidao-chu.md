## UI Exports

可用UiExport类型的汇总列表:

| 类型 | 目的 |
| :--- | :--- |
| **hacks** | 应包含在每个应用程序中的任何模块 |
| **visTypes** | 注册提供商的模块`ui/registry/vis_types`。 |
| **fieldFormats** | 注册提供商的模块`ui/registry/field_formats`。 |
| **spyModes** | 注册提供商的模块`ui/registry/spy_modes`。 |
| **chromeNavControls** | 注册提供商的模块`ui/registry/chrome_nav_controls`。 |
| **navbarExtensions** | 注册提供商的模块`ui/registry/navbar_extensions`。 |
| **docViews** | 注册提供商的模块`ui/registry/doc_views`。 |
| **app** | 将应用程序添加到系统。这个uiExport类型被定义为元数据的对象，而不仅仅是一个模块id。 |

关于以上解释，在官网没有给出各个类型的解释，针对国内开发者，尤其对于英语不好的人，名字起的再好，我们也不知道它是要干嘛。

这块描述的是kibana plugin 支持的类型。目前我有看到**visTypes**\(视图组件\)，**app**\(应用组件\)，**hacks**\(集合组件\)，**chromeNavControls**\(浏览器导航组件\)，其他组件暂未看到案例

