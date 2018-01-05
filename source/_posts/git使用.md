---
title: git的基本使用
date: 2018-1-1 22:29:32
categories:
tags:
     - 杂项
---


今天发现一个挺好的代码托管平台  coding，就借此说一下git命令的基本使用，另外以下叙述同样也适用于github。

我是在ubuntu下使用的，window平台安装了git方法一样。
---




#### 1.生成ssh

  打开terminal，输入“ssh-keygen -t rsa -c "xxxxxxxx@xxx.com(自己注册时绑定的邮箱)"”命令


  继续输入"cat  ~/.ssh/id_rsa.pub"命令，查看ssh公钥

 <!-- more -->

####   2.获取ssh

  将命令行中的ssh按照格式粘贴到项目中（账户->ssh公钥）


  找到拓展名为pub的文件，以记事本方式打开它，将内容粘贴到网页中的SSH-RSA公钥内容对话框中，后点击添加按钮。

  ssh应该配置成功。
   
  运行ssh -T git@git.coding.net   添加到信任host列表
####   3.创建本地仓库

  在本地创建一个文件夹，使用mkdir命令，作为你上传代码的本地仓库，接下来就要把这个仓库与coding服务器端进行配置

  首先要初始化本地仓库，输入"git init"命令


  接下来克隆远程仓库，输入"git clone http://xxxxxxxx"命令，命令中的url(链接)寻找方式如下



  将这个url粘贴到命令中，进行远程仓库的克隆



####   4.代码推送

  这时候，本地仓库的配置就完成了，接下来要查看一下本地仓库的状态，一检查配置是否成功，进而进行代码的推送

  输入命令"git status"



  比如新建xuchao.txt文件，
  
``` bash
echo "hello" > xuchao.txt
```

  输入git status命令后，会发现以红色字体打印出来的“gg.txt”，说明该文件存在于本地仓库，但并未推送到云端

  输入"git add 文件名"命令

  输入"git commit -m "代码备注" "命令提交

  然后输入"git push origin master"命令推送到云端，origin是库名称，master是分枝。

  因为我们之前没有使用"git config"命令，所以推送代码时会要求输入用户名和密码，这里用config命令设置。

  一切结束后，输入"git status"查看本地代码状态，会用绿字显示，表示上传成功，进入coding.net的项目主页，你会发现自己在本地推送的代码已经出现在项目中。
  
  以上就是基本配置全部内容
  
####   知识拓展

git常用命令

创建版本库

```
$ git clone <url>                  #克隆远程版本库
$ git init                         #初始化本地版本库
```

修改和提交

```
$ git status                       #查看状态
$ git diff                         #查看变更内容
$ git add .                        #跟踪所有改动过的文件
$ git add <file>                   #跟踪指定的文件
$ git mv <old><new>                #文件改名
$ git rm<file>                     #删除文件
$ git rm --cached<file>            #停止跟踪文件但不删除
$ git commit -m "commit messages"  #提交所有更新过的文件
$ git commit --amend               #修改最后一次改动
```

查看提交历史

```
$ git log                    #查看提交历史
$ git log -p <file>          #查看指定文件的提交历史
$ git blame <file>           #以列表方式查看指定文件的提交历史
```
撤销

```
$ git reset --hard HEAD      #撤销工作目录中所有未提交文件的修改内容
$ git checkout HEAD <file>   #撤销指定的未提交文件的修改内容
$ git revert <commit>        #撤销指定的提交
$ git log --before="1 days"  #退回到之前1天的版本
```
分支和标签

```
$ git branch                   #显示所有本地分支
$ git checkout <branch/tag>    #切换到指定分支和标签
$ git branch <new-branch>      #创建新分支
$ git branch -d <branch>       #删除本地分支
$ git tag                      #列出所有本地标签
$ git tag <tagname>            #基于最新提交创建标签
$ git tag -d <tagname>         #删除标签
```
合并和衍生

```
$ git merge <branch>        #合并指定分支到当前分支
$ git rebase <branch>       #衍合指定分支到当前分支
```

远程操作

```
$ git remote -v                   #查看远程版本库信息
$ git remote show <remote>        #查看指定远程版本库信息
$ git remote add <remote> <url>   #添加远程版本库
$ git fetch <remote>              #从远程库获取代码
$ git pull <remote> <branch>      #下载代码及快速合并
$ git push <remote> <branch>      #上传代码及快速合并
$ git push <remote> :<branch/tag-name>  #删除远程分支或标签
$ git push --tags                       #上传所有标签
```


