## Learn how to undo changes with the reset command
`git reset` command. It's one of Git's most useful tools for undoing changes at different levels: **unstaged**, **staged**, and even **committed** changes.

### Git Reset: Three Levels of Undo

|      Command      |Affects Working Dir |Affects Staging Area Style |Affects Commit History|
| ---------------- |:------------------:|-------------------------- |-------------------------- |
| `git reset --soft`      | ❌     |❌|✅|
| `git reset --mixed` (default)     | ❌ |     ✅       |✅|
|`git reset --hard`|✅|✅|✅|

### 1. Undo Last Commit (Keep Changes)
If you committed too early, but want to keep your work in the staging area:
```js
git reset --soft HEAD~1
```
`HEAD~1` means "the commit before HEAD"

This:

* Removes the last commit

* Keeps your changes staged (ready to recommit)

### 2. Unstage Files (but Keep Changes)
You added files with `git add`, but now you want to unstage them:
```js
git reset
```
Or to unstage a specific file:
```js
git reset <file>
```
This:

* Moves files from the staging area back to working directory

* Does not touch file contents

### 3. Undo Commit and Unstage Changes
Want to undo the last commit **and** unstage the changes?
```js
git reset --mixed HEAD~1
```
This:

* Removes the last commit

* Keeps your code changes (unstaged)


### 4. Completely Discard Changes and Commits
Danger zone! 🔥
```js
git reset --hard HEAD~1
```
This:

* Deletes the last commit

* Deletes your local changes

* Cannot be undone (unless you're using `git reflog`)

### Undo Uncommitted Changes (Working Directory)
Want to discard changes in files before committing?
```js
git checkout -- <file>
```
Or to discard all uncommitted changes:
```js
git restore .
```

### Rescue with git reflog
If you reset something accidentally, run:
```js
git reflog
```
This shows recent Git actions, including lost commits. You can recover by copying the commit hash and doing:
```js
git reset --hard <commit-hash>
```

