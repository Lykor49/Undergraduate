# git基本指令

## 1. git clone
作用：把 Github 上的远程仓库完整下载到本地
示例：git clone https://github.com/Lykor49/Undergraduate.git

## 2. git status
作用：查看当前仓库有哪些文件被修改、新增或等待提交
示例：git status

## 3. git add .
作用：把当前仓库里的所有修改加入“待提交区”
示例：git add . 所有修改; git add Python/python.md 只添加一个文件

## 4. git commit -m "xxx"
作用：把已经add的修改保存成一个本地Git版本，只是存到本地Git，还没有上传到Github
示例：git commit -m "add Python basics notes"

## 5. git push
作用：把本地已经commit的版本上传到Github
示例：git push

## 6. git pull
作用：把Github上最新的内容同步到本地
示例：git pull

## 7. .gitignore
作用：告诉Git哪些文件或文件夹不要上传到Github
注意：.gitignore 不是命令，而是仓库里的一个文件

## 8. branch
作用：创建一条独立开发线，可以修改代码而不影响main主分支
- 后续学习再说

