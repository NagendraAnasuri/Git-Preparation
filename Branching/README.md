## Practice creating and switching between branches

Practicing how to **create** and **switch between branches** is one of the core skills in Git. Branches allow you to work on different features, bug fixes, or experiments without affecting the main codebase.

Here’s a step-by-step guide to help you practice working with branches:

### 1. Check the Current Branch
To check the current branch, Run:
```js
git branch
```
This will show a list of local branches.

The current branch will have an asterisk (*) next to it (usually `main` or `master` by default).

### 2. Create a New Branch
To create a new branch, run:
```js
git branch feature-xyz
```
Replace feature-xyz with your desired branch name (e.g., `add-login`, `bugfix-header`, etc.).

This creates the branch but doesn’t switch to it.

### 3. Switch to a Branch
To move to another branch:
```js
git switch feature-xyz
```
Or (older syntax):
```js
git checkout feature-xyz
```
Now you're working on the feature-xyz branch. Any commits will only affect this branch.

### 4. Create and Switch in One Command
You can create and switch in a single step:
```js
git switch -c new-feature
```
Or:
```js
git checkout -b new-feature
```

### 5. Make Changes and Commit
Make changes to a file (e.g., edit index.html), then add and commit:
```js
git add .
git commit -m "Add new feature in new-feature branch"
```

### 6. Switch Back to Main
Return to the main branch:
```js
git switch main
```
If needed:
```js
git checkout main
```

### 7. List All Branches
```js```
git branch
```
To see remote branches too:
```js
git branch -a
```
### 8. Delete a Branch
After merging or if a branch is no longer needed:
```js
git branch -d feature-xyz
```
Force delete (if unmerged):
```js
git branch -D feature-xyz
```

### 9. View Branch History
To visualize the branch history:
```js
git log --oneline --graph --all
```

