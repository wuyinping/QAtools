**1. 在新环境安装ruby2.0，直接编译安装或者通过ruby版本管理工具rvm安装**
```bash
# 安装rvm
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -sSL https://get.rvm.io | bash -s stable
# 通过rvm安装ruby 2.0，需要先通过root用户安装ruby依赖的系统库
rvm install 2.0.0
```

**2. 安装git**
```bash
# 用root安装git
yum install git
```

**3. 从gitlab上克隆仓库到服务器上**
```bash
# 切换到合适的目录
cd /home/work/webserver
git clone git@gitlab.iduoku.cn:QA/apiTest.git
```

**4. 安装PostgreSQL数据库和对应的开发包**
```bash
# 安装PostgreSQL数据库
yum install postgresql-server
yum install postgresql-devel
# 初始化数据库
service postgresql initdb
# 配置本地用户免密码信任
vim /var/lib/pgsql/data/pg_hba.conf
# update the `local all all ident` to `local all  all  trust`
# 启动postgreSQL
service postgresql start
```

**5. 安装项目依赖的gem包**
```bash
cd /home/work/webserver/apiTest
# 配置源为淘宝的gem源
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem sources -l
# 安装gem包依赖管理工具bundler
gem install bundler
# 安装依赖的gem包
bundle install
```

**6. 创建数据库**
```bash
# 创建数据库
rake db:create
# 数据库迁移
rake db:migrate
```

**7. 备份还原数据库**
```bash
# 在老机器上备份数据库
pg_dump -Upostgres xin_test_dev > xin_test_dev.sql
# scp到新机器上
cd /home/work/webserver/backup
scp work@192.168.1.xxx:~/webserver/backup/xin_test_dev.sql /home/work/webserver/backup
# 删除数据库
dropdb -Upostgres xin_test_dev
# 创建数据库
createdb -Upostgres xin_test_dev
# 执行还原操作
psql -Upostgres xin_test_dev < ./xin_test_dev.sql
```

**8. 安装javascript运行环境，nodejs**
```bash
# 安装nodejs
yum install nodejs
```

**9. 配置端口转移port forward**
``bash
iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 3001
```

**10. 启动服务**
```bash
cd /home/work/webserver/apiTest/script
sh start.sh
```

**11. 找op协助更换域名指向新的ip地址**
apitest.iduoku.cn   192.168.1.xxx

