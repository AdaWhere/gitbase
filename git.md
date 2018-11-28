


<!-- 自己总结 -->

# 1 创建本地仓库
$ mkdir  demo

# 2 进入本地仓库
$ cd demo

# 3 初始化本地仓库
$ git  init

# 4 克隆远程项目代码
 $ git clone git@gitlab.com:Ada/testgit.git

 git@gitlab.com:AdaWhere/testgit.git 远程仓库地址

 # 5 在远程仓库上建立分支
 $ git remote add gitlab git@gitlab.com:Ada/testgit.git

  gitlab  为远程分支的名字

# 6 拉取远程分支的 （源上的分支 master）
$ git pull gitlab master

# 7 开始提交本地仓库的代码 

  
  ## 1 创建文件  
     $ touch demo.js

  ##2 添加提交文件
      $ git add .  提交全部文件
      
      $ git add file.format 提交制定文件

  ## 3 提交文件

    $  git commit -m "提交信息"

  ## 4 push 到分支上面

   $ git push gitlab master 
   

# 8 创建分支 合并分支，删除分支

 ## 1.创建分支 git branch branchname
    切换分支 git checkout branchname 
    查看当前分支  git branch
    提交本地代码
    git add .
    git commit -m "fc"
    git push  gitlab(源名) branchname (源生的另外一个分支)

 ## 2.合并分支 

   切换回主分支 master  git checkout master
   合并分支  git merge branchname 

 ## 3.删除分支 git branch -d branchname

# 9 删除指令

  ## 1 删除 .git 文件
  ### 1  查询是否有  .git 文件
      $ ls -a
  ### 2 删除 .git 文件
      $ rm -rf .git
  ## 2 删除本地仓库
     $ rm -rf folder(本地仓库名字) 

  ## 3 删除远程关联 remote 
     git remote remove origin(源名)

 ssh 公钥场的配置
# 1. 查询本机是否有ssh
  $ cd ~/.ssh
  $ ls
  出现
  id_rsa  id_rsa.pub  known_hosts
  没有出现则没有 ssh 

# 2 ssh-keygen 创建ssh

  出现以下代码
  $ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/schacon/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/schacon/.ssh/id_rsa.
Your public key has been saved in /Users/schacon/.ssh/id_rsa.pub.
The key fingerprint is:
43:c5:5b:5f:b1:f1:50:43:ad:20:a6:92:6a:1f:9a:3a schacon@agadorlaptop.local


# 3 查询 公钥

 $ cat ~/.ssh/id_rsa.pub

 公钥
 ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAklOUpkDHrfHY17SbrmTIpNLTGK9Tjom/BWDSU
GPl+nafzlHDTYW7hdI4yZ5ew18JH4JW9jbhUFrviQzM7xlELEVf4h9lFX5QVkbPppSwg0cda3
Pbv7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8V6RjsNAQwdsdMFvSlVK/7XA
t3FaoJoAsncM1Q9x5+3V0Ww68/eIFmb1zuUFljQJKprrX88XypNDvjYNby6vw/Pb0rwert/En
mZ+AW4OZPnTPI89ZPmVMLuayrD2cE86Z/il8b+gw3r3+1nKatmIkjn2so1d01QraTlMqVSsbx
NrRFi9wrf+M7Q== schacon@agadorlaptop.local

# 5 本机每次产生的 公钥是唯一的
 
  每次替换 ，要一一对应远程的ssH 公钥

  生成ssh 首次登陆yes 

# 6删除多余的 ssh   
   添加新的ssh 
首先检查本机公钥：

$ cd ~/.ssh
如果提示：No such file or directory 说明你是第一次使用Git。如果不是第一次使用，请执行下面的操作,清理原有ssh密钥。

$ mkdir key_backup
$ cp id_rsa* key_backup
$ rm id_rsa*


生成新的公钥 

$ ssh-keygen  生成公钥
$ ssh-keygen -t rsa -C "your email url"
