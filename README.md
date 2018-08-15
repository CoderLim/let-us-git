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
```


[这是本书: 千万不要打开!](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
