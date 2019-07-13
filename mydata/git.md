Git使用总结
1.下载代码到本地
1.1指定存储文件路径
1.运行git-bash.exe

2.指定盘符：cd f:work

1.2下载代码
命令：$ git clone <版本库的网址> <本地目录名>

版本库的网址：若有用户名、密码，则：http//:用户名@版本库的网址

本地目录名：若不填写此属性则用远程代码仓库名为目录名称；如果填写则用填写名称为本地目录名称。

 

2.更新远程代码
命令: git pull -u origin master:master。

这里的master是我的分支的名称，在使用的时候要换成你自己分支的名称；也可直接 git pull 更新默认分支

3.提交本地代码
3.1查看本地代码状态
命令：git status

状态：

1.已暂存 （changes to be committed）

所列的内容是在Index中的内容，commit之后进入Git Directory

 

new file //表示新建文件

modified //表示修改文件

deleted //表示删除文件

 

2.已修改 （changed but not updated）

  所列的内容是在Working Directory中的内容，add之后将进入Index。

 

modified //表示修改文件

deleted //表示删除文件

 3.未跟踪 （untracked files）

所列的内容是尚未被Git跟踪的内容，add之后进入Index

 

3.2将文件添加至Index暂存
git add命令主要用于把我们要提交的文件的信息添加到索引库中。当我们使用git commit时，git将依据索引库中的内容来进行文件的提交。

git add . ：他会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包 括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

git add -u ：他仅监控已经被add的文件（即tracked file），他会将被修改的文件提交到暂 存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

git add -A ：是上面两个功能的合集（git add --all的缩写）

3.3提交已暂存的文件
1. git commit -m "备注说明"

这个命令表示添加备注

2. git push -u origin master:master 

提交到Git仓库。这里master为我自己的分支的名称，实际应用中，你要改成自己的分支的名称

