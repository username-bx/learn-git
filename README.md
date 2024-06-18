# git 技术分享

> 序言: 今天是git技术分享,抛砖引玉 主要是大家互相学习一下.
第一部分是git的工作流程,接plant单子开始,开发,自测(联调),提测,上线.
第二部分是工作中可能使用的命令,命令的简写和区别.



## git 工作流

### 1. 查看远程分支,本地分支,全部分支
```shell
git branch -a
git branch -r
git branch

```

### 1. plant分配到任务单后,一个任务单一个分支,多个任务单多个分支

```shell
// 不管什么情况下,分支一定基于master 切换到本地分支master
git checkout master
// 拉取最新的master  //分支管理 excel表格
git pull
git checkout -b feat-20240000-xxx

// 本地分支没有master
git checkout origin/master (git branch -a)
git checout -b feat-20240000-xxx
```

### 2. 开发过程中,一定不要合并其它人的分支,dev分支,test分支.

```shell
// 检查分支,从master开始,其它commit都是自己功能
git log --oneline
```

### 3. 自测,联调
```shell
// 1. 本地自测,本地联调 只需要切换 env 文件的,代理服务器
// 2. dev 分支自测

// 上传到远程分支,保存
git add .
git commit
git push // --set-upstream


git checout dev
git pull
git merge feat-20240000-xxx
git push 

// git pull 提示 no tracking infomation
//git branch --set-upstream-to xxx origin/xxx

// git push --set-upstream origin dev
// git push -u origin dev
// git push origin dev:dev git push origin dev
```

### 自测改bug

```shell
git checkout feat-20240000-xxx
....working...
git add .
git commit -m ''
git push // git push -u origin xxx

git checkout dev
git merge feat-20240000-xxx

```

### 3. 提测

```shell
git checkout stage
git pull
git merge feat-20240000-xxx

// 写提测单 两处地方写
// 改plant状态
// 通知测试 重新部署jenkins

```

### 4. 上线前一天

```shell

git checkout master 
git pull
git merge feat-20240000-xxx


// git tag
git tag <tagname>
git tag <tagname> commit_id 
git tag <tagname> -a xxx -m 

git tag -d <tagname>

git show <tagname>

git push origin <tagname>
git push origin -d <tagname>


```







## 可能用到的命令 commit  123123123213

```shell
git add 
git add .
git add -A

git restore --stageed ./README.md
git restore --staged .
git restore .

git commit // 默认是vim编辑器
git commit -m ''
git reset --soft HEAD^
cm1
cm2
cm3
cm4

git config --list
core.editor="D:\Software\notepad++\notepad++.exe" -multiInst -notabbar -nosession -noPlugin

// 临时储存一下 没有必要commit的时候
git stash list
git stash save xxx
git stash pop
git stash apply 
git stash drop


git revert
// 回退 时光机
git reset --hard commit_id
git log
git reflog

// master 临时一个修改bug
git cherry-pick 



git pull git fetch --rebase 区别


git config --global alias.br branch
git br


gitk
```