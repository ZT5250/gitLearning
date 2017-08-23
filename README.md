# Git常用命令记录

 ``` git init ``` [初始化一个本地的git仓库,自己创建一个空的文件夹用来作为自己的git本地仓库]

 ``` git add <filename> ``` [添加单个文件] 
 
 ``` git add --a ``` [添加所有文件]

 ``` git status ``` [查看当前工作区中的状态]

 ``` git commit -m "提交备注信息" ``` [向自己的工作区提交修改]

 ``` git log ``` [查看提交历史]
 
 ``` git log --pretty=oneline ``` [简化log信息]

 ``` git reset --hard HEAD^ ``` [回退到上一个版本]

 ``` git reset --hard <commit_id> ``` [回退到指定的版本
 
 ``` git diff HEAD -- <fillename> ``` [查看工作区(存放已经添加的文件的区域)和版本库里面最新版本的区别]

 ``` git reflog ``` [查看自己执行的命令历史记录]
 
 ``` git checkout -- <filename> ``` [丢弃工作区的修改，让这个文件回到最近一次git commit或git add时的状态]
 
 ``` git rm <filename> ``` [确定要从git仓库中删除的文件，先执行此命令，在执行git commit
 
 ``` git remote add <别名> <远程仓库地址> ``` [添加远程仓库，一般远程仓库的别名都使用origin，也可以指定其他的名称，方便添加多个远程仓库]
 
 ``` git push -u <远程仓库别名> <本地当前分支（一般就是master分支）> ``` [第一次向空的远程仓库push代码时候，使用该命令，可以把本地分支内容推送到远程仓库，并且将本地分支与远程master分支关联]
 
 > 这里需要注意，要现将自己的ssh公钥添加到github或者码云上，然后才能执行与远程仓库相关的操作
 > 包括从远程仓库clone项目下来也需要添加ssh公钥，具体的生成的命令可以使用，``` ssh-keygen -t rsa -C "youremail@example.com" ```
 
 ``` git push <远程仓库别名> master ``` [以后push代码，就可以直接使用该命令，将本地master分支的内容推送到远程仓库中]
 
 ``` git clone <远程仓库地址> ``` [从远程仓库复制项目代码到本地，想要学习开源项目的，可以通过该命令复制自己喜欢的项目到本地，查看源码并学习源码]
 
 ``` git checkout -b dev ``` [创建dev分支，并切换到dev分支上]
 
 > 这里相当于执行了 ``` git branch dev ``` 和 ``` git checkout dev ``` 两条命令
 
 ``` git branch ``` [查看当前分支]
 
 ``` git checkout <分支名称> ``` [切换分支]
 
 ``` git merge <分支名称> ``` [将指定的分支内容合并到当前分支]
 
 ``` git branch -d <分支名称> ``` [删除指定分支]
 
 > 多分支协作有很多好处，一般自己的master分支是与服务器仓库保持一致的，是最后要push的，平时自己开发可以创建一个dev分支，功能都开发完毕测试通过之后，
 > 再将dev分支的内容合并到master分支上；平时在bug修改的时候，也可以通过不同的bug创建不同的分支来工作，这样代码互不影响，都能保证正常运行，修改完毕之
 > 后，将相应的bug分支合并到master分支上，并将那个bug分支删除即可，这样能时刻保证master中的代码是能正常运行的代码
 
 ``` git log --graph ``` [可以查看分支合并图]