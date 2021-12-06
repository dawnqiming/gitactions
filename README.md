# gitactions
常用命令

GitLab代码提交总结

Git知识储备：
github教程：https://www.w3cschool.cn/github/github-nzu62q6u.html
常用git命令清单：http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html、
git远程操作命令：http://www.ruanyifeng.com/blog/2014/06/git_remote.html
git命令: https://blog.51cto.com/steed/2440587

代码库采用Fork方式创建分支和代码提交
Fork 是对一个仓库的克隆。克隆一个仓库允许你自由试验各种改变，而不影响原始的项目

一、	初次拉取代码时，使用Fork功能先克隆代码库到自己空间，操作如图：
 
二、	使用git clone命令下载自己空间的远程代码库
命令如下：
git clone ssh://*****.git
 
注意是自己空间的代码库
使用 git branch –a 显示所有分支，绿色的为当前所在分支，我们当前使用的分支是master
如果需要切换分支 使用命令：git checkout Br_release_10.1.2.300
 
三、	添加主空间的远程主机地址
git remote add upstream ssh://*****.git
git remote –v 会显示出所有远端主机地址
	 
四、	合并主空间代码分支到本地分支
先使用git fetch命令更新远程代码，再使用git merge命令合并远程分支到本地分支
具体操作如下图：

五、	提交代码
1、git add命令 提交到暂存区
2、git commit命令 提交到本地仓库
commit命令提交时，描述信息格式必须按下面格式样式写  
第一种格式：需求开发提交
git commit -m "[TicketNo:] AR000EMO17
[Description:] 导航位分配异常KRI风险量化模型支撑需求
[Binary Source:]NA"
    
备注：TicketNo是需求编号
第二种格式：DTS问题单提交代码
git commit -m " [TicketNo:]DTS2020081412760 
[Description:]1,修改DTS2020081412760 
[Binary Source:]NA"

3 提交代码到远程主机
  git push origin master

六、	合并代码到主空间代码库，即提交Merge Request
按如下步骤提交Merge Request请求
1、进入主代码仓，点击fork进入自己的空间代码仓库
2、点击左侧 Merge Request，再点击绿色按钮 New Merge Request，有时候要等一会，不一定能马上弹出来，你刚刚push的记录
3 、如下图填写相关人员信息，点绿色按钮提交

【问题一】主干创建了新分支，本地怎么同步创建新分支？

使用下面的命令进行同步远程新分支到本地
git fetch upstream master:master_100

git fetch命令详解：https://www.jianshu.com/p/a5c4d2f99807

【问题二】GIT修改提交备注后无法推送远端解决方法
http://wiki.inhuawei.com/pages/viewpage.action?pageId=140322376


4 多个commit合并成一个
git log 查询提交的记录  3b2bdf1e0448ece5f7ee2b0578dea4cfbfe3f72c
git reset --soft 3b2bdf1e0448ece5f7ee2b0578dea4cfbfe3f72c
$ git fetch top   向本地同步远程代码
$ git merge top/Br_feature_12.0.1   ..分支合并到远程
$ git push -f origin Br_feature_12.0.1   强制推送到本地仓库


