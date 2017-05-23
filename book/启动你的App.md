---
description: 启动你的第一个React Native 应用
---

# 启动你的App

本章提要

- 1.搭建React Native环境
- 2.启动App

## 1.搭建React Native环境
啊哈，我们即将近距离接触React Native了。不过，我们得在这之前安装一下React Native环境。

首先，我们来安装Node.js环境。
如果你的系统是Windows，那么到Node.js官网上下载安装包，一路next就行了。
如果是Linux或MacOS，那么作者君推荐使用神奇的nvm。
nvm的地址是:
https://github.com/creationix/nvm
按照说明安装即可。

然后执行

```
nvm install x.xx.x(要安装的版本号)
```
这样Node.js就安装完毕了。

接下来，我们来安装Java环境。去Oracle的官网上下载安装包http://www.oracle.com/technetwork/java/javase/downloads/index.html
然后安装。

同样的，Windows用户一路next然后设置JAVA_HOME环境变量即可。
对于Linux和MacOS用户来说，会稍稍麻烦一些。
首先把安装包解压到opt目录，然后在/etc/profile里加上
```
export JAVA_HOME=/opt/(这里是安装包解压后的路径，别填错)
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```
最后别忘了执行一下`source /etc/profile`

如果执行`java -version`可以正常输出的话，那么恭喜啦，对很多人来说不怎么好装的Java环境被你安装好了哟

然后安装安卓环境，我们先去Google的开发者网站https://developer.android.google.cn/studio/index.html 上下载Android Studio。
安装好Android Studio，我们需要安装SDK及SDK Tools。首先，我们来安装SDK。在SDK Platforms，选择Show Package Details，然后勾选Android 6.0下的Google APIs，Android SDK Platform 23，Intel x86 Atom_64 System Image还有Google APIs Intel x86 Atom_64 System Image。接下来，在SDK Tools窗口中选择Show Package Details，然后选中有23.0.1的选项并下载。
最后，我们需要在/etc/profile中写入环境变量

```
export ANDROID_HOME='/home/elven/Android/Sdk'
```
Windows用户也需要设置`ANDROID_HOME`这个环境变量。

如果是老司机的话，Android Studio是不需要安装的，不过为了及时，方便的更新SDK，还是装上吧。

再来三步，环境就安装好啦，如果感觉有些焦灼，给自己冲杯茶，咖啡或果汁是很好的选择~

接下来，我们需要安装React Native。在终端中执行

```
npm install react-native-cli -g
```

然后安装Yarn

```
npm install yarn -g
```

最后安装Watchman，按照这里( 
https://facebook.github.io/watchman/docs/install.html#build-install
    
)的说明一步步安装。
如果有报错的话，多半是有什么没装，按照报错里的信息装一下就Ok了。另外，Windows系统不需要安装Watchman（其实是Watchman不能在在这个系统运行）

到这里，开发环境就搭建好了。

## 2.启动App

在启动App之前，我们得创建一个新的项目（啥都没有拿什么启动，哈哈）
在终端输入

```
react-native init 项目名
```

等待一会儿，进入项目目录。
好了，拿出你的小手机和数据线并与电脑相连。
新开一个终端，然后进入项目目录，执行

```
react-native start
```
回到原来的终端，执行

```
react-native run-android
```
如果是Windows的话，只要执行`run-android`这条命令就可以，packager可以自行启动，
这里分开是为了保证App可以正常启动。

闭一会儿眼睛，稍稍休息下之后，你就会在手机上看到启动好的App了！

作者君猜，你可能不知道项目中的index.android.js里的最后一句是什么意思，所以就在代码里小小的解释一下:

```
AppRegistry.registerComponent('项目名称', () => 组件名称);
```