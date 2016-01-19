<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [安装完需要source一下rvm的脚本](#source-rvm)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

1. 源码启动  
进入appium目录，执行命令`node .`

2. 下载appium/smaple-code源码，用来练习  
`git clone git@github.com:appium/sample-code.git`  
我是用ruby语言开发，所以需要安装ruby和相关的工具。

3. 安装rvm  
rvm官网 http://rvm.io/  
安装rvm
  ```bash
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -sSL https://get.rvm.io | bash -s stable
# 安装完需要source一下rvm的脚本
source /home/guolei/.rvm/scripts/rvm
  ```

4. 安装ruby  
用rvm这个ruby version manager安装ruby-2.0.0  
`rvm install 2.0.0`  
过程中需要输入sudo用户的密码

5. 安装bundler  
先将gem source换为淘宝源  
`gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/`  
编辑价目录下的.gemrc配置文件，添加如下配置，不安装ri和rdoc等文档  
`gem: --no-ri --no-doc`  
安装bundler依赖管理工具  
`gem install bundler`  

6. 安装appium/sample-code需要的gems  
进入sample-code/examples/ruby/目录，执行命令  
`bundle install`  
如果下载速度慢的话，可以执行  
`bundle config mirror.https://rubygems.org https://ruby.taobao.org`  
将rubygems.org镜像到taobao.org，使用taobao的源，然后执行  
`bundle install`  

7. 进入sample-code/examples/ruby/cucumber_android/features/目录，执行命令  
`cucumber`  
输出  
  ```bash
Feature: Version check
  Settings must display the Android version
  Scenario: Settings                     # features/settings.feature:41
    Given I click about phone            # features/step_definitions/steps.rb:24
    Then the Android version is a number # features/step_definitions/steps.rb:31
1 scenario (1 passed)
2 steps (2 passed)
0m25.277s
  ```

**troubleshooting**

1. 安装WizNote
```bash
sudo add-apt-repository ppa:wiznote-team
sudo apt-get update
sudo apt-get install wiznote
#启动
WizNote
```

2. 执行cucumber后，提示Error: The following desired capabilities are required, but were not provided: deviceName  
进入sample-code仓库的sample-code/examples/ruby/cucumber_android/features/support目录，修改appium.txt文件，添加`deviceName = "yourlovename"`

3. 默认手机系统是英文的，所以cucumber的step_definitions中的step.rb需要更新为对应的中文