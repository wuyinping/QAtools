1. 登录、配置gitlab setting、添加SSH KEY  
输入网址 http://gitlab.iduoku.cn/ 使用LDAP的登陆方式，输入自己的域账号用户名和密码登陆gitlab
![webhook1](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/webhook1.png)  
登陆后

2. 更新通知邮箱  
先添加邮箱，从主页面的左侧边栏 -> Profile Settings -> Emails  
![profile1](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/profile1.png)
将添加的新邮箱作为邮件通知邮箱  
从主页面的左侧边栏 -> Profile Settings -> Notifications  
将Notification email邮箱更新为 @baidu-mgame.com 结尾的邮箱。  
![profile2](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/profile2.png)

3. 配置SSH Key  
git push操作需要配置ssh key  
从主页面的左侧边栏 -> Profile Settings -> SSH Keys -> Add SSH Key  
生成key的方式：  
打开Git Bash,在弹出的Git命令行窗口中输入如下命令生成ssh key  
```bash
ssh-keygen -t rsa -C "XXXX@baidu-mgame.com"
# 一路回车，拷贝出来，命令参考
# Windows:
clip < ~/.ssh/id_rsa.pub
# Mac:
pbcopy < ~/.ssh/id_rsa.pub
# GNU/Linux (requires xclip):
xclip -sel clip < ~/.ssh/id_rsa.pub
```
![profile3](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/profile3.png)
