### git status
列出已缓存、未缓存、未追踪的文件。<br>
### git log
显示已提交的快照。你可以列出项目历史，筛选，以及搜索特定更改。只作用于提交的项目历史。<br>
1） 默认格式显示完整项目历史：`git log`<br>
2） 限制提交数量： `git log -n <limit>`<br>
3） 将每个提交压缩到一行： `git log --oneline`<br>
4） 另外包含哪些文件被更改了，以及每个文件相对的增删行数：`git log --stat`<br>
5） 显示代表每个提交的一堆信息。显示每个提交全部的差异（diff），这也是项目历史中最详细的视图： `git log -p`<br>
6） 搜索特定作者的提交。<pattern> 可以是字符串或正则表达式：`git log --author="<pattern>"`<br>
7） 搜索提交信息匹配特定 <pattern> 的提交。<pattern> 可以是字符串或正则表达式：`git log --grep="<pattern>"`<br>
8） 只显示发生在 <since> 和 <until> 之间的提交。两个参数可以是提交 ID、分支名、HEAD 或是任何一种引用。`git log <since>..<until>`<br>
9） 只显示包含特定文件的提交。`git log <file>`<br>
10） --graph 标记会绘制一幅字符组成的图形，左边是提交，右边是提交信息。--decorate 标记会加上提交所在的分支名称和标签。--oneline 标记将提交信息显示在同一行，一目了然。`git log --graph --decorate --oneline`