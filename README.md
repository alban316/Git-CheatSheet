# Git-CheatSheet

### Content TBD
Content TBD

### Configure (Global) git config
```
git config -- global user.email “whoever@wherever.com”
git config -- global user.name “whoever”
```

### Configure (Local) git config
Overrides global settings for a particular repo (see [this post](https://notechnique.wordpress.com/2010/02/26/git-check-your-config/))….
```
git config user.email “whoever@wherever.com”

git config user.name “whoever”
```

### Clone repository locally
This clones the repo locally; not the same as forking.
```
git clone https://github.com/alban316/myrepo 
```

### If you already have files in a local folder
Create a repository on github, then:

```
git init

git remote add origin https://github.com/alban316/myrepo.git

git add -- all

git commit -m &quot;some remarks initial commit&quot;

git push -u origin master
```

The files are pushed from local out to github.

### Adding remote (github) content to local

```
git pull https://github.com/alban316/myrepo.git
```
(if VIM launches, press &lt;Escape&gt; then type :q)

### Committing changes to git
```
git commit -m &quot;some remarks about nature of updates&quot;
```
### Pushing changes to github
```
git push -u origin master
```
### Getting updates from remote
```
git pull origin master
```
### Checking status
```
git status
```
### Remove a file from repo, but NOT from file system
```
git rm -- cached file.txt
git rm -- cached somefolder/*
```
Meanwhile, ```git rm file.txt``` removes the file from the repo but also deletes it from the local file system.

### Some bash commands
#### To remove a folder and all of its subfolders:
```
rm -rf myfolder
```
#### To list folder contents:
```
ls
```
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
### Working with **Git Stash**
#### To stash changes (but not adds!)
```
git stash
```
#### To apply stashed files to the current branch
```
git stash apply
```
See also *Apply a specific stash*, below
#### To list the stashes (there may be multiple)
```
git stash list
```
#### To show files in a stash
```
git stash show 1
```
#### Drop a stash
```
git stash drop 1
```
#### Apply a specific stash
```
git stash apply 1
```

### Undo Last Commit
```
git reset HEAD~
```
See also [this thread](https://stackoverflow.com/questions/19303898/how-to-undo-last-commit#19303993)
Note: If you've already pushed, either don't do this at all **OR** after it's undone, create a new branch and abandon the other. Assuming this is an option. Otherwise you're now behind what you previously pushed.
