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

~~这步非常重要，绝大部分无法正常启动kibana 项目，都是由于无法安装完整所有依赖，即npm install 执行过程报错。强烈建议有VPN，使用npm install，我尝试过cnpm install ,虽然执行不错，但是有部分依赖无法下载下来，造成启动失败。~~

~~在公司开发的人请注意，公司防火墙可能会限制从github 中下载依赖，这块需要将所有git下载代码由ssh强制更换成http。~~
~~修改方式如下：~~

```
git config --global url."https://".insteadOf "git://"
```

~~或者在.gitconfig文件中添加~~

```
[url "https://"]
    insteadOf = git://
```

~~两者原理一样，都是将ssh 方式转换成http方式。~~


以上改动是5.5.1版本需要做的，从6.x版本，kibana官方更新了包管理方式，使用了yarn,使用后的感觉是这个超级棒，值得推荐！

1. 安装yarn  

    ```npm install  -g yarn@1.6```
    **注意：**我这里安装的是1.6版本，yarn最新版本已经是1.7，使用该版本无法工作，暂未追究原因，这块需要注意。
    
2. 下载依赖  

    ```yarn kbn bootstrap```
    
3. 运行

    ```yarn start```
    
    
## vs code 搭配开发技巧

关于vs code强大我就不介绍了，这不是本文的重点。这块主要是建议安装的一些插件：

1. [Prettier formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
2. [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
3. [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
4. [JavaScript (ES6) code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)


建议将**其他格式化插件禁用**，多个格式化插件可能格式化完还是会爆红，这个是我目前发现格式化kibana代码最好的插件

关于debug,目前版本还无法配置，有看到官方提到在7.x版本，就可以在vscode 中配置debug了。具体如何配置参考vscode debug教程。（如果有人现在知道的话，欢迎帮忙添加）


## 参考
1. [setting-up-your-development-environment](https://github.com/elastic/kibana/blob/master/CONTRIBUTING.md#setting-up-your-development-environment)

