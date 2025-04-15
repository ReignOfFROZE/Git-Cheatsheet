# Cheatsheet

It is important to note that there are many ways of doing the same things in Git, and the ones outlined in this guide are just a small subset of the many ways you can manage a repository using Git.

Clone a repo that you own:
```
git clone git@github.com:ReignOfFROZE/Learning.git
```

Clone a repo that somebody else owns (note the difference in using `HTTPS` vs `SSH`):
```
git clone https://github.com/GTNewHorizons/GT5-Unofficial.git
```

Stage code to be committed:
```
git add path/to/file
git add .
git add -A # functionally the same as ., just a little more annoying to type
```

Commit staged files:
```
git commit -m "Brief description of changes made"
```

Push files to GitHub:
```
# If this is the first time you're pushing to this branch, use this variant to link your local branch to the remote branch
git push -u origin branchname
# If this is not the first time and the branches are already linked, use this variant
git push
```

Branch management:
```
# See branches and what branch you have active. Use arrow keys to navigate and press 'q' to quit.
git branch 
# Check out a new branch from the branch you're currently on
git checkout -b newBranch
# Check out a new branch from changes on another branch
git checkout -b newBranch anotherBranch
# Switch to another pre-existing branch
git checkout anotherBranch
# Switch to another branch but do not attempt to update anything about the other branch (safer way to switch between pre-existing branches)
git switch anotherBranch
# Delete a local branch
git branch -D branchName
# Delete a remote branch
git push remotename --delete branchName
```

Different ways to pull files from other repositories/your repository

When you first clone a repository, it will automatically generate a "remote" called `origin`. A remote is a remote repository in some form of remote storage location (GitHub, GitLab, BitBucket, etc). You can manage remotes as such:
```
git remote add remotename link-to-remote # can be HTTPS or SSH links
git remote set-url remotename new-remote-link
git remote remove remotename
```

If you want to get code from remotes locally, you can do a few different things:
```
# To create a new branch with code from a remote branch
git checkout -b localBranchName remoteName/branchName
# To fetch the remote changes, and then rebase them onto your local branch
# WARNING: This is likely to cause rebase conflicts if your local changes are conflicting with remote changes, I'd only recommend doing this if you're confident your changes won't cause problems, you don't care about your local changes, or you are comfortable reconciling the conflicts
git fetch remoteName
git rebase remoteName/branchName
# To pull changes from a remote repository onto your branch (this is essentially the same as merging the changes, but can be configured using the git config command. See https://git-scm.com/docs/git-config.
git pull remoteName branchName
```

To view the git log and see what commits you have locally:
```
git log
# A cleaner view
git log --oneline
```

To stash changes that are staged to be committed but have not yet been committed:
```
git stash
```
To then unstash those changes (essentially popping the changes onto whatever branch you have active)
```
git stash pop
```

One note, a lot of things revolving around rebasing and merging will probably require what is known as a **force push** to be able to be pushed to GitHub, this isn't as scary as it sounds, and can be done trivially by just adding the `-f` flag to your `git push` command
