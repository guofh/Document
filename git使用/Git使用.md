#为什么使用Git
自由，没有什么比自由更能让人向往。想象着在一个海岛，或是一片竹林里，没有网络，离开了嘈杂与吵闹。一杯龙井茶，在大自然的陪伴下，完成自己的项目。代码修改，提交，分支管理...这一切，只需要Git，就足够了。

#分布式管理工具
传统的集中式管理工具如SVN，clearcase需要一个中央版本库，所有人干活都需要连接网络然后从服务器下载代码，修改后再去提交到中央服务器。而分布式管理工具是每个人都有一个完整的版本库，自己在自己的版本库中修改提交，而这一切是不需要网络的。虽然大部分时候使用Git也需要一个服务器，但这个服务器的概念不同于集中式版本管理工具的服务器概念，它只是大家为了提交合并代码方便用的，即使没有这个服务器，大家也可以互相提交代码给对方，只不过会相对麻烦一点。所以大家约定俗成找一台机器做服务器，可以把它想象成是一个什么都不做的队友，他只是被动接收大家的代码。

#安装Git
*	linux下安装
Debian或者Ubuntu可以通过`sudo apt-get install git`命令来安装。其他版本linux可以通过源码安装。Git官网下载源码，解压后输入`./config`，`make`，`sudo make install`命令进行安装即可。

*	windows下安装
下载msysgit安装即可，安装成功后会看到Git bash应用，是一个命令行窗口。

*	MacOSX下安装
在Xcode中安装Git:选择菜单“Xcode”->“Preferences”，在弹出窗口中找到“Downloads”，选择“Command Line Tools”，点“Install”就可以完成安装了。

#Git常用命令
1.	`clone`。用法：`git clone https://github.com/guofh/xxx.git` 从远程仓库克隆一份到本地文件夹。除了https还可以使用SSH协议，格式为`git clone git@github.com:guofh/xx.git`  

2.	`init`。用法：`git init`这条命令执行后会在本地建立一个新的本地仓库。

3.	`add`。用法：`git add xxx.c`命令执行后会在本地仓库添加xxx.c文件。除了添加单个文件，还可以添加多个文件，如：`git add xxx.c aaa.c aaa.h`会添加多个文件到本地仓库。  

4.	`commit`。用法：`git commit -m "commit file"`会将新的修改内容提交到本地仓库。`-m`后面是本次提交的日志说明，方便以后查看做了哪些修改。

5.	`status`。用法：`git status`。该命令会显示当前仓库状态，比如那些文件做了修改，哪些文件还没有提交等。

6.	`diff`。用法：`git diff xxx.c`。改命令会显示xxx.c做了哪些修改。

7.	`log`。用法：`git log`。该命令会查看所有提交日志。

8.	`reflog`。用法：`git reflog`。改命令会显示历史操作记录。

9.	`reset`。用法：`git reset --hard commit_id`。该命令会将`HEAD`指针指向commit_id这个版本，实现版本跳转。除了版本跳转，还可以使用`git reset --head xxx.c`命令实现暂缓区修改退回到工作区。

10.	`checkout`。用法：`git checkout -- xxx.c`将工作区的xxx.c文件撤销回和版本库或者暂缓区内容一致。第二种是切换分支的用法`git checkout master`命令执行后，当前分支切换到master分支。使用`git checkout -b job origin/job`将会在本地建立job分支并和远程job分支同步。

11.	`rm`。用法：`git rm xxx.c`将xxx.c文件从版本库中删除，之后使用`git commit`将删除动作提交。

12.	`branch`。用法：`git branch job`，命令执行后会创建一个job分支。也可以使用`git checkout -b job`命令，表示新建一个job分支并切换到该分支上。使用`git branch`查看所有分支和当前在哪个分支上。使用`git branch -d job`将删除job分支。`git branch --set-upstream job origin/job`建立本地分支和远程分支的关联。

13.	`merge`。用法：`git merge job`，命令执行后会将job分支内容合并到当前分支上。

14.	`tag`。用法：`git tag v1.0`创建一个新标签，默认在HEAD上，也可以指定commit_id，如`git tag v1.0 12345`在12345这次提交上打标签。使用`git tag`可以查看所有标签。使用`git tag -d v1.0`可以删除v1.0标签。

15.	`push`。用法：`git push origin job`会将本地job分支内容推送到远程服务器。

16.	`pull`。用法：`git pull`抓取远程库最新内容。

