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
