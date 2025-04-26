## How to use Git with GitHub, the most popular Git hosting service

### What is GitHub?
* **GitHub** is a **remote hosting platform** for Git repositories.

* It makes it easy to **share**, **collaborate**, and **manage** Git projects online.

* It offers extras like **issues**, **pull requests**, **CI/CD**, **pages**, and **actions**.

Think of Git as the engine and GitHub as the garage where you store and showcase your project cars.


## How to Use Git with GitHub (Step-by-Step)

### 1. Create a GitHub Account
* Go to [github.com](https://github.com/).

* Sign up for a free account if you don't have one.

### 2. Create a New Remote Repository
* Click the + icon → **New repository**.

* Give it a name (e.g., `awesome-project`).

* Keep it **empty** (don’t add README yet if you're pushing a local repo).

### 3. Link Your Local Repo to GitHub
If you already have a local project:
```js
git init
git add .
git commit -m "First commit"
```
Then connect to GitHub:
```js
git remote add origin https://github.com/your-username/awesome-project.git
```
Verify:
```js
git remote -v
```

### 4. Push Your Code to GitHub
```js
git push -u origin main
```
(If your branch is `master`, replace `main` with `master`.)

-`u` sets the **upstream** so next time you can just type `git push`.

Your code is now online!

### 5. Pull Changes from GitHub
If you or your teammate make changes and you want them locally:
```js
git pull origin main
```
(or just `git pull` after upstream is set.)

### 6. Make Changes and Push Again
* Edit or add files locally

* Stage and commit:
```js
git add .
git commit -m "Made some updates"
git push
```
Repeat!

### Cool Things You Can Do on GitHub

|Feature	|Purpose|
|-----------|--------|
|**Pull Requests (PRs)**|	Propose changes, review code, collaborate|
|**Issues**	|Track bugs, tasks, feature requests|
|**Actions**|	Set up CI/CD pipelines to test/deploy code|
|**GitHub Pages**|	Host static websites directly from a repo|
|**Project Boards**	|Kanban-style project management|

### Quick Cheat Sheet

|Command	|Meaning|
|-----------|--------|
`git clone <repo-url>`|	Copy remote repo locally
`git remote add origin <repo-url>`|	Connect to GitHub
`git push -u origin main` |	Push initial code
`git pull origin main`|	Fetch and merge remote changes
`git fetch` + `git merge`|	Alternative to git pull
`git status`|	Check what’s going on locally

### Common GitHub Terms

|Term	|Meaning|
|-----------|--------|
Fork|	Copy someone else's repo into your account
Star	|Bookmark a repo you like
Watch	|Get notifications about repo updates
Contributor|	Someone who pushed code to the repo