# Git

### Merge

* If have master branch permission, merge to master locally and push to public
* if not, pull master to dev branch, resolve conflict and push to public and pull request

### Restore 

Commit level

```text
# keep history: o-o-o => o-o-o-o
git revert HEAD~n

# destroy history o-o-o => o-o
git reset --hard <commit>

# detached head: o-[head]-[master]
git checkout <commit>

# restore multiple commit
git revert <older commit>..<newer commit>
```

File level

```text
# restore file to working
git checkout <commit> file

# restore file to staging
git reset <commit> file

# restore file to both staging and working
git reset -- hard HEAD file
```

### Delete 

branch

```text
# Delete local branch:
git branch -D branch_name

# Delete remote branch:
git push <remote_name> --delete <branch_name>

```

### Note

* .gitignore will have no effect if the file/directory is already in the staging, to stop this, run: git rm -r --cached directory /

