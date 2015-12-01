1. 创建项目  
输入网址 http://gitlab.iduoku.cn/ 使用LDAP的登陆方式，输入自己的域账号用户名和密码登陆gitlab  
登陆后  
![webhook2](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook2.png)
点击左侧边栏的Groups链接
![webhook3](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook3.png)
选择对应的Group
![webhook4](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook4.png)
点击New Project创建一个项目，填写Project path、Description、Visibility Level  
项目创建好之后
![webhook5](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook5.png)
按照命令在本地配置git信息、创建好项目仓库，参考 svn迁移git文档 http://doc.iduoku.cn/pages/viewpage.action?pageId=17863782 将项目代码从svn迁移到gitlab上。  
配置项目  .gitignore 文件  
里面一行一个目录或者文件，标示不提交的文件或者目录  
git push操作应该需要配置ssh key  
从主页面 -> Profile Settings -> SSH Keys -> Add SSH Key
![webhook6](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook6.png)
添加完SSH Key后，将项目git push到gitlab上，查看gitlab上有更新，表明SSH Key已配置好。  
项目负责人添加项目组成员  
进入对应Group下的项目 > Members
![webhook7](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook7.png)
点击Add members，添加项目组成员，Reporter是没有merge代码权限的角色，Developer以上的用户具有merge代码的权限，请负责人合理分配。正常情况给负责review的人Developer权限，其他人给Reporter权限即可。
![webhook8](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook8.png)

2. 配置项目的web hook  
进入对应的项目，在左侧的侧边栏点击 Settings 链接
![webhook9](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook9.png)
添加URL，勾选Trigger - Push events，去掉勾选SSL verification
![webhook10](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook10.png)

3. 配置jenkins项目
在jenkins中新建一个项目，项目配置中的源码管理，选择Git，填写Repository URL和Credentials，Credentials中填写有权限读取gitlab项目的ssh key或者用户名密码。
![webhook11](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook11.png)

4. 测试gitlab Web Hook
进入项目的Settings -> Web Hooks，找到添加的Web hooks，点击hook后面的Test Hook按钮。
![webhook12](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook12.png)

5. 回到jenkins，查看项目是否自动构建