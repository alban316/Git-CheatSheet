# Git-CheatSheet

### Content TBD
Content TBD


### Merge conflict prerequisites & references
Consider installing free, [Kdiff](http://kdiff3.sourceforge.net/), as recommended by multiple threads on StackOverflow, including [this one](https://stackoverflow.com/questions/4957630/how-do-you-merge-in-git-on-windows).

Now, edit C:\\users\\{username}\\.gitconfig as follows:

```
[merge]
        tool = kdiff3
[mergetool "kdiff3"]
        path = C:/Program Files/KDiff3/kdiff3.exe
[diff]
        tool = kdiff3
        guitool = kdiff3
[difftool "kdiff3"]
        path = C:/Program Files/KDiff3/kdiff3.exe
```

If these steps are not completed, git mergetool will default to a vim-based merge tool.

### Rebase & Resolve merge conflicts
Scenario: BranchA is a branch of master. BranchB is also a branch of master. A pull request for BranchA into master has been completed. BranchB needs to reflect the updates that have now been applied to master.

```
git checkout master
git pull

git checkout BranchB
git rebase --merge master

git mergetool

git commit

git merge --continue
```
