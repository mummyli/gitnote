### 安装
`apt-get install git`
### 检出仓库
* 本地仓库克隆版本：`git clone /path/to/repository`
* 远端服务器SSH版本： `git clone username@host:/path/to/repository`
* 远端服务器https： `git clone https:/path/to/repository.git`
### 创建新仓库
`git init` or `git init <dir>` or `git init --bare <directory>`（该命令会创建一个新的目录）创建新仓库。<br >
会在你项目的根目录下创建一个新的`.git`目录，其中包含了你项目必需的所有元数据。除了`.git`目录之外，已经存在的项目不会被改变（就像 SVN 一样，Git 不强制每个子目录中都有一个`.git`目录）。<br>
共享的仓库应该总是用`--bare`标记创建（见下面的讨论）。一般来说，用 —bare 标记初始化的仓库以 .git 结尾。比如，一个叫my-project的仓库，它的空版本应该保存在 my-project.git 目录下。<br>
`-—bare`标记创建了一个没有工作目录的仓库，这样我们在仓库中更改文件并且提交了。中央仓库应该总是创建成裸仓库，因为向非裸仓库推送分支有可能会覆盖已有的代码变动。将-—bare看成是用来将仓库标记为储存设施，而不是一个开发环境。也就是说，对于所有的 Git 工作流，中央仓库是裸仓库，开发者的本地仓库是非裸仓库。
`git status`查看当前状态。<br>
### 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的`工作目录`，它持有实际文件；第二个是`缓存区（Index）`，它像个缓存区域，临时保存你的改动；最后是`HEAD`，指向你最近一次提交后的结果。
### 添加与提交
使用`git add`跟踪新文件:`git add <filename>` or `git add *`
提交改动： `git commit -m "mdify information"`
### 推动更改
克隆的项目： `git push origin master`
还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器：`git remote add origin <server>`
### git配置
定义`当前仓库`所有提交使用的作者姓名： `git config user.name <name>`<br>
定义`当前用户`所有提交使用的作者姓名： `git config --global user.name <name>`<br>
定义当前用户所有提交使用的作者邮箱： `git config --global user.email <email>`<br>
为Git命令创建一个快捷方式（别名）： `git config --global alias.<alias-name> <git-command>`<br>
定义当前机器所有用户使用命令时用到的文本编辑器： `git config --system core.editor <editor>`<br>
用文本编辑器打开全局配置文件，手动编辑： `git config --global --edit`<br>
<br>Git 将配置项保存在三个单独的文件中，允许你分别对单个仓库、用户和整个系统设置:
* /.git/config – 特定仓库的设置。
* ~/.gitconfig – 特定用户的设置。这也是 --global 标记的设置项存放的位置。
* $(prefix)/etc/gitconfig – 系统层面的设置。

