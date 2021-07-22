### git branch
1) `git branch`: 列出仓库中所有分支。
2) `git branch <branch>`: 创建一个名为 `<branch>` 的分支。不会 自动切换到那个分支去。
3) `git branch -d <branch>`: 删除指定分支。这是一个安全的操作，Git 会阻止你删除包含未合并更改的分支。
4) `git branch -D <branch>`: 强制删除指定分支，即使包含未合并更改。如果你希望永远删除某条开发线的所有提交，你应该用这个命令。
5) `git branch -m <branch>`: 将当前分支命名为 <branch>。

### git checkout
切换分支
1) `git checkout <existing-branch>`: 查看特定分支，分支应该已经通过 `git branch` 创建。这使得 `<existing-branch>` 成为当前的分支，并更新工作目录的版本。
2) `git checkout -b <new-branch>`: 创建并查看 `<new-branch>`，`-b` 选项是一个方便的标记，告诉Git在运行 `git checkout <new-branch>` 之前运行 `git branch <new-branch>`。 
3) `git checkout -b <new-branch> <existing-branch>`: 和上一条相同，但将 <existing-branch> 作为新分支的基，而不是当前分支。


### git merge
合并是 Git 将被 fork 的历史放回到一起的方式。`git merge` 命令允许你将 `git branch` 创建的多条分支合并成一个。<br>
注意，下面所有命令将更改 并入 当前分支。当前分支会被更新，以响应合并操作，但目标分支完全不受影响。也就是说 `git merge` 经常和 `git checkout` 一起使用，选择当前分支，然后用 `git branch -d` 删除废弃的目标分支。
1) `git merge <branch>`: 将指定分支并入当前分支。Git 会决定使用哪种合并算法（下文讨论）。
2) `git merge --no-ff <branch>`: 将指定分支并入当前分支，但 总是 生成一个合并提交（即使是快速向前合并）。这可以用来记录仓库中发生的所有合并。