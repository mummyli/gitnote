### 1、本地版本控制系统
RCS。 RCS 的工作原理是在硬盘上保存补丁集（补丁是指文件修订前后的变化）；通过应用所有的补丁，可以重新计算出各个版本的文件内容。
### 2、集中版本控制系统
CVS、Subversion 以及 Perforce 等。
### 3、分布式版本控制系统
Git、Mercurial、Bazaar 以及 Darcs 等。
### 4、什么是Git
1) 直接记录快照，而非差异比较。
2) 近乎所有操作都是本地的。
3) Git保证完整性。所有的数据在存储前都计算校验和，然后以校验和来引用。
4) Git一般只添加数据。
### 5、Git的三种状态
1) `已修改(modified)`: 表示修改了文件，但还没保存到数据库中。
2) `已暂存(staged)`: 表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
3) `已提交(committed)`: 表示数据已经安全地保存在本地数据库中。
### 6、Git配置
Git 自带一个 `git config` 的工具来帮助设置控制 Git 外观和行为的配置变量。
1) `/etc/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果在执行 `git config` 时带上 `--system` 选项，那么它就会读写该文件中的配置变量。 （由于它是系统配置文件，因此你需要管理员或超级用户权限来修改它。）
2) `~/.gitconfig` 或 `~/.config/git/config` 文件：只针对当前用户。 你可以传递 `--global` 选项让 Git 读写此文件，这会对你系统上 所有 的仓库生效。
3) 前使用仓库的 Git 目录中的 `config` 文件（即 `.git/config`）：针对该仓库。 你可以传递 `--local` 选项让 Git 强制读写此文件，虽然默认情况下用的就是它。

可以通过以下命令查看所有的配置以及它们所在的文件：
`git config --list --show-origin`

配置用户信息：<br>
```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

检查配置信息：`git config --list`<br>
查看某一项配置信息：`git config <key>`