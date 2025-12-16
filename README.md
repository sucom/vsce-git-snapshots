# Git Snapshots (VS Code Extension)

Never lose your progress — instantly back up your work before taking the next step, whether by you or your AI. During learning, complex problem solving, complex feature development, or just want to look back how you got here.

With a few keystrokes or clicks, you can snapshot your entire project or a file, tag a session, or branch off your experiments — no complex Git commands required.

git-snapshots makes Git commits simple, fast, and easy for instant snapshots without commands.

##### Other related extensions without Git (for non-git environments)
- [Backup Folder](https://marketplace.visualstudio.com/items?itemName=spajs.backup-folder)
- [Backup File](https://marketplace.visualstudio.com/items?itemName=spajs.backup-file)

## ✨ Features:

With Git Snapshots, you’ll never touch the terminal for everyday Git tasks. Your history stays clean, your workflow stays smooth, and your focus stays on building.

- *Quick commit* **( Ctrl + Shift + C )**
  Saves all files, stages everything, commits with auto message `tag@timestamp`.

- *Prompt commit* **( Ctrl + Shift + M )**
  Same as quick commit, but lets you edit the prefilled message.

- *Auto‑commit* on save with configurable debounce.

- *Create tag* **( Alt + Shift + T )**
  Prompts for a tag name, creates an annotated tag.

- *Create branch* **( Alt + Shift + B )**
  Prompts for a branch name, creates and checks out a new branch.

- *Status bar icons* for all actions — no shortcuts required.

- *Silent mode* for distraction‑free workflows.

### 🛡 Self‑healing:

- Initializes Git repos automatically if missing
- Prompts for identity (name/email) when needed
- Offers to create a sensible .gitignore if absent

## ⚙️ Configuration

### Extension settings [ ctrl + , ] / gitSnapshots

- `autoCommitOnSave`: Automatically commit changes on file save. [default: false]

- `autoCommitDebounceMs`: Debounce delay (milliseconds) for auto-commit on save. [default: 1000]

- `prefix`: Commit message prefix. [default: commit]

- `silent`: Suppress popup info messages (only show status bar updates). [default: false]

### Optional git settings (built-in with extension actions)

#### Initialize a local Git repo: *(if not initialized)*
  ```bash
  # for initial-branch=master
  git init

  # OR

  git init --initial-branch=main
  ```

#### Git identity: *(if not configured)*
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

1. *Make an initial commit* using **Ctrl+Shift+M**
    - Enter a message like *base / initial / level-0 / etc.* This creates the baseline for the commit trail.

2. *Start a session* with **Ctrl+Shift+T**
    - Example: ```session/topic/feature-name/story#/task-name/experiment-name/...```. This tag will be used as commit prefix for easy grouping.

3. *Work and take snapshots* with
    - *Quick commit* **Ctrl+Shift+C**: tag@timestamp1, tag@timestamp2...
    - *Prompt commit* **Ctrl+Shift+M**: edit the prefilled message for future reference.

4. *Branch* off your big milestones with **Alt+Shift+B**
    - Example: ```experiment-objects```.

5. *Optional small milestone tags* with **Ctrl+Shift+T**
    - to mark small checkpoints (e.g., milestone-1).

6. *Review* history with any git visual tools/extensions.


## 🏕️ Quality of Life

git-snapshots isn’t just about quick commits — it’s tuned for a smooth developer experience:

- **Debounced auto-commit on save**
  When `autoCommitOnSave` is enabled, saving multiple files (e.g. with *Save All*) triggers only **one commit**. A short debounce ensures the commit happens after the last save, so your history stays clean.

- **Silent mode**
  Prefer fewer popups? Enable `gitSnapshots.silent` to suppress info messages. You’ll still see status bar updates for 5 seconds, but no extra dialogs.

- **Status bar icons**
  No need to memorize shortcuts — quick actions are always available in the status bar:
  - `$(check)` Quick Commit
  - `$(comment)` Commit with Comment
  - `$(tag)` Create Tag
  - `$(git-branch)` Create/Switch Branch

- **No wasted commits**
  Both quick and prompt commits skip gracefully if there are no changes, so you won’t clutter history with empty commits.

These touches make snapshotting feel natural and unobtrusive, whether you’re experimenting, learning, or building features with or without AI.

## 🛠️ Troubleshoot

***Error:***

> Commit/Command failed: git status --porcelain fatal: not a git repository (or any of the parent directories): .git

***Reason:*** Not a git repository.

***Fix:*** Init Git. See the above Configuration ➡️ Initialize a local Git repo section.

---

***Error:***

> Commit/Command failed: git commit -m "commit: -base" Author identity unknown *** Please tell me who you are. Run git config --global user.email "you@example.com" git config --global user.name "Your Name" to set your account's default identity. Omit --global to set the identity only in this repository. fatal: unable to auto-detect email address (got 'xyz@system.(none)')

***Reason:*** Missing git identity.

***Fix:*** Set Git idenity. See the above Configuration ➡️ Git identity section.


## ☑️ Requirements

- VS Code v1.100.0 or higher.
- Git

## ⚖️ License

MIT

## 🏠 Home

[GitHub](https://github.com/sucom/vsce-git-snapshots)
