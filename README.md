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

如果重新提交发现提示
```yaml
To https://github.com/felix-mli/learnGitCommand.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/felix-mli/learnGitCommand.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
这意味着远程仓库的main分支比本地的main分支更新，git拒绝直接覆盖远程的历史（这是一种保护机制）
因为之前使用了git reset --mixed回退了本地提交，导致本地分支的代码比远程分支的旧，或者在修改了这些代码之后，远程仓库有了别人的提交
就需要使用到变基rebase操作： git pull --rebase origin main

### git rebase
git rebase比较适合在个人分支上进行操作。在main分支上进行rebase不是一个好的办法，因为git rebase会将当前分支的提交从公共祖先开始重新用到目标分支的最新状态上，这会改变提交的hash值，导致远程分支的提交历史与本地分支不一致。


### git revert 
git revert 的作用是撤销某次的提交，相对于git reset来说，它的改动不会很大。适合跳着撤销某一次的代码，并保留中间提交的代码。

### git checkout
使用git checkout -b new_branch会创建一个分支，在这个分支上进行操作，最后通过分支进行提交

