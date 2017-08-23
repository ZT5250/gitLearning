# Git常用命令记录

 ```git init``` [初始化一个本地的git仓库,自己创建一个空的文件夹用来作为自己的git本地仓库]

 ```git add <filename>``` [添加单个文件] 
 
 ```git add --a``` [添加所有文件]

 ```git status``` [查看当前工作区中的状态]

 ```git commit -m "提交备注信息"``` [向自己的工作区提交修改]

 ```git log``` [查看提交历史]
 
 ```git log --pretty=oneline``` [简化log信息]

 ```git reset --hard HEAD^``` [回退到上一个版本]

 ```git reset --hard <commit_id>``` [回退到指定的版本
 
 ```git diff HEAD -- <fillename>``` [查看工作区(存放已经添加的文件的区域)和版本库里面最新版本的区别]

 ```git reflog``` [查看自己执行的命令历史记录]
 
 