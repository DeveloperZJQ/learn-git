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
