<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [注意：本文档中的命令没有经过真实环境测试，只做示范，请认真核对再执行。](#)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 注意：本文档中的命令没有经过真实环境测试，只做示范，请认真核对再执行。

**1. 拷贝jenkins程序**  
将192.168.1.109服务器上的/home/work/webserver/jenkins目录打包拷贝到新的服务器上/home/work/webserver/jenkins下  
```bash
# 在老机器上执行打包命令
cd /home/work/webserver/jenkins
tar -cvf jenkins.tar *
# 拷贝之前，新机器上需要创建对应的目录 mkdir -p /home/work/webserver/jenkins
scp jenkins.tar work@192.168.1.xxx:/home/work/webserver/jenkins
# 如果是开放云，请使用开放云的登陆方式
ssh work@192.168.1.xxx
cd /home/work/webserver/jenkins
tar -xvf jenkins.tar
```

**2. 拷贝jenkins备份文件**  
将192.168.1.109服务器上的/home/work/.jenkins目录打包压缩拷贝到新的服务器的/home/work目录下，解压解包
```bash
# 在老机器上执行打包压缩命令
cd /home/work
tar -zcvf jenkins.tar.gz ./.jenkins
# 拷贝到新机器的/home/work目录下解包解压缩
scp jenkins.tar.gz work@192.168.1.xxx:/home/work
# 如果是开放云，请使用开放云的登陆方式
ssh work@192.168.1.xxx
cd /home/work
tar -zxvf jenkins.tar.gz
```

**3. 运行jenkins启动脚本**  
进入/home/work/webserver/jenkins目录，执行命令 `./jenkins.sh start`
```bash
cd /home/work/webserver/jenkins
# 保证环境中已经安装java. yum install java-1.7.0-openjdk.x86_64
./jenkins.sh start
```

**4. 做端口转发port forward**
```bash
sudo su - root
iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8999
```

**5. 找op协助更换域名指向新的ip地址**  
jenkins.iduoku.cn   192.168.1.xxx

