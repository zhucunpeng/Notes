# Git
## shell的分类
- 图形界面shell:通过提供友好的可视化界面
- 命令行shell：通过键盘输入特定命令的方式，调用相应的应用程序

## bush
Linux默认使用bash
### bush命令格式
    + 命令[-options][参数]
    + 查看帮助:命令 --help
### bash常见命令
- pwd (Print Working Directory) 查看当前目录
- cd (Change Directory) 切换目录，如 cd /etc
- ls (List) 查看当前目录下内容，如 ls -al
- mkdir (Make Directory) 创建目录，如 mkdir blog
- touch 创建文件，如 touch index.html
- cat 查看文件全部内容，如 cat index.html
- more/less 查看文件，如more /etc/passwd、less /etc/passwd
- rm (remove) 删除文件，如 rm index.html、rm -rf  blog
- rmdir (Remove Directory) 删除文件夹，只能删除空文件夹，不常用
- mv (move) 移动文件或重命名，如 mv index.html ./demo/index.html
- cp (copy) 复制文件，cp index.html ./demo/index.html
- head 查看文件前几行，如 head -5 index.html
- tail 查看文件后几行 –n –f，如 tail index.html、tail -f -n 5 index.html 
- tab 自动补全，连按两次会将所有匹配内容显示出来
- history 查看操作历史
- > 和 >>重定向，如echo hello world! > README.md，>覆盖 >>追加
- wget 下载，如wget https://nodejs.org/dist/v4.4.0/node-v4.4.0.tar.gz
- tar 解压缩，如tar zxvf node-v4.4.0.tar.gz
- curl 网络请求，如curl http://www.baidu.com
- whoami 查看当前用户
- | 管道符可以将多个命令连接使用，上一次（命令）的执行结果当成下一次（命令）的参数。
- grep 匹配内容，一般结合管道符使用

## vi编辑器
### 三种模式
- 命令模式
- 插入模式
- 底行模式

### 使用Vi编辑器
- 打开/创建文件， vi 文件路径
- 底行模式 :w保存，:w filenme另存为
- 底行模式 :q退出
- 底行模式 :wq保存并退出
- 底行模式 :e! 撤销更改，返回到上一次保存的状态
- 底行模式 :q! 不保存强制退出
- 底行模式 :set nu 设置行号
- 命令模式 ZZ（大写）保存并退出
- 命令模式 u辙销操作，可多次使用
- 命令模式 dd删除当前行
- 命令模式 yy复制当前行
- 命令模式 p 粘贴内容
- 命令模式 ctrl+f向前翻页
- 命令模式 ctrl+b向后翻页
- 命令模式 i进入编辑模式，当前光标处插入
- 命令模式 a进入编辑模式，当前光标后插入
- 命令模式 A进入编辑模式，光标移动到行尾
- 命令模式 o进入编辑模式，当前行下面插入新行
- 命令模式 O进入编辑模式，当前行上面插入新行

### SSH是一种网络协议，用于计算机之间的加密登录
- 格式:ssh user@host
    + user 代表真实存在的用户host代表要登录的远程计算机
- 加密技术:对称性加密和非对称加密(ssh属于后者)
    + 对称加密算法是在加密和解密时使用的是同一个密钥
    + 非对称加密算法需要两个密钥来进行加密和解密，这两个密钥分别是公开密钥(public Key)和私有密钥(private key)
- 免密码登录
    + ssh-keygen-trsa 会创建公钥和密钥(默认在用户目录/.ssh目录下)
    + ssh-copy-id user@host添加到对应远程主机的用户目录/.ssh目录下
    + 也可以登录远程主机进入到用户目录/.ssh目录下手动创建authorized_key文件，并将自己的公钥粘入该文件

## 版本控制
- 本地版本控制系统
- 集中式版本控制系统(SVN)
- 分布式版本控制系统(Git)

### Git工作原理
- 已提交(committed)
- 已修改(modified)
- 已暂存(staged)

## Git使用
### 配置用户
- git config --global user.name "自己的名字"
- git config --global user.email "自己的邮箱地址"
\-- global 配置当前 用户所有仓库
\-- system配置当前计算机上所有用户的所有仓库
### 初始化仓库
- git init 
    + 只是创建了一个名为.git的隐藏目录，这个目录就是存储我们历史版本的仓库 ls -al 可以查看
- git clone 仓库地址
- git status 可以检测当前仓库文件的状态
- git add 文件名/文件路径 * 或-A代表所有
- git status 可以再次查看仓库状态
- git chaeckout 文件名 回到之前的状态
- git commit -m '备注信息' 会生成一个唯一SHA值，
- git log 查看一下提交的历史
- git reset --hard SHA值 可以回到之前某一次的提交
- git branch <branchName> 创建一个名为branchName的新分支
- git branch -d <branchName> 删除一个名为branchName的旧分支
- git branch -m <oldBranchName> 将名为oldBranchName的分支名称修改为newBranchName
- git branch -m <newBranchName> 将正在工作分支名称修改为newBranchName
- git checkout <localBranchName> 切换到名为localBranchName的本地分支上
- git checkout <remoteBranchName> 切换到名为remoteBranchName的远程分支上，此时未新建分支，而是处于一个名为no
- branch的临时分支上，还需要使用git branch -b 来创建一个新分支并将该临时分支挂接到新分支上
- git checkout -b <branchName> 创建一个名为branchName的新分支，并切换到该分支上
- git merge <branchName> 将名为branchName的分支合并到当前所处在的分支上
- git pull 从服务器的仓库中获取代码，和本地代码合并
- git push 将本地代码推送到服务器的仓库中
- git push -f 强制将本地代码推送到服务器的仓库中，用来推送本地index和服务器index有矛盾的分支
- git push origin --delete <branchName> 删除名为branchName的远程分支
- git clone <userName>@<serviceAddress>:<serviceProjectDirectory/projectName> <localProjectDirectory>/ 从服务器端克隆项目到本地
- git remote add “主机名称” “远程仓库地址”添加远程主机，即给远程主机起个别名，方便使用
- git remote 可以查看已添加的远程主机
- git remote show “主机名称”可以查看远程主机的信息
- git push origin --delete 分支名称   删除远程分支
- git push origin :分支名称   删除远程分支
- git difftool 比较的是工作区和暂存的差异
- git difftool “SHA”比较与特定提交的差异
- git difftool “SHA”“SHA”比较某两次提交的差异
- git difftool 分支名称 比较与某个分支的差异





