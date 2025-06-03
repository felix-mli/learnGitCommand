# learnGitCommand
To learn the git command

### git status
去查看现在的本地代码的修改
```yaml
git status
```

### git add & git commit & git push
git add 表示把修改的文件放入暂存区
git commit -m "XXX" 表示对这一次的提交进行一些描述，并且文件会在本地进行提交，我们可以进行多次进行add还有commit，最后一起push
git push 表示把本地的修改推送到远程仓库
```yaml
git add XXX
git commit -m "XXX"
git add XXX
git commit -m "XXX"
git push
```

### git log
使用git log可以查看提交的历史，可以看到commit的hash值，Author，Date以及commit的描述信息
```yaml
git log
```

### git reset
如果使用git commit -m "XXX"之后发现还有需要修改的地方，那么需要进行回退，使用git reset HEAD~1
```yaml
git status
git add XXX
git commit -m "XXX"
git status
git reset HEAD~1
git status
```
如果代码已经push到了远程分支，然后你需要回退到一个固定的hash值，可以使用git reset --mixed hash
--mixed => 重置到某个节点，并保留此节点到当前节点的改变到工作区，即未git add状态，所以需要重新git add和git commit
--soft => 重置到某个节点，并保留此节点到当前节点的改变到暂存区，即已git add状态，所以可以直接git commit
--hard => 当前工作区、暂存区以及此节点到当前阶段的改变都不会保留，直接替换为重置节点的工作区。

### git revert 
git revert 的作用是撤销某次的提交，相对于git reset来说，它的改动不会很大。适合跳着撤销某一次的代码，并保留中间提交的代码。

