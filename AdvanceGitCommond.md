# Git 高级命令记录

## 重写commit历史

### 将提交应用到最后一次commit中

 ``` git commit --amend ``` [ 有时候做了一个小的更改，不想单独弄出来一个commit，那就可以使用此命令，直接将当前这一次commit提交到上一次commit中 ]
 
### 整理本地的commit（未push的commit）

 ``` git rebase -i HEAD~3 ``` [其中 ``` -i ``` 表示启用交互模式，``` ~3 ``` 表示最近的三次commit ]
 
 运行过上述命令之后会出现如下所示的内容，要保证第一个是pick，即采用这一次commit的内容，详细介绍请参照官网，或者阅读下方的说明，这里仅做一次命令的记录，
 pick表示使用本次commit，squash或者s表示不使用本次提交
 
 ```
	pick f7f3f6d changed my name a bit
	pick 310154e updated README formatting and added blame
	pick a5f4a0d added cat-file

	# Rebase 710f0f8..a5f4a0d onto 710f0f8
	#
	# Commands:
	#  p, pick = use commit
	#  r, reword = use commit, but edit the commit message
	#  e, edit = use commit, but stop for amending
	#  s, squash = use commit, but meld into previous commit
	#  f, fixup = like "squash", but discard this commit's log message
	#  x, exec = run command (the rest of the line) using shell
	#
	# These lines can be re-ordered; they are executed from top to bottom.
	#
	# If you remove a line here THAT COMMIT WILL BE LOST.
	#
	# However, if you remove everything, the rebase will be aborted.
	#
	# Note that empty commits are commented out
 ```
 
 经过整理之后，保存并推出编辑模式，会弹出合并后的提示信息，再保存推出，就会将所有的commit合并成一个或多个commit，可以通过 ``` git log ``` 查看整理后的commit
 
### 调试功能
 ``` git bisect start ``` [开始进行调试]
 
 ``` git bisect bad ``` [告诉git当前commit是bad]
 
 ``` git bisect good commitid ``` [在告诉git哪一个commit是good，然后git就会在当前的commit和good commit之间进行二分查找，不停的切换到对应的commit上，本地进行调试通过之后，通过执行 ``` git bisect good/bad ```告诉git当前测试的commit是好的还是坏的，最终git会找出第一次出现错误的commit，然后我们就可以定位出现问题的commit，并进行相应的错误检查]
 
 ``` git bisect reset ``` [调试完毕之后，在执行一遍此命令，会将你带回到正常的状态，否则会停留在一个奇怪的分支中]
 