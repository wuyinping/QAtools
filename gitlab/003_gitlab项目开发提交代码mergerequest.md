<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [1. 项目开发](#1)
- [2. 提交代码](#2)
- [3. merge request](#3-merge-request)
- [4. Merge Requests list](#4-merge-requests-list)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

以下步骤是在项目负责人创建完对应项目之后。创建项目请参考[002_gitlab创建项目和配置webhook](http://gitlab.iduoku.cn/QA/firstStation/blob/master/gitlab/002_gitlab%E5%88%9B%E5%BB%BA%E9%A1%B9%E7%9B%AE%E5%92%8C%E9%85%8D%E7%BD%AEwebhook.md)
#### 1. 项目开发
  * 查找项目  
    登陆gitlab http://gitlab.iduoku.cn/ 后选择左边栏的Projects -> Explore Projects -> 排序选Most stars -> 选择对应Groups下的项目
    ![merge1](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge1.png)
  * 创建对应的开发版本分支  
    如本次项目开发的版本号为V1.1.1，则在项目的页面，点击创建分支的按钮
    ![merge_temp1](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp1.png)
    新分支取名为V1.1.1，从master 中创建，点击创建按钮
    ![merge_temp2](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp2.png)
  * 本地checkout 代码进行开发  
    到自己的机器上用git将项目git clone下来  
    clone仓库到本地
    ![merge_temp3](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp3.png)
    master不允许push，我们需要在分支上开发  
    假如分支为V1.1.1 ，项目clone到本地后，使用git checkout -b V1.1.1 origin/V1.1.1 创建本地分支，并切换到分支上（此时本地分支会关联到远程仓库的分支上）
    ![merge_temp4](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp4.png)
  * 分支开发  
    把远程分支V1.1.1的最新代码拉取到本地，然后 merge到本地分支上，保证本地的代码版本与远程是一致的，这时候就可以进行开发了  
    **PS：请使用`git merge --no-ff`命令**
    ![merge_temp5](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp5.png)
    用git开发的流程如下：
    
        ```bash
      git fetch    # 经常从远程 拉取最新代码
      git merge --no-ff  origin/分支    # 然后 merge 分支最新代码到 本地的分支
        ```
    执行merge 可能会出现冲突，此时需要对冲突文件进行修改，使用git status可以查看冲突的文件列表
    ![merge_temp6](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge_temp6.png)
    修改完冲突文件后，重新提交然后push即可
    
#### 2. 提交代码  
    改动代码，实现需求
    
    ```bash
    git add    # 将改动加入index
    git commit    # 将改动提交到本地git仓库
    git push    # 将改动push到远端仓库
    ```
    ![merge6](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge6.png)
    
#### 3. merge request  
在本地git push完成之后  
登陆gitlab，选择对应的Project -> Merge Requests -> New Merge Request  
Source branch 选择改动的分支，点击按钮 Compare branches
![merge7](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge7.png)
在New merge request填写Title、Description(支持markdown标记语言)、Assign to(分配给相关负责人review)，点击提交按钮
![merge8](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge8.png)

#### 4. Merge Requests list  
提交完merge request之后，对应的项目负责人会收到邮件通知，在对应的项目 -> Merge Requests 页面会列出所有提交的请求
![merge9](http://gitlab.iduoku.cn/QA/firstStation/raw/master/article-img/gitlab/merge9.png)