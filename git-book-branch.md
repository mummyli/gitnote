### 1、分支简介
1) `git branch <name>`： 创建分支
2) `git checkout <branchname>`： 切换分支
3) `git checkout -b <branchname>`： 创建并切换分支

### 2、分支的新建与合并
```bash
# 1、新建分支 追踪系统中的 #53 问题
$ git checkout -b iss53
Switched to a new branch "iss53"

# some operation

# 2、临时修复任务
$ git checkout master
Switched to branch 'master'
$ git checkout -b hotfix
Switched to a new branch 'hotfix'

# some operation

# 3、修复完成，合并hotfix分支
$ git checkout master
$ git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 index.html | 2 ++
 1 file changed, 2 insertions(+)

# 4、删除hotfix分支
$ git branch -d hotfix
Deleted branch hotfix (3a0874c).
```
#### 遇到冲突时的合并
```bash
# 出现冲突
$ git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.


# 查看那些因包含合并冲突而处于未合并（unmerged）状态的文件：
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

    both modified:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

### 3、分支管理
1) `git branch`： 查看分支列表
2) `git branch -v`： 查看分支列表，包含每个分支最后一次的提交信息
3) `git branch --merged`: 查看所有包含已经合并工作的分支
4) `git branch --no-merged`: 查看所有包含未合并工作的分支


### 4、分支开发工作流
1) 长期分支
2) 主题分支

### 5、远程分支