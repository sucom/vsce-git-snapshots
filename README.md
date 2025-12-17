# Git Snapshots (VS Code Extension)

<p align="center">
  <img src="images/icon-sm.png" alt="Git Snapshots logo" width="120"/>
</p>
<p align="center">
  <img src="images/statusbar-icons.png" alt="Status bar icons"/>
</p>

Never lose your progress — instantly back up your work before taking the next step, whether by you or your AI. During learning, complex problem solving, complex feature development, or just want to look back how you got here.

With a few keystrokes or clicks, you can snapshot your entire project or a file, tag a session, or branch off your experiments — no complex Git commands required.

You don't really require remote (origin) repository. For personal learning/experiments, you can keep all your learning/experiment commit history local. Push only when you are ready to move to remote.

git-snapshots makes Git commits simple, fast, and easy for instant snapshots without commands.

##### Other related extensions without Git (for non-git environments)
- [Backup Folder](https://marketplace.visualstudio.com/items?itemName=spajs.backup-folder)
- [Backup File](https://marketplace.visualstudio.com/items?itemName=spajs.backup-file)


## ⚡ Quick Start

1. **Install** Git Snapshots from the VS Code Marketplace.
2. **Initialize** a Git repo (extension will prompt if missing).
3. **Make your first commit** with `Ctrl+Shift+M` or the status bar icon.
4. **Push to remote** with `Ctrl+Alt+P` once you’ve linked your GitHub repo.

## 🚀 Installation

- Install from [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=spajs.git-snapshots)

- Command Line: `code --install-extension spajs.git-snapshots`

OR

1. Open VS Code
2. Go to Extensions
3. Search for `git snapshots` and select this extension
4. Click **Install**

## ✨ Features:

With Git Snapshots, you’ll never touch the terminal for everyday Git tasks. Your history stays clean, your workflow stays smooth, and your focus stays on building.

- *Quick commit* **( Ctrl + Shift + C )** | *use status bar icon*

  Saves all files, stages everything, commits with auto message `tag@timestamp`.

- *Prompt commit* **( Ctrl + Shift + M )** | *use status bar icon*

  Same as *Quick commit*, but lets you edit the pre-filled message.

- *Auto‑commit* on save with configurable debounce.

- *Create tag* **( Alt + Shift + T )** | *use status bar icon*

  Prompts for a tag name, creates an annotated tag. These tags are automatically attached to the latest commit and pushed silently to the remote origin when you press Push.

- *Create branch* **( Alt + Shift + B )** | *use status bar icon*

  Prompts for a branch name, creates and checks out a new branch.

- *Push* **( Ctrl + Alt + p )** | *use status bar icon*

  - Pushes commits to the configured remote (origin).
  - If `autoCommitOnPush` is enabled, uncommitted changes are auto‑committed before pushing.
  - Tags are also pushed automatically.

- *Status bar icons* for all actions — no shortcuts required.

- *Silent mode* for distraction‑free workflows.

### 🛡 Self‑healing:

- Initializes Git repos automatically if missing
- Prompts for identity (name/email) when needed
- Offers to create a sensible `.gitignore` if it’s missing

## ⚙️ Configuration

### Extension settings [ ctrl + , ] / gitSnapshots

- `autoCommitOnPush`: On push, automatically commit uncommitted changes using a message autoCommitOnPush@timestamp. [default: false]

- `autoCommitOnSave`: Automatically commit changes on file save. [default: false]

- `autoCommitDebounceMs`: Debounce delay (milliseconds) for auto-commit on save. [default: 1000]

- `prefix`: Commit message prefix. [default: commit]

- `silent`: Suppress popup info messages (only show status bar updates). [default: false]

### Optional git settings (built-in with extension actions)

#### Initialize a local Git repo
*(if not initialized)*
  ```bash
  # for initial-branch=master
  git init

  # OR

  git init --initial-branch=main
  ```

#### Git identity
*(if not configured)*
```shell
# --global (applies everywhere)

git config --global user.name "Full Name"
git config --global user.email "email.address@xyz"
```

```shell
# applies to current project only

git config user.name "Full Name"
git config user.email "email.address@xyz"
```
- *user.name* → shows up in commit history as the author.
- *user.email* → also stored in commits; can be any valid email (doesn’t have to be real if you’re just local).

#### Optional settings (advanced users): *(if not configured)*
```shell
# --global (applies everywhere)

git config --global core.autocrlf input
git config --global pull.rebase false
```

```shell
# applies to current project only

git config core.autocrlf input
git config pull.rebase false
```
- *core.autocrlf* : normalize line endings
  - Controls how Git handles line endings between Windows (CRLF) and Unix (LF).
  - input means: convert CRLF → LF on commit, but leave files as‑is when checking out.
  - Useful if you want consistent LF endings in history, but not strictly required.

- *pull.rebase* : use merge instead of rebase on pull
  - Controls whether git pull does a merge or a rebase.
  - false = default merge behavior.

## 🚀 Usage

1. *Make an initial commit* using **Ctrl+Shift+M** | *use status bar icon*

    - Enter a message like *base / initial / level-0 / etc.* This creates the baseline for the commit trail.

2. *Start a session* with **Ctrl+Shift+T** | *use status bar icon*

    - Example: ```session/topic/feature-name/story#/task-name/experiment-name/...```. This tag will be used as commit prefix for easy grouping.

3. *Work and take snapshots* with

    - *Quick commit* **Ctrl+Shift+C** | *use status bar icon*: for quick commit with message: tag@timestamp1, tag@timestamp2...
    - *Prompt commit* **Ctrl+Shift+M** | *use status bar icon* : edit the prefilled message for future reference.

4. *Branch* off your big milestones with **Alt+Shift+B** | *use status bar icon*

    - Example: ```experiment-objects```.

5. *Optional small milestone tags* with **Ctrl+Shift+T** | *use status bar icon*

    - to mark small checkpoints (e.g., milestone-1).

6. *Review* history with any git visual tools/extensions.

7. *Working with remote repository* - Git requires authentication before you can push commits or tags to a repo. Refer the Git Authentication Tips section below or your remote repo authentication guide.


## 🏕️ Quality of Life

git-snapshots isn’t just about quick commits — it’s tuned for a smooth developer experience:

- **Debounced auto-commit on save**
  When `autoCommitOnSave` is enabled, saving multiple files (e.g. with *Save All*) triggers only **one commit**. A short debounce ensures the commit happens after the last save, so your history stays clean.

- **Silent mode**
  Prefer fewer popups? Enable `gitSnapshots.silent` to suppress info messages. You’ll still see status bar updates for 5 seconds, but no extra dialogs.

- **Status bar icons**
  No need to memorize shortcuts — quick actions are always available in the status bar:
  ![Status bar icons](images/statusbar-icons.png)
  - ![Status bar icons](images/statusbar-commit.png) → Quick Commit
  - ![Status bar icons](images/statusbar-comment.png) → Commit with Comment
  - ![Status bar icons](images/statusbar-tag.png) → Create Tag
  - ![Status bar icons](images/statusbar-branch.png) → Create/Switch Branch
  - ![Status bar icons](images/statusbar-push.png) → Push to remote (origin)

- **No wasted commits**
  Both quick and prompt commits skip gracefully if there are no changes, so you won’t clutter history with empty commits.

These touches make snapshotting feel natural and unobtrusive, whether you’re experimenting, learning, or building features with or without AI.


## 🔐 Git Authentication Tips
When working with remote repositories, Git requires authentication before you can push commits or tags. Here are the recommended approaches:

> Git caches/stores credentials per remote URL, so multiple projects with different accounts are supported.

#### Cache/Store your credentials:
```shell
git config --global credential.helper cache   # keeps in memory for a few hours
git config --global credential.helper store   # saves in plain text (simple but less secure)
```

### HTTPS with Personal Access Tokens (PATs) - GitHub

- Generate a PAT (GitHub Repo):

  1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic).
  2. Click Generate new token.
  3. Select scope: check repo (full control of private repos).
  4. Copy the token (you won’t see it again).

- Use the PAT:

  - When Git prompts for username/password:
  - Username = your GitHub username.
  - Password = the PAT.


### SSH Keys (advanced, for multiple accounts)

> create `.ssh` folder in ~ (sytem home folder) if not exist.
>
> In windows ~ = c:\users\YourName

1. Generate an *ssh key file* in the `~/.ssh` folder, using `ssh-keygen` command

    ```shell
    ssh-keygen -t ed25519 -C "github-key-1" -f ~/.ssh/id_ed25519-github-key1
    ```

    This will generate:

    - *Private key:* `~/.ssh/id_ed25519-github-key1`
    - *Public key:* `~/.ssh/id_ed25519-github-key1.pub`

    > `-t ed25519` → Algorithm: fixed and recommended.
    >
    > `-C "github-key-1"` → Comment: human‑readable label (short text/email) for easy identification inside the key file. Ex: "GitHub-key-1", "work", "email-address", etc.
    >
    > `-f ~/.ssh/id_ed25519-github-key1` → file path and name for the key pair. Recommended descriptive filenames. Ex: id_ed25519-github, id_ed25519-work, etc.


2. Add to remote repo SSH settings (ex: GitHub):

    Copy the content of public key `~/.ssh/id_ed25519-github-key1.pub` into GitHub (/your remote repo) → Settings → SSH and GPG keys.

#### *Optional* Configuration for multiple accounts [Personal, Work]:
Edit ~/.ssh/config

```code
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519-github-key1

Host bitbucket.company.com
  HostName bitbucket.company.com
  User git
  IdentityFile ~/.ssh/id_ed25519-work
```
> Use SSH repo URLs like
>
> git@`github.com`:**usernameX**/repo.git
>
> git@`bitbucket.company.com`:**usernameY**/repo.git`


#### Verify SSH setup

Run the following to confirm your key is working:

```shell
ssh -T git@github.com

# If successful, GitHub will reply:
# Hi usernameX! You've successfully authenticated, but GitHub does not provide shell access.

ssh -T git@bitbucket.company.com

# If successful, GitHub will reply:
# Hi usernameY! You've successfully authenticated, but GitHub does not provide shell access.
```

> You may get a first time warning. Continue connecting with `yes`<br>
>
> The authenticity of host 'github.com (n.n.n.n)' can't be established.<br>
> ED25519 key fingerprint is SHA256:+...x...y...z...U.<br>
> This key is not known by any other names.<br>
> Are you sure you want to continue connecting (yes/no/[fingerprint])? `yes`<br>
> Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.<br>
>
> This will create two files [`known_hosts`, `known_hosts.old`] in `~/.ssh` folder


#### If you have multiple accounts in single domain (Ex: GitHub), use aliases.

```code
Host github-userX
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519-github-key1

Host github-userY
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519-github-key2
```
> Define different Host aliases with respective IdentityFiles for each account.
>
> Then use repo URLs like:
>
> - git@`github-userX`:usernameX/repo.git
>
> - git@`github-userY`:usernameY/repo.git

#### Verify SSH setup
```shell
ssh -T git@github-userX
# If successful, GitHub will reply:
# Hi usernameX! You've successfully authenticated, but GitHub does not provide shell access.

ssh -T git@github-userY
# If successful, GitHub will reply:
# Hi usernameY! You've successfully authenticated, but GitHub does not provide shell access.
```

### Identity vs Authentication
Identity (user.name, user.email) is already handled per project by Git Snapshots (if not configured).

Authentication (PATs or SSH keys) is managed by Git itself — Git Snapshots extension relies on Git’s secure helpers.


## 🛠 Push Checklist

- **Repo linked**: Make sure `origin` is set (extension will prompt if missing).

- **Identity configured**: Confirm `user.name` and `user.email` are set locally (extension handles this).

- **Commits exist**: At least one commit in history (with/without gitSnapshots you should have some commits).

- **Authentication** checklist:

  - If using HTTPS → have your `PAT` handy.

  - If using SSH → ensure your key is added in your repo account (Ex: GitHub and `ssh -T git@github.com` works).

- **Branch alignment**: Local branch matches remote default (`main` vs `master`). Extension will prompt if mismatch.

- **Tags**: If you’ve created `tags`, accept a prompt *(for now and will be silent in the next update)* to push them too.

## 🛠️ Troubleshoot

### NOT a git repository
---
***Error:***

> Commit/Command failed: git status --porcelain fatal: not a git repository (or any of the parent directories): .git

**→ Fix:** Init Git. See the above Configuration ➡️ [Initialize a local Git repo](#initialize-a-local-git-repo) section.

### Author identity unknown
---
***Error:***

> Commit/Command failed: git commit -m "commit: -base" Author identity unknown *** Please tell me who you are. Run git config --global user.email "you@example.com" git config --global user.name "Your Name" to set your account's default identity. Omit --global to set the identity only in this repository. fatal: unable to auto-detect email address (got 'xyz@system.(none)')

**→ Fix:** Set Git idenity. See the above Configuration ➡️ [Git identity](#git-identity) section.

### Push failed (*if `gitSnapshots: push` fails on the following*)
---

#### `Authentication failed`
***Error:***
> fatal: Authentication failed

**→ Fix:**

- If using HTTPS → ensure your PAT is correct and re‑enter when prompted.
- If using SSH → verify with: `ssh -T git@...` refer [Verify SSH setup](#verify-ssh-setup) section in Authentication Tips for more details.
---

#### `Push failed: (fetch first)`

>Push failed: Command failed: git push -u origin main To xyz.git ! [rejected] main -> main (fetch first) error: failed to push some refs to 'xyz.git' hint: Updates were rejected because the remote contains work that you do not hint: have locally. This is usually caused by another repository pushing to hint: the same ref. If you want to integrate the remote changes, use hint: 'git pull' before pushing again. hint: See the 'Note about fast-forwards' in 'git push --help' for details.

**Reason:** Updates were rejected because the remote contains work that you do not have locally.

**→ Fix:** Run

```shell
# get files from origin
git fetch origin

# merge origin files with local
git merge origin/main
# if fatal: refusing to merge unrelated histories, try
# git merge origin/main --allow-unrelated-histories

# push local to origin branch
git push -u origin main
```
---

#### `branch mismatch`

***Error:***

> error: src refspec main does not match any

**→ Fix:**

- Confirm your local branch name:
    ```shell
    git branch --show-current
    ```

- If remote default is main but you’re on master, rename or push accordingly:

    ```shell
    git push -u origin master
    ```

---

#### `no commits yet`

***Error:***

> error: src refspec main does not match any

**→ Fix:**

- Make an initial commit first:

  ```shell
  git commit --allow-empty -m "Initial commit"
  git push -u origin main
  ```
---


### 📘 Quick Recovery Commands

| Error message                          | Reason                                   | Fix commands                          |
|----------------------------------------|------------------------------------------|---------------------------------------|
| fatal: Authentication failed           | PAT incorrect or SSH key not set         | HTTPS → re‑enter PAT<br>SSH → `ssh -T git@github.com` |
| ! [rejected] main -> main (fetch first)| Remote has commits you don’t have        | `git fetch origin`<br>`git merge origin/main`<br>`git push -u origin main` |
| fatal: refusing to merge unrelated histories | Local and remote both have independent first commits | `git fetch origin`<br>`git merge origin/main --allow-unrelated-histories`<br>`git push -u origin main` |
| error: src refspec main does not match any | Branch mismatch or no commits yet        | Check branch → `git branch --show-current`<br>Make commit → `git commit --allow-empty -m "Initial commit"` |



## ☑️ Requirements

- VS Code v1.100.0 or higher.
- Git

## ⚖️ License

MIT

## 🏠 Home

[GitHub](https://github.com/sucom/vsce-git-snapshots)
