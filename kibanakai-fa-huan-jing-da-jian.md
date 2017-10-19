要开发kibana 插件，首先要在本地搭建开发环境，我这里推荐使用vs code,如果问我为什么，我只想说这么火的开发工具，不用一下，怎么跟上世界开发潮流呢。

## 第一步

首先 需要安装node.js,可以去[官网](https://nodejs.org/en/)下载最新版本，对于如何安装就不废话了。

## 第二步

下载 kibana 源代码，在[github](https://github.com/elastic/kibana)下下载即可。

## 第三步

在kibana项目根目录下执行

```
1. $ git tag
2. $ git checkout 指定version
```

## 第四步

这步非常重要，绝大部分无法正常启动kibana 项目，都是由于无法安装完整所有依赖，即npm install 执行过程报错。强烈建议有VPN，使用npm install，我尝试过cnpm install ,虽然执行不错，但是有部分依赖无法下载下来，造成启动失败。

在公司开发的人请注意，公司防火墙可能会限制从github 中下载依赖，这块需要将所有git下载代码由ssh强制更换成http。

修改方式如下：

```
git config --global url."https://".insteadOf "git://"
```

或者在.gitconfig文件中添加

```
[url "https://"]
    insteadOf = git://
```

两者原理一样，都是将ssh 方式转换成http方式。

接下来执行

```
npm install
```

执行成功以后，执行启动命令

```
npm start
```

在浏览器中访问[https://localhost:5061即可。](https://localhost:5061即可。)

默认dev 启动方式会使用ssl,所以是https,如果需要修改的话，可以修改\kibana\src\cli\serve\serve.js文件。修改位置如下：

```
  if (opts.dev) {
    set('env', 'development');
    set('optimize.lazy', true);

    // if (opts.ssl) {
    //   set('server.ssl.enabled', true);
    // }

    // if (opts.ssl && !has('server.ssl.certificate') && !has('server.ssl.key')) {
    //   set('server.ssl.certificate', DEV_SSL_CERT_PATH);
    //   set('server.ssl.key', DEV_SSL_KEY_PATH);
    // }
  }
```



