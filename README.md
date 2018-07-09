## let-us-git

### A同学reset后，B同学如何拉去到reset的版本

```bash
# A同学
git reset --hard 01234
git push -f origin dev

# B同学
git reset --hard origin/dev
```
