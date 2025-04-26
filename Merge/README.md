## Merge changes from one branch into another and learn how merge commits work

Merging branches is a fundamental part of Git that lets you bring the changes from one branch into another. Let's walk through a practical, step-by-step example of how to merge changes from one branch into another, and explain how merge commits work.

### Step 1: Create a Sample Repository (if needed)
```js
mkdir merge-practice
cd merge-practice
git init
```
Create a sample file:
```js
echo "Initial content" > file.txt
git add .
git commit -m "Initial commit on main"
```

### Step 2: Create and Switch to a Feature Branch
```js
git switch -c feature-branch
```
Make a change:
```js
echo "Feature branch change" >> file.txt
git commit -am "Update file.txt in feature-branch"
```
### Step 3: Switch Back to the main Branch
```js
git switch main
```
You are now on the main branch again.

### Step 4: Merge the Feature Branch Into Main
```js
git merge feature-branch
```
If there’s no conflict, Git will perform a fast-forward merge if possible, or create a merge commit if necessary.

### What is a Merge Commit?
A **merge commit** is a special commit that has **two parent commits** — the tips of the branches being merged. It records the point in history where two branches were combined.

You’ll see something like this in the log:
```js
git log --oneline --graph --all
```
```js
*   8d3cdef Merge branch 'feature-branch'
|\
| * 3a2c1fd Update file.txt in feature-branch
* | 2f3e2b1 Initial commit on main
```
### Resolving Merge Conflicts
If both branches modify the same lines in a file, Git will prompt a conflict. You’ll need to manually edit the file, resolve the conflict, and then:
```js
git add file.txt
git commit  # This completes the merge and creates a merge commit
```
### Step 5: Delete the Feature Branch (Optional)
```js
git branch -d feature-branch
```
Use -D to force delete if it hasn't been merged.

