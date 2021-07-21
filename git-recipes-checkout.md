### git checkout
这个命令有三个不同的作用：检出文件、检出提交和检出分支。
1) `check master`： 回到master分支
2) `git checkout <commit> <file>`： 查看文件之前的版本。它将工作目录中的`<file>`文件变成`<commit>`中那个文件的拷贝，并将它加入缓存区。
3) `git checkout <commit>`： 更新工作目录中的所有文件，使得和某个特定提交中的文件一致。你可以将提交的哈希字串，或是标签作为`<commit>`参数。这会使你处在分离 HEAD 的状态。