## Learn about the cooler way to integrate changes from one branch into another

**Rebasing** — the cooler, cleaner way to integrate changes from one branch into another

While `git merge` combines the histories of two branches (with a merge commit), `git rebase` lets you replay your commits on top of another branch, giving you a **linear history** that's easier to read.

### Merge vs Rebase (Quick Comparison)
|      Action      |         Result          |       History Style       |
| ---------------- |:-----------------------:|-------------------------- |
| `git merge`      | Adds a merge commit     |Branchy, keeps full history|
| `git rebase`     | Rewrites commit history |     Linear, cleaner       |

		
### How Rebase Works (Step-by-Step)
### 1. Start with two branches
You're on `feature-branch`, and `main` has some new commits.
```js
git switch feature-branch
```
Rebase your branch onto main:
```js
git rebase main
```
### What Git Does Internally
Git:

1. Temporarily saves your `feature-branch` commits.

2. Moves `feature-branch` to the latest commit in `main`.

3. Reapplies your commits one by one **on top** of `main`.		

### Example
```js
Before rebase:

main:    A---B---C
               \
feature:         D---E

After rebase:

main:    A---B---C---D'---E'
```
Notice how commits `D` and `E` are **rewritten** as new commits `D'` and `E'`.

### When to Use Rebase
Use `rebase` for:

Cleaning up your local commits before merging

Making history linear for easier debugging

Avoid `rebase` on **shared branches** (like `main`) if others are working on them, because rebasing rewrites history!

### Pro Tip: Rebase + Fast-forward Merge = Clean History
```js
git switch main
git merge --ff-only feature-branch
```
If the rebase made your branch linear, this will **fast-forward** without a merge commit.

### Interactive Rebase (git rebase -i)
Want to edit, squash, or reword commits before merging?
```js
git rebase -i main
```
You'll get a text editor where you can:

**pick** (keep a commit)

**squash** (combine commits)

**reword** (change commit message)