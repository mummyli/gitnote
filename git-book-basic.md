### 1、获取Git仓库
获取git项目仓库的两种方法：
1) 将尚未进行版本控制的本地目录转换为 Git 仓库: `git init`
2) 从其它服务器 克隆 一个已存在的 Git 仓库: `git clone <url> <rename>`

### 2、记录每次更新到仓库
1) 查看当前文件状态：`git status`
2) 跟踪新文件： `git add <file>`
3) 暂存已修改文件： `git add <file>`
4) 忽略文件： 编辑`.gitignore`文件
    * 所有空行或者以 # 开头的行都会被 Git 忽略。
    * 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。
    * 匹配模式可以以（/）开头防止递归。
    * 匹配模式可以以（/）结尾指定目录。
    * 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。
5) 查看尚未暂存的文件更新内容：`git diff`
6) 暂存文件和最后一次提交的差异： `git diff --staged` or `git diff --cached`
7) 提交：`git commit -m "comments"`
8) 跳过使用暂存区： `git commit -a -m 'comments'`
9) 移除文件： `git rm <file>`
10) 移动文件： `git mv file_from file_to`

### 3、查看提交历史
1) `git log`: 会按时间先后顺序列出所有的提交，最近的更新排在最上面。 正如你所看到的，这个命令会列出每个提交的 SHA-1 校验和、作者的名字和电子邮件地址、提交时间以及提交说明。
2) `git log -p -3`: 它会显示每次提交所引入的差异。
3) `git log --stat`:  每次提交的简略统计信息。该选项在每次提交的下面列出所有被修改过的文件、有多少文件被修改了以及被修改过的文件的哪些行被移除或是添加了。

### 4、撤销操作
`git commit --amend`: 重新提交。这个命令会将暂存区中的文件提交。 如果自上次提交以来你还未做任何修改（例如，在上次提交后马上执行了此命令）， 那么快照会保持不变，而你所修改的只是提交信息。
#### 取消暂存的文件
`git reset`
#### 撤销对文件的修改
`git checkout`: 会覆盖文件


### 5、远程仓库的使用
1) `git remote`: 查看已经配置的远程仓库服务器(别名)
2) `git remote -v`: 显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL。
3) `git remote add <shortname> <url>`： 添加远程仓库
4) `git fetch <remote>`: 从远程仓库抓取
5) `git push <remote> <branch>`: 推送到仓库
6) `git remote show <remote>`: 查看仓库详情
7) `git remote rename <old_name> <new_name>`：重命名
8) `git remote remove <remote>`： 移除仓库

### 6、打标签
1) `git tag`: 列出标签
2) `git tag [-l | -list] 'v_1.*'`: 按通配符列出标签
#### 创建标签
1) 轻量标签（lightweight）:很像一个不会改变的分支——它只是某个特定提交的引用。
    * `git tag v1.4-lw`
2) 附注标签（annotated）: Git数据库中的完整对象，可被校验。包含打标签者的名字、电子邮件、日期、标签信息(并且可以使用 GNU Privacy Guard （GPG）签名并验证)
    * `git tag -a`创建附注标签。`git tag -a v1.4 -m "my version 1.4"`
    * `git show` 命令可以看到标签信息和与之对应的提交信息
3) 后期打标签：`git tag -a v1.2 9fceb02`
4) 共享标签<br>
默认情况下，`git push` 命令并不会传送标签到远程仓库服务器上。 在创建完标签后你必须显式地推送标签到共享服务器上。 这个过程就像共享远程分支一样——你可以运行 `git push origin <tagname>`。<br>
`git push origin --tags`推送所有标签
5) 删除标签：`git tag -d <tagname>`
6) 删除远程仓库标签： `git push <remote> :refs/tags/<tagname>` or `git push origin --delete <tagname>`
