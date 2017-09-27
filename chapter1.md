# 插件资源

以下 是对开发kibana 插件有用的资源
## IRC channel
kibana 官方为大家注册了一个类似聊天室的通道，在这里大家可以获取有用咨询和交流 [Freenode Web Client](http://webchat.freenode.net/?channels=kibana).

[float]
==== Some light reading
- Our {repo}blob/master/CONTRIBUTING.md[contributing guide] can help you get a development environment going
- Tim Roes' excellent blog series https://www.timroes.de/2016/02/21/writing-kibana-plugins-custom-applications/[Writing Kibana Plugins]

[float]
==== Videos
- https://www.elastic.co/elasticon/2015/sf/contributors-guide-to-the-kibana-galaxy[Contributors Guide to the Kibana Galaxy]
- https://www.elastic.co/elasticon/conf/2016/sf/how-to-build-your-own-kibana-plugins[Kibana Plugin Dev - Elasticon 2016]

[float]
==== Plugin Generator

Check out the https://github.com/elastic/generator-kibana-plugin[plugin generator] to kick-start your plugin.

[float]
==== References in the code
 - {repo}blob/{branch}/src/server/plugins/plugin.js[Plugin class]: What options does the `kibana.Plugin` class accept?
 - <<development-uiexports>>: What type of exports are available?
