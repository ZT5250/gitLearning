![Git logo](https://raw.githubusercontent.com/ZT5250/gitLearning/master/gitlogo%402x.png)

# Git常用命令记录

## Git本地操作相关命令

 ``` git init ``` [初始化一个本地的git仓库,自己创建一个空的文件夹用来作为自己的git本地仓库]

 ``` git add <filename> ``` [添加单个文件] 
 
 ``` git add --a ``` [添加所有文件]

 ``` git status ``` [查看当前工作区中的状态]

 ``` git commit -m "提交备注信息" ``` [向自己的工作区提交修改]

 ``` git log ``` [查看提交历史]
 
 ``` git log --pretty=oneline ``` [简化log信息]
 
 ``` git log -1 ``` [查看最近一次的commit日志信息]
 
 ``` git log -p -1 ``` [查看最近一次的commit日志信息，并列出不同的内容]
 
 ``` git log --stat ``` [查看所有的commit日志信息，并列出所有文件的修改行数（不显示具体的改动内容）]
 
 ``` git log --author=test ``` [查看test推送的所有commit日志信息]
 
 ``` git log --name-only ``` [仅在提交信息后显示已修改的文件清单。]
 
 ``` git log --name-status ``` [列出commit中文件的新增、修改、删除的文件清单。]
 
 ``` git log --since=1.days ``` [当前时间之前1天的commit日志信息,也可以使用after]
 
 ``` git log --until=1.days ``` [前1天到最初的所有commit日志信息,也可以使用before]
 
 ``` git log master ^dev ``` [查看master分支有，dev分支没有的commit日志信息]
 
 ``` git log dev ^master ``` [查看dev分支有，master分支没有的commit日志信息]

 ``` git reset --hard HEAD^ ``` [回退到上一个版本]

 ``` git reset --hard <commit_id> ``` [回退到指定的版本
 
 ``` git diff HEAD -- <fillename> ``` [查看工作区(存放已经添加的文件的区域)和版本库里面最新版本的区别]
 
 ``` git blame <文件名> ``` [查看文件具体的修改历史，每次的commit id 和提交的内容]

 ``` git reflog ``` [查看自己执行的命令历史记录]
 
 ``` git checkout -- <filename> ``` [丢弃工作区的修改，让这个文件回到最近一次git commit或git add时的状态]
 
  > 这里需要注意命令中的 ``` -- ``` 如果漏写，则变成了切换分支的命令，在下面有讲到
  
 ``` git checkout <commitid> <filepath> ``` [从指定commit中检出指定路径的文件]
 
 ``` git rm <filename> ``` [确定要从git仓库中删除的文件，先执行此命令，在执行git commit
 
 ``` git checkout -b dev ``` [创建dev分支，并切换到dev分支上]
 
 > 这里相当于执行了 ``` git branch dev ``` 和 ``` git checkout dev ``` 两条命令
 
 ``` git branch ``` [查看当前分支]
 
 ``` git checkout <分支名称> ``` [切换分支]
 
 ``` git merge <分支名称> ``` [将指定的分支内容合并到当前分支]
 
 ``` git branch -d <分支名称> ``` [删除指定分支]
 
 > 多分支协作有很多好处，一般自己的master分支是与服务器仓库保持一致的,并且要保证是稳定的，是最后要push的，平时自己开发可以创建一个dev分支，功能都开发完毕测试通过之后，
 > 再将dev分支的内容合并到master分支上；平时在bug修改的时候，也可以通过不同的bug创建不同的分支来工作，这样代码互不影响，都能保证正常运行，修改完毕之
 > 后，将相应的bug分支合并到master分支上，并将那个bug分支删除即可，这样能时刻保证master中的代码是能正常运行的代码
 
 ``` git log --graph ``` [可以查看分支合并图]
 
 > stash可以有多个，后面加上具体的stash名称可以对指定的stash进行操作，通过 ``` git stash list ``` 可以查看所有的stash
 
 ``` git stash ``` [存储工作区的所有内容，临时有任务需要处理，但是暂时不想提交的文件，可以先存储起来(内容没有提交)，然后切换到其他分支进行处理]
 
 ``` git stash list ``` [查看存储的工作现场,可以有多个]
 
``` git stash apply ``` [恢复存储的工作现场（注：之前存储在stash中的工作现场不会被删除，需要在执行另外的命令吧stash中的内容删除）]

``` git stash drop ``` [删除stash中存储的内容]

``` git stash pop ``` [恢复工作区并删除之前存储的stash中的内容]
 	
 	
 
## Git远程操作相关命令

 > 这里需要注意，要现将自己的ssh公钥添加到github或者码云上，然后才能执行与远程仓库相关的操作
 > 包括从远程仓库clone项目下来也需要添加ssh公钥，具体的生成的命令可以使用，``` ssh-keygen -t rsa -C "youremail@example.com" ```
 
 ``` git remote add <别名> <远程仓库地址> ``` [添加远程仓库，一般远程仓库的别名都使用origin，也可以指定其他的名称，方便添加多个远程仓库]
 
 ``` git push -u <远程仓库别名> <本地当前分支（一般就是master分支）> ``` [第一次向空的远程仓库push代码时候，使用该命令，可以把本地分支内容推送到远程仓库，并且将本地分支与远程master分支关联]
 
 ``` git push <远程仓库别名> master ``` [以后push代码，就可以直接使用该命令，将本地master分支的内容推送到远程仓库中]
 
 ``` git clone <远程仓库地址> ``` [从远程仓库复制项目代码到本地，想要学习开源项目的，可以通过该命令复制自己喜欢的项目到本地，查看源码并学习源码]
 
 ``` git pull <远程仓库别名> <远程分枝> ``` [从远程仓库拉取指定分支最新的代码到当前分支]
 
 ``` git pull <远程仓库别名> <远程分枝>:<本地分支名称> ``` [从远程仓库拉取指定分支最新的代码到指定分支]
 
 > 以下两条命令与git pull有相同的作用，但是更安全，可以自己选择是否要合并到本地分支<br>
 > ``` git fetch <远程仓库别名> <远程分支>:<本地分支名称> ``` [获取远程指定分支最新的代码库并在本地创建一个分支]<br>
 > ``` git merge <本地分支> ``` [将创建的分支与当前分支合并，可以先执行 ``` git diff <本地分支> ``` 查看具体的修改，自己决定是否需要合并分支]
 
 ## Git常用别名配置
 ``` git config --global alias.st status ``` [为 ``` git status ``` 配置别名，以后就可以直接使用``` git st ``` 来达到同样的效果]
 
 ``` git config --global alias.co checkout ``` [为 ``` git checkout ``` 配置别名，以后就可以直接使用``` git co ``` 来达到同样的效果]
 
 ``` git config --global alias.ci commit ``` [为 ``` git commit ``` 配置别名，以后就可以直接使用``` git ci ``` 来达到同样的效果]
 
 ``` git config --global alias.br branch ``` [为 ``` git branch ``` 配置别名，以后就可以直接使用``` git br ``` 来达到同样的效果]
 
 ``` git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit" ```
 
 [格式化处理一下日志显示，让查看日志更清晰直观]
 
 ![格式化之后的日志](https://www.liaoxuefeng.com/files/attachments/00138492662982594cbd1a942114472aeeb5f0a502faed1000/0)

 
 > 引用 [廖雪峰老师的图片](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375234012342f90be1fc4d81446c967bbdc19e7c03d3000)

 