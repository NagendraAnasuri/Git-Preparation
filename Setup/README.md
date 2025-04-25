## Install and configure Git on your local machine

To install and configure Git on your local machine, follow these steps:

### Step 1: Download Git

1. Go to the official Git website: https://git-scm.com/.
2. The website will automatically detect your operating system and provide the appropriate download link
3. Download the Git installer for your operating system:
    * **Windows**: Click the "Download for Windows" button.
    * **macOS**: Click the "Download for macOS" button.
    * **Linux**: Follow the instructions specific to your distribution (Ubuntu, Fedora, etc.).

### Step 2: Install Git

### On Windows:
1. Run the downloaded .exe file to start the installation.

2. Choose the default options for most users, but here are the important ones:

    * **Select Components**: Make sure to select “Git Bash Here” to allow right-click integration in Windows Explorer.

    * **Choose the default editor used by Git**: Choose your preferred text editor (e.g., VS Code, Vim).

    * **Adjusting your PATH environment**: Choose “Use Git from the command line and also from 3rd-party software.”

    * **HTTPS transport backend**: Select "Use the OpenSSL library."

    * **Line endings**: Choose "Checkout Windows-style, commit Unix-style line endings."

    * **Git Credential Manager**: Choose "Git Credential Manager" to enable secure credential storage.

3. Complete the installation process.

### On macOS:
1. After downloading the `.dmg` file, open it and follow the instructions to drag Git into your Applications folder.

2. Alternatively, you can install Git using **Homebrew** by running:

```js
brew install git
```

### On Linux (Ubuntu Example):
1. Open a terminal and run the following commands to install Git:

```js
sudo apt update
sudo apt install git
```

### Step 3: Verify Installation
To verify that Git was installed successfully, open your terminal (or Git Bash on Windows) and run:

```js
git --version
```

This will display the installed version of Git, confirming it is working.

### Step 4: Configure Git
After installation, you need to configure Git with your name and email address. These configurations are used for commit messages.

1. Set your global username:
```js
git config --global user.name "Your Name"
```

2. Set your global email address:
```js
git config --global user.email "youremail@example.com"
```

You can verify your configuration with:
```js
git config --global --list
```

### Step 5: Set Up Git Bash (Windows Only)
Git Bash allows you to interact with Git through a terminal interface. You can open Git Bash by right-clicking on your desktop or within a folder and selecting **Git Bash Here**.

### Step 6: SSH Key Configuration (Optional, for GitHub/Remote Repositories)
If you plan to push to remote repositories like GitHub, you'll want to configure an SSH key to securely connect to the repository.

1. Check for existing SSH keys by running:
```js
ls -al ~/.ssh
```
If there is an existing key, you can skip to the next step. Otherwise, generate a new SSH key by running:
```js
ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
```
Follow the prompts and press Enter to accept the default file location.

2. Add the SSH key to the SSH agent:
```js
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

3. Copy the public key to your clipboard:
```js
cat ~/.ssh/id_rsa.pub
```

Copy the output (the long string starting with ssh-rsa).

4. Add the key to your GitHub account (or another Git service):

On GitHub, go to **Settings > SSH and GPG keys > New SSH key**.

Paste your public key into the "Key" field and give it a title.

### Step 7: Test SSH Connection (Optional)
Test your SSH connection to GitHub by running:
```js
ssh -T git@github.com
```

If successful, you’ll see a message saying "Hi username! You've successfully authenticated."