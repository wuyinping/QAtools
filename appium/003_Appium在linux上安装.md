<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

    - [安装过程](#)
- [Android](#android)
- [Dev](#dev)
    - [troubleshooting](#troubleshooting)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 安装过程

1. 安装ubuntu14.04
  * 下载ubuntu14.04，刻录到U盘
  * U盘启动安装系统
2. 更新ubuntu14.04
  * `sudo apt-get update; sudo apt-get upgrade`
  * 见troubleshooting_1
3. 安装nodejs, [ubuntu安装nodejs - appium文档](https://github.com/nodejs/node-v0.x-archive/wiki/Installing-Node.js-via-package-manager#debian-and-ubuntu-based-linux-distributions)
  * `curl -sL https://deb.nodesource.com/setup_5.x | sudo -E bash -; sudo apt-get install --yes nodejs`
4. 安装Android SDK Manager
  * 下载[Android SDK Manager](http://pan.baidu.com/s/1c0t28vQ)
5. 下载Android SDK
  * 解压缩，到android-sdk-linux/tools/目录下执行 `sh android` 下载更新SDK包
  * 添加Android SDK的platform-tools和tools目录到path环境变量
  * 见troubleshooting_1
6. 安装Android Studio
7. 安装Apache Ant
  * 下载[Apache Ant](http://pan.baidu.com/s/1c0t28vQ)
8. 设置ANDROID_HOME环境变量
  * `export ANDROID_HOME="~/Android/Sdk"`
9. 安装git
10. 下载Appium仓库到本地
  * 见troubleshooting_4
11. 进入目录，先运行`node bin/appium-doctor.js --dev`检查一下所需的依赖，参考 https://github.com/appium/appium/issues/4937

  ```bash
# Android
ANDROID_HOME
JAVA_HOME
ADB
Android
Emulator
# Dev
mvn
adb
ant
android-16
android-19
  ```
  
`./reset.sh --android --verbose`

## troubleshooting
**声明**
ubuntu使用的是 14.04 LTS 版本

1. ubuntu运行android studio出错unable to run mksdcard  
缺少32位的开发lib，安装如下lib
`sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6`
2. ubuntu update时提示MD5 sum mismatch  
最终将apt源换成了**aliyun**的，才解决问题。163、neu、bjtu都不好使了。
3. 安装配置搜狗输入法  
http://jingyan.baidu.com/article/a3aad71aa1abe7b1fa009641.html
4. Agent admitted failure to sign using the key  
在当前用户下执行命令：`ssh-add`
5. Error target id is not valid. Use 'android list targets' to get the target id  
下载对应的Android API。
6. LG G3连接ubuntu14.04电脑后，`adb devices`无法识别  
改变媒体设备(MTP)为发送图像(PTP)模式，重新插拔手机。