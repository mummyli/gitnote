#### 1、reset
将一个分支的末端指向另一个提交，用来移除当前的一些提交。<br>
如下回退两个提交：
```bash
git checkout hotfix
git reset HEAD~2
```
除了在当前分支上操作，你还可以通过传入这些标记来修改你的缓存区或工作目录：
* `--soft` – 缓存区和工作目录都不会被改变
* `--mixed` – 默认选项。缓存区和你指定的提交同步，但工作目录不受影响
* `--hard` – 缓存区和工作目录都同步到你指定的提交
#### 2、checkout
`git checkout <branch>`： 切换分支<br>
`git checkout HEAD~2`： 把HEAD移动到特定提交<br>
#### 3、revert
Revert 撤销一个提交的同时会创建一个新的提交。这是一个安全的方法，因为它不会重写提交历史。比如，下面的命令会找出倒数第二个提交，然后创建一个新的提交来撤销这些更改，然后把这个提交加入项目中。
```bash
git checkout hotfix
git revert HEAD~2
```

#### 4、总结
|命令|作用域|常用场景|
|---|------|-----|
|git reset	|提交层面|	在私有分支上舍弃一些没有提交的更改|
git reset|	文件层面|	将文件从缓存区中移除|
git checkout|	提交层面	|切换分支或查看旧版本|
git checkout|	文件层面|	舍弃工作目录中的更改|
git revert|	提交层面|	在公共分支上回滚更改|
git revert|	文件层面|	（然而并没有）|