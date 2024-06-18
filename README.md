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
// 拉取最新的master
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
git checout dev
git pull
git merge feat-20240000-xxx
git push //git push origin dev:dev git push origin dev
```










## 可能用到的命令

git add 
git add .
git add -A

git restore --stageed ./README.md
git restore --staged .
git restore .

git commit // 默认是vim编辑器
git commit -m ''

git config --list
core.editor="D:\Software\notepad++\notepad++.exe" -multiInst -notabbar -nosession -noPlugin
