## let-us-git

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
```
