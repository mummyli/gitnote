### git remote
`git remote`允许你创建、查看和删除与其他仓库之间的链接。
1) `git remote`: 列出你和其他仓库之间的远程连接
2) `git remote -v`: 和上个命令相同，但同时显示每个连接的 URL。
3) `git remote add <name> <url>`: 创建一个新的远程仓库连接。在添加之后，你可以将 <name> 作为 <url> 便捷的别名在其他 Git 命令中使用。
4) `git remote rename <old_name> <new_name>`: 将远程连接从 <old-name> 重命名为 <new-name>。
5) `git remote rm <name>`:  移除名为的远程仓库的连接。

### git fetch
`git fetch`命令将提交从远程仓库导入到你的本地仓库。拉取下来的提交储存为远程分支，而不是我们一直使用的普通的本地分支。你因此可以在整合进你的项目副本之前查看更改。
1) `git fetch <remote>`: 拉取远程仓库的所有分支。
2) `git fetch <remote> <branch>`: 拉取指定分支。

### git pull
在基于 Git 的协作工作流中，将上游更改合并到你的本地仓库是一个常见的工作。我们已经知道应该使用 `git fetch`，然后是 `git merge`，但是 `git pull` 将这两个命令合二为一。
1) `git pull <remote>`: 拉取当前分支对应的远程副本中的更改，并立即并入本地副本。效果和 `git fetch` 后接 `git merge origin/.` 一致。
2) `git pull --rebase <remote>`: 和上一个命令相同，但使用 git rebase 合并远程分支和本地分支，而不是使用 git merge。

### git push
Push 是你将本地仓库中的提交转移到远程仓库中时要做的事。
1) `git push <remote> <branch>` : 将指定的分支推送到 `<remote>` 上，包括所有需要的提交和提交对象。它会在目标仓库中创建一个本地分支。为了防止你覆盖已有的提交，如果会导致目标仓库非快速向前合并时，Git 不允许你 push。
2) `git push <remote> --force`: 和上一个命令相同，但即使会导致非快速向前合并也强制推送。除非你确定你所做的事，否则不要使用 `--force` 标记。
3) `git push <remote> --all`: 将所有本地分支推送到指定的远程仓库。
4) `git push <remote> --tags`: 当你推送一个分支或是使用 `--all` 选项时，标签不会被自动推送上去。`--tags` 将你所有的本地标签推送到远程仓库中去。