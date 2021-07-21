### 安装
`apt-get install git`
### 检出仓库
* 本地仓库克隆版本：`git clone /path/to/repository`
* 远端服务器SSH版本： `git clone username@host:/path/to/repository`
* 远端服务器https： `git clone https:/path/to/repository.git`
### 创建新仓库
`git init`创建新仓库。`git status`查看当前状态。
### 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的`工作目录`，它持有实际文件；第二个是`缓存区（Index）`，它像个缓存区域，临时保存你的改动；最后是`HEAD`，指向你最近一次提交后的结果。
### 添加与提交
使用`git add`跟踪新文件:`git add <filename>` or `git add *`
提交改动： `git commit -m "mdify information"`
### 推动更改
克隆的项目： `git push origin master`
还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器：`git remote add origin <server>`