## How Git stores data on the files system and the plumbing commands that make it all work

Git is a powerful version control system that efficiently stores and manages data, keeping track of the entire history of a project. Understanding how Git stores data on the file system can help you grasp the inner workings of Git, as well as the low-level "plumbing" commands that make everything work.

### How Git Stores Data
At a high level, Git stores all of its data in the `.git` directory inside a project. This directory contains everything Git needs to manage the repository, including the history of all commits, branches, configurations, and other metadata.

Git stores the data in several components:

**1. Objects**: Git stores information about the files and changes in the form of objects.

**2. Refs**: Git uses references (refs) to keep track of the heads of branches and tags.

**3. Index**: Git’s staging area is where changes are prepared before being committed.

**4. Configuration**: Git keeps various configuration settings in the repository.

Let's break down these components further and explore the plumbing commands that interact with them.

### 1. Git Objects
Git's core data structure is an object database. Git objects are the heart of the repository, and they are what Git uses to track and store the entire history of the project. There are four main types of objects:

* **Commit:** A snapshot of your project and a record of changes made. It also contains a reference to its parent commit(s).

* **Tree**: A representation of a directory (including the files it contains). Each tree object has a reference to the files and subdirectories.

* **Blob**: A binary large object that represents the content of a file. Git stores file contents as blobs.

* **Tag**: A reference to a commit, typically used for marking releases or important points in history.

Git objects are stored in a compressed format inside the `.git/objects` directory.

**Object Storage** in .git/objects

* Objects are stored in the .git/objects directory using a directory structure. Objects are named using the first two characters of their hash ID (SHA-1 hash), and the rest of the hash is used as the file name.

* Each object is compressed and stored in a file with the .pack extension in some cases, for efficiency.

For example, a commit object with the SHA-1 hash e6f1d6d63b7fbe1344d370fcf6b24485b6d623b0 would be stored in:
```js
.git/objects/e6/f1d6d63b7fbe1344d370fcf6b24485b6d623b0
```
### 2. Git Refs
Git uses references (refs) to track branches, tags, and remote references. A **ref** is essentially a pointer to a commit. The most commonly used refs are:

* **HEAD**: A special reference that points to the current branch or commit that you're working on.

* **Branch Refs**: For example, `refs/heads/main` or `refs/heads/feature-xyz` points to the most recent commit on a specific branch.

* **Remote Refs**: For example, `refs/remotes/origin/main` points to the main branch on the remote repository.

These refs are stored in the `.git/refs` directory.

#### How Refs Work:
* When you commit, Git updates the ref for the current branch to point to the new commit.

* You can check out a commit, which changes the HEAD ref to point to that commit.

* Git uses the ref structure to manage and track the branches and tags in your repository.

### 3. Git Index (Staging Area)
The **index** is the intermediate area where changes are staged before being committed. When you use `git add` to stage files, Git stores them in the index.

* The index contains references to the file contents that are about to be committed, but it is separate from the working directory (the actual files you see).

* The contents of the index are stored in the `.git/index` file.

### 4. Git Configuration
Git maintains configuration settings at several levels, including:

* **System-level**: Global configuration for all users on the system.

* **User-level**: Configuration for the specific user.

* **Repository-level**: Configuration for a specific repository.

These configurations are stored in files within the `.git` directory, such as:

* `.git/config`: The repository-specific configuration.

* `.gitmodules`: Stores information about any submodules in the repository.

### Plumbing Commands
Plumbing commands in Git are the low-level commands that interact directly with Git's internal objects and references. These commands are typically used for scripting or automation. Unlike the "porcelain" commands (e.g., `git commit`, `git push`), plumbing commands are more raw and provide more control.

Here are some important plumbing commands:

**1. `git cat-file`**

This command allows you to view the contents of Git objects (commits, trees, blobs, tags).

* **Example: View commit object:**
    ```js
    git cat-file commit <commit_hash>
    ```
* **Example: View tree object (list files in a commit):**
    ```js
    git cat-file tree <commit_hash>
    ```

**2. `git ls-tree`**

Lists the contents of a tree object, which represents a directory. You can use it to see the files in a specific commit or branch.

* **Example: List files in a commit:**
    ```js
    git ls-tree <commit_hash>
    ```
**3. `git rev-parse`**

This command is used to parse Git references and get information like commit hashes, branch names, or HEAD status.

* **Example: Get the current commit hash:**
    ```js
    git rev-parse HEAD
    ```

**4. `git update-ref`**

This command updates a reference directly, which is often used in scripting or advanced Git workflows.

* **Example: Update HEAD ref to point to a different commit:**
    ```js
    git update-ref HEAD <commit_hash>
    ```
**5. `git commit-tree`**

This command allows you to create a commit object manually. It's useful for scripting or creating commits outside the normal workflow.

* **Example: Create a new commit:**
    ```js
    git commit-tree <tree_hash> -p <parent_commit_hash> -m "commit message"
    ```
**6. `git cat-file commit`**

Displays the information stored in a commit object, including its parent commit and the tree object it points to.

* **Example:**
    ```js
    git cat-file commit <commit_hash>
    ```

**7. `git ls-remote`**

Shows references in a remote repository. It is often used to get information about branches or tags on a remote.

* **Example:**
    ```js
    git ls-remote <remote_url>
    ```
### Summary of How Git Stores Data
* Git stores all data in the .git directory, which contains:

    * **Objects** (commit, tree, blob, and tag objects),

    * **Refs** (branches, tags, and remotes),

    * **Index** (the staging area),

    * **Configuration files.**

* **Objects** are stored as compressed files, with each file representing a snapshot of your project at a certain point (commit, file, or directory).

* **Refs** are pointers to commits that represent the heads of branches and tags.

* **Index** is a staging area for changes that are prepared for the next commit.

* **Plumbing commands** give direct access to Git's internal structures, allowing more granular control over Git operations.

Understanding these internal mechanisms gives you deeper insight into how Git works under the hood and how you can interact with it in a more advanced way.