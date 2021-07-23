`git rebase`和`git merge`都被设计来将一个分支的更改并入另一个分支，只不过方式有些不同。
### Merge
将 master 分支合并到 feature 分支最简单的办法就是用下面这些命令：
```bash
git checkout feature
git merge master
```
或者
```bash
git merge master feature
```
merge会将两个分支的历史连接在一起。保留了所有的历史提交记录。<br>
Merge 好在它是一个安全的操作。现有的分支不会被更改，避免了 rebase 潜在的缺点。<br>
另一方面，这同样意味着每次合并上游更改时 feature 分支都会引入一个外来的合并提交。如果 master 非常活跃的话，这或多或少会污染你的分支历史。虽然高级的 git log 选项可以减轻这个问题，但对于开发者来说，还是会增加理解项目历史的难度。
### Rebase
```bash
git checkout feature
git rebase master
```
它会把整个 feature 分支移动到 master 分支的后面，有效地把所有 master 分支上新的提交并入过来。但是，rebase 为原分支上每一个提交创建一个新的提交，重写了项目历史，并且不会带来合并提交。
### rebase黄金法则
绝不要在公共的分支上使用它。