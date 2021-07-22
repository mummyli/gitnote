### git branch
1) `git branch`: 列出仓库中所有分支。
2) `git branch <branch>`: 创建一个名为 `<branch>` 的分支。不会 自动切换到那个分支去。
3) `git branch -d <branch>`: 删除指定分支。这是一个安全的操作，Git 会阻止你删除包含未合并更改的分支。
4) `git branch -D <branch>`: 强制删除指定分支，即使包含未合并更改。如果你希望永远删除某条开发线的所有提交，你应该用这个命令。
5) `git branch -m <branch>`: 将当前分支命名为 <branch>。