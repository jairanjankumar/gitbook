# Git

Git Log

```
$ git log
$ git reflog
```

Changing the git comment for already raised Pull Request

```
$ git fetch origin Dec04th
$ git commit —amend
$ git push origin Dec04th  
(or, $ git push -f origin Dec04th)
```

Update the PR, remove a file from a raised Pull Request

```
$ git checkout <origin/PRbranch>
$ git checkout upstream/master src/folder/filename.ext (can give absolute path)
$ git commit -m "no change in filename.ext"
$ git push origin <origin PRbranch>
```

Git Squash / ot Fixup

```
// ~3 to see last 3 commit in head
$ git rebase -i HEAD~3
This command will open vi editor. replace 'pick' by 's' to squash the commit.
and use "f" instead of "s" if you don't want to keep the commit messages of old commits, 
"f" will automatically remove the messages of old commits.

By doing so, your tip would be behind head. so you need to force push the changes.
$ git push origin <PRbranch> -f
```

You can also amend the commit, add file/change file without new commit id,

```
$ git commit --amend -a
$ git push -f origin branchName
```

Fetch an unmerged pull request for a branch which you don't own

```
// Add the upstream remote: (ignore if you have already one )
$ git remote add upstream https://github.geo.xxxx.com/yyyy/zzzz.git

// After that, you can checkout any pull request to a new branch with its ID:
$ git pull upstream pull/PULL_REQUEST_ID/head
 e.g. $ git pull upstream pull/307/head

git fetch upstream pull/PULL_REQUEST_ID/head:NEW_BRANCH_NAME
$ git checkout NEW_BRANCH_NAME
```

git branch

```
// Create a new branch
$ git checkout -b <newBranchName>

// Change a branch
$ git checkout <branchName>

// List all the branches
$ git branch

// Deleting a local branch
$ git branch -d <branchName>
```

Remove untracked files from the working tree

```
To show what will be deleted
$ git clean -n

this will delete files:
$ git clean -f

To remove directories: 
$ git clean -f -d 
or 
$ git clean -fd

To remove ignored files, run 
$ git clean -f -X 
or 
$git clean -fX

To remove ignored, non-ignored files and directories, run 
$ git clean git clean -xdf
```

HEAD is the symbolic name for the currently checked out commit.HEAD actually points to a branch’s ref and the branch points to the commit. HEAD is thus attached to a branch. When you make a new commit, the branch that HEAD points to is updated to point to the new commit. HEAD follows automatically since it just points to the branch.

```
$ git symbolic-ref HEAD
refs/heads/branchName
$ git rev-parse refs/heads/branchName
25aa71ffbc7dc9435bd0e1d1c85dc3e003ef4229
$ git rev-parse HEAD
25aa71ffbc7dc9435bd0e1d1c85dc3e003ef4229
HEAD → refs/heads/branchName → 25aa71ffbc7dc9435bd0e1d1c85dc3e003ef4229
```

so, when HEAD is detached, it points directly to a commit. instead of indirectly pointing to one through a branch.

**Git reset commitID --hard/soft/mixed**

* **`--soft`**: **uncommit** changes, changes are left staged (_index_).
* **`--mixed`** _(default)_: **uncommit + unstage** changes, changes are left in _working tree_.
* **`--hard`**: **uncommit + unstage + delete** changes, nothing left.

**Problem:**

After MacBook Pro to High Sierra upgrade, git command failed with following error:

```
$ git
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

Fix :

So, this looks something wrong with Xcode. Below worked for me.

```
$ xcode-select --install
```
