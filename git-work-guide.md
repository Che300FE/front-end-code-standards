团队开发中，遵循一个合理、清晰的Git使用流程，是非常重要的。否则，每个人都提交一堆杂乱无章的commit，项目很快就会变得难以协调和维护。

### 第一步：新建分支
首先，每次开发新功能，都应该新建一个单独的分支。

```
# 获取主干最新代码
$ git checkout master
$ git pull
# 新建一个开发分支myfeature
$ git checkout -b myfeature
```
### 第二步：提交分支commit
分支修改后，就可以提交commit了。

```
$ git add --all
$ git status
$ git commit --verbose
```

### 第三步：撰写提交信息
提交commit时，必须给出完整扼要的提交信息，第一行是不超过50个字的提要，然后空一行，罗列出改动原因、主要变动、以及需要注意的问题。最后，提供对应的网址（比如Bug ticket）。

### 第四步：与主干同步
分支的开发过程中，要经常与主干保持同步，同步的时候要将冲突进行合并。

```
$ git pull origin master
```
### 第五步：推送到远程仓库
合并commit后，就可以推送当前分支到远程仓库了。

```
$ git push origin myfeature 
```

### 第六步：发出Pull Request

提交到远程仓库以后，就可以发出 Pull Request到master分支，然后请求别人进行代码review，确认可以合并到master。

参考自： [Git 使用规范流程](http://blog.jobbole.com/88955/)

### 其他常用git命令

#### 1、克隆项目到本地
git clone git@gitlab.corp.qunar.com:campus2015/training2.git

#### 2、简写命令

git config --global alias.co checkout

git config --global alias.br branch

git config --global alias.ci commit

git config --global alias.st status

#### 3、git branch 创建分支

git branch : 列举本地分支

git branch -r ： 列举远程分支

git branch -a ： 列举本地和远程分支

git branch newBranch ： 新建一个分支

git branch -m | -M oldbranch newbranch ：重命名

git branch -d | -D branchname ：删除branchname分支 

git branch -d -r branchname ：删除远程branchname分支

#### 4、git reset ：Git版本恢复命令

git reset --mixed：此为默认方式，不带任何参数的git reset，即时这种方式，它回退到某个版本，只保留源码，回退commit和index信息

git reset --soft：回退到某个版本，只回退了commit的信息，不会恢复到index file一级。如果还要提交，直接commit即可

git reset --hard：彻底回退到某个版本，本地的源码也会变为上一个版本的内容

例如 git reset --hard HEAD 直接revert到最近的一次提交。

[http://www.tech126.com/git-reset/](http://www.tech126.com/git-reset/)

#### 5、删除远程分支

在git中重命名远程分支，其实就是先删除远程分支，然后重命名本地分支，再重新提交一个远程分支。

##### 1）删除远程分支：
$ git push --delete origin devel

##### 2）重命名本地分支：
git branch -m devel develop

##### 3）推送本地分支：
$ git push origin develop

http://zengrong.net/post/1746.htm

#### 6、更换远程仓库地址

1.修改命令

git remote set-url origin [url]

例如：git remote set-url origin gitlab@gitlab.chumob.com:php/hasoffer.git

2.先删后加

git remote rm origin

git remote add origin [url]
