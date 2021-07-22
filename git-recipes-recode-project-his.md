### git commit --amend
它允许你将缓存的修改和之前的提交合并到一起，而不是提交一个全新的快照。它还可以用来简单地编辑上一次提交的信息而不改变快照。<br>
但是，amend 不只是修改了最新的提交——它进行了一次替换。对于 Git 来说，这看上去像一个全新的提交
#### 不要修复公共提交
永远不要修复一个已经推送到公共仓库中的提交。<br>
修复过的提交事实上是全新的提交，之前的提交会被移除出项目历史。这和重设公共快照的后果是一样的。如果你修复了其他开发者在之后继续开发的一个提交，看上去他们的工作基础从项目历史中消失了一样。对于在这上面的开发者来说这是很困惑的，而且很难恢复。
### git rebase
将分支移到一个新的基提交的过程。<br>
从内容的角度来看，rebase 只不过是将分支从一个提交移到了另一个。但从内部机制来看，Git 是通过在选定的基上创建新提交来完成这件事的——它事实上重写了你的项目历史。理解这一点很重要，尽管分支看上去是一样的，但它包含了全新的提交。<br>
rebase 是将上游更改合并进本地仓库的通常方法。你每次想查看上游进展时，用 git merge 拉取上游更新会导致一个多余的合并提交。在另一方面，rebase 就好像是说「我想将我的更改建立在其他人的进展之上」。<br>
`git rebase <base>`:将当前分支 rebase 到 <base>，这里可以是任何类型的提交引用（ID、分支名、标签，或是 HEAD 的相对引用）。
#### 不要 rebase 公共历史
#### 例子
```bash
# 开始新的功能分支
git checkout -b new-feature master
# 编辑文件
git commit -a -m "Start developing a feature"

### 在 feature 分支开发了一半的时候，我们意识到项目中有一个安全漏洞:
# 基于master分支创建一个快速修复分支
git checkout -b hotfix master
# 编辑文件
git commit -a -m "Fix security hole"
# 合并回master
git checkout master
git merge hotfix
git branch -d hotfix


### 将 hotfix 分支并回之后 master，我们有了一个分叉的项目历史。我们用 rebase 整合 feature 分支以获得线性的历史，而不是使用普通的 git merge。
git checkout new-feature
git rebase master


### 它将 new-feature 分支移到了 master 分支的末端，现在我们可以在 master 上进行标准的快速向前合并了:
git checkout master
git merge new-feature
```
### git rebase -i
`-i`标记开始交互式`rebase`。交互式 rebase 给你在过程中修改单个提交的机会，而不是盲目地将所有提交都移到新的基上。你可以移除、分割提交，更改提交的顺序。
### git reflog
Git 用引用日志这种机制来记录分支顶端的更新。它允许你回到那些不被任何分支或标签引用的更改。在重写历史后，引用日志包含了分支旧状态的信息，有需要的话你可以回到这个状态。