## let-us-git


### git rebase
[rebase](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)

###  图形化展示
```
git log --graph --pretty=oneline --abbrev-commit
# 或者
git log --graph --oneline
```

### A同学reset后，B同学如何拉去到reset的版本

```bash
# A同学
git reset --hard 01234
git push -f origin dev

# B同学
git reset --hard origin/dev
```

### A同学新建分支a，B同学如何在本地拉取到分支a

```bash
# A同学
git checkout -b branch-a
git push -u origin branch-a

# B同学
git fetch
git checkout branch-a

#或者
git checkout -b branch-a
git pull origin branch-a
```

### 删除分支（本地和远程）

```bash
#  机器A
git push --delete origin test
git branch -d test

# 机器B
git fetch --all --prune
```

### git revert

```bash
#  第一步
git revert 0ab3c3
#  出现冲突，解决后
git add file1
git commit -m 'xxx' file1
# 然后状态显示：1、解决冲突后执行git revert --continue 2、git revert --abort
# 但是已经解决了冲突，再add和commit都没效果，所以只能abort了
# 看看这里的解释： https://www.monarchdigital.com/blog/2015-04-21/understanding-how-git-revert-works-and-when-use-it

#  正确姿势
# n代表不用每个revert版本都提交commit
# ..表示左边版本不可达但是右边版本可达的所有提交: 75bc23e是老版本，4de6ad1是最新版本(如果这个是非最新版本貌似会产生和上面一样的问题)
git revert -n 75bc23e..4de6ad1
# 然后解决冲突，再
git add file1
git commit
# 会让写commit的备注内容，写完保存，完成！
```

### git 大小写不敏感，重命名报错

```
The following untracked working tree files would be overwritten by checkout
```

[参考这里](https://www.cnblogs.com/imzhi/p/solution-to-git-checkout-error-tips.html)


[这是本书: 千万不要打开!](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)


### 忽略已在版本中的文件

```
# git的(.gitignore)不能直接忽略已经在版本库同步了的文件,只能控制本地忽略(不同步)某个文件...

# 如果想在本地忽略某个文件的话执行这个命令:
git update-index --assume-unchanged <file>

# 如果想重新同步这个文件的话执行这个命令.
git update-index --no-assume-unchanged <file>
```
