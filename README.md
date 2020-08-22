# learn-git
# 更改文件名
git add filename
git rm oldfilename
git commit -m "update filename"
git status
git log

# 12. 分离头指针情况下的注意事项
1. git branch
2. git log --graph
3. git checkout commitID
4. git branch
5. vim README.MD 并将12标题下的所有内容导入到其中，保存.
6. git commit -am "Test for no head"
7. git checkout dev 基于dev分支去fix bug
8. git branch nohead commitID
9. git log --all 

# 13. 删除不需要分支
1. git branch -av
2. git branch -d 分支名称 , 如 git branch -d nohead
3. git branch -D 分支名称 , 强制删除该分支

-d and -D的不同之处在于，-d需要把当前的需要提交到分支的代码合并到不删除的分支上,才能删除该分支; -D是强制删除该分支.

# 15.怎么修改最新commit的message
1. git branch -av
2. git log -3
3. git commit --remend 进入交互界面,输入更改信息
 
# 16. 怎么修改老旧commit的message
1. git log -3 查找自己分支的任何历史信息，找到commitID
2. git rebase -i commitID 这个时候就是再进行变基了,会有两个交互提醒,根据提示的信息和自己的需求进行相应的更改.
3. 交互完成之后,提示Successfully,即ok. 

# 19. 怎么比较暂存区和HEAD所含文件的差异
1. git add 文件名  将文件放到暂存区
2. git status 	查看当前git的状态
3. git diff --cached 查看缓存区与当前HEAD的区别

# 20. 比较暂存区和工作区所含文件的差异
1. vim README.md
2. git add README.md
3. git diff    比较暂存区和工作区所有文件的区别
4. git diff --README.md  比较暂存区和工作区README.md文件的区别
5. git status

# 21. 暂存区恢复HEAD成一样
1. git reset HEAD	将缓存区恢复成和HEAD指向一样的模样
2. git diff --cached	比较缓存区和工作区的差异
3. git diff		比较缓存区和HEAD的差异

# 22. 工作区恢复成暂存区一样的内容
1. git status
2. git checkout -- README.md	指定README.md恢复成和暂存区一样
3. git diff 			比较暂存区和工作区的区别

# 23. 消除最近的几次提交
1. git log --graph
2. git reset --hard commitID    HEAD、暂存区和工作区恢复成该commitID

# 24. 比较不同提交的指定文件的差异
1. git log --graph
2. git diff commitID1 commitID2  比较两次提交的差异
3. git diff dev master		 比较dev和master分支的差异
4. git diff dev master -- README.md  比较两个分支README.md文件的差异

# 25. 正确删除文件的方法
1. git branch
2. git rm test2.md(filename)  	删除指定的文件
3. git add .
4. git commit -m "rm test2.md"
5. git push origin dev		删除远程仓库中的test2.md文件

# 26. 开发中临时加塞了紧急任务怎么处理
1. git branch		查看当前所在分支
2. git stash		保存当前工作区到一个目录
3. git status		查看当前暂存区的状态 
4. git stash apply	恢复保存到堆栈的内容,在stash内部保存不会丢失,使用git stash list依然存在
5. git stash pop	恢复保存到堆栈中的内容,在stash内部将不会保存,使用git stash list不会存在,所以该命令与上命令要区分.
6. git status		查看状态和查看文件是否已经恢复.

# 27. 指定不要git管理的文件
1. github.com/github/gitignore   地址参考git忽略管理的配置

# 28. 如何将Git仓库备份到本地
1. 常用的传输协议
	|常用协议|语法格式|说明|
	| ----	| ----  | ----|
	|本地协议(1)| /path/to/repo.git	| 哑协议|
	|本地协议(2)| file:///path/to/repo.git|智能协议|
	|http/https协议| http(s)://git-server.com:port/path/to/repo.git|平时接触到的都是智能协议|
	|ssh协议| user@git-server.com:path/to/repo.git|工作中最常用的智能协议|

2. 哑协议与智能协议
直观区别: 哑协议传输进度不可见;智能协议传输可见.
传输速度: 智能协议比哑协议传输速度快.
