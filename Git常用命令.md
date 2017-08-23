# 初始化一个本地的git仓库
### 自己创建一个空的文件夹用来作为自己的git本地仓库
## git init

# 向自己的工作区中添加修改
### 添加单个文件
## git add <filename>
### 添加所有文件
## git add --a

# 查看当前工作区中的状态
## git status

# 向自己的工作区提交修改
## git commit -m "提交备注信息"

# 查看提交历史
## git log
### 简化log信息
## git log --pretty=oneline

# 回退到指定版本（commit或者push）
### 回退到上一个版本
## git reset --hard HEAD^
### 回退到指定的版本
## git reset --hard <commit_id>

# 查看自己执行的命令历史记录
## git reflog
