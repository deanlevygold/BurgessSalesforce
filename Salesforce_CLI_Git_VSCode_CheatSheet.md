# 🚀 Salesforce CLI + Git + VS Code Cheat Sheet

Your one-stop reference for managing Salesforce metadata deployments with free tools.

---

## 🧭 1. Navigation & File Basics

| Command | Description |
|----------|--------------|
| `pwd` | Print working directory. |
| `ls` | List files/folders in current directory. |
| `ls -a` | Include hidden files (like `.git` or `.bashrc`). |
| `cd foldername` | Change into a folder. |
| `cd ..` | Move up one level. |
| `mkdir foldername` | Create a new folder. |
| `rm -rf foldername` | Delete folder and contents (careful!). |
| `nano filename` | Edit a text file directly in terminal. |
| `source ~/.bashrc` | Reloads Bash aliases after editing. |

---

## 💻 2. Git & GitHub Commands

| Command | Description |
|----------|--------------|
| `git init` | Initialise a new Git repository. |
| `git clone <repo-url>` | Clone a GitHub repo to your machine. |
| `git status` | Show tracked/untracked files. |
| `git add .` | Stage all files for commit. |
| `git commit -m "Message"` | Commit staged changes. |
| `git push origin <branch>` | Push commits to GitHub. |
| `git pull origin <branch>` | Pull and merge latest code. |
| `git checkout -b <branch>` | Create and switch to a new branch. |
| `git checkout <branch>` | Switch branches. |
| `git merge <branch>` | Merge another branch into current. |
| `git branch -a` | List all branches. |
| `git diff` | Show file diffs. |
| `git log --oneline --graph --decorate` | Visual commit history. |
| `git diff --name-only <main>...<branch>` | Visual commit history. |

---

## 🧩 3. Salesforce CLI (sf) Core Commands

| Command | Description |
|----------|--------------|
| `sf --version` | Check CLI version. |
| `sf org login web --alias <alias>` | Login to a Salesforce org via browser. |
| `sf org list` | List all authenticated orgs. |
| `sf org open --target-org <alias>` | Open org in browser. |
| `sf project retrieve start --manifest manifest/package.xml --target-org <alias>` | Retrieve metadata from org. |
| `sf project deploy start --manifest manifest/package.xml --target-org <alias>` | Deploy metadata to org. |
| `sf deploy metadata validate --manifest manifest/package.xml --target-org <alias>` | Validate deployment (check-only). |
| `sf metadata type list --target-org <alias>` | List available metadata types. |
| `sf apex run test --target-org <alias>` | Run all Apex tests. |
| `sf data query -q "SELECT Id, Name FROM Account LIMIT 10" --target-org <alias>` | Run SOQL query. |

---

## ⚙️ 4. Folder Structure & Files

| File/Folder | Description |
|--------------|-------------|
| `force-app/main/default/` | Main metadata folder. |
| `manifest/package.xml` | List of metadata components to deploy/retrieve. |
| `sfdx-project.json` | Project definition and API version. |
| `.gitignore` | Files/folders ignored by Git. |
| `.bashrc` | Stores custom command aliases. |

---

## ⚡ 5. Salesforce Aliases (Shortcuts)

| Command | Description |
|----------|--------------|
| `sfdev <cmd>` | Run any Salesforce CLI command from project folder. |
| `sfretrieve-dev` | Retrieve metadata from dev org. |
| `sfretrieve-deploycheck` | Retrieve from DeployCheck sandbox. |
| `sfretrieve-uat` | Retrieve from UAT. |
| `sfretrieve-prod` | Retrieve from Production. |
| `sfdeploy-deploycheck` | Deploy to DeployCheck sandbox. |
| `sfdeploy-uat` | Deploy to UAT sandbox. |
| `sfdeploy-prod` | Deploy to Production. |
| `sflist` | List connected orgs. |
| `sforg-open-dev` | Open developer org in browser. |
| `sforg-open-prod` | Open Production org. |

---

## 🧠 6. VS Code Shortcuts

| Shortcut | Action |
|-----------|--------|
| **Ctrl + Shift + P** | Command Palette. |
| **Ctrl + `** | Toggle terminal. |
| **Ctrl + Shift + G** | Source Control view. |
| **Ctrl + Shift + E** | File Explorer. |
| **Ctrl + P** | Quick Open. |
| **Ctrl + /** | Comment/uncomment lines. |
| **Right-click → Compare with Selected** | Side-by-side file comparison. |

---

## 🔐 7. Common Git Issues

| Issue | Fix |
|-------|-----|
| "No file found at manifest/package.xml" | Ensure you run CLI from project folder. |
| LF/CRLF warnings | `git config core.autocrlf true` or ignore. |
| Untracked files present | Run `git add .`. |
| `.gitignore` excludes force-app | Remove that line from `.gitignore`. |
| Missing "Accept Both Changes" | Not a merge conflict — merge manually. |

---

## ⚡ 8. Daily Workflow Summary

| Step | Action | Command |
|------|---------|----------|
| 1 | Login to orgs | `sf org login web --alias deandev` |
| 2 | Retrieve from Prod | `sf project retrieve start --manifest manifest/package.xml --target-org prod` |
| 3 | Commit baseline | `git add . && git commit -m "Baseline: Production snapshot"` |
| 4 | Retrieve from Dev | `sf project retrieve start --manifest manifest/package.xml --target-org deandev` |
| 5 | Create feature branch | `git checkout -b feature/deandev-sync` |
| 6 | Commit and push | `git add . && git commit -m "Deandev changes" && git push` |
| 7 | Validate deploy | `sfdeploy-deploycheck` |
| 8 | Merge to UAT and Prod | Use Git merge commands and PRs. |

---

## 🧰 9. Extra Useful Commands

| Command | Description |
|----------|--------------|
| `sf data tree export --query "SELECT Id, Name FROM Account" --output-dir data` | Export sample data. |
| `sf data tree import --input-dir data --target-org <alias>` | Import sample data. |
| `sf org logout --target-org <alias>` | Log out of an org. |
| `sf env log tail --target-org <alias>` | Stream real-time debug logs. |
| `sf apex run --file scripts/apex/script.apex --target-org <alias>` | Run Apex script. |
| `sf help <command>` | Get help on a specific command. |

---

## ✅ TL;DR (Most Common)

```bash
# Login to your dev org
sf org login web --alias deandev

# Retrieve metadata from Dev
sfretrieve-dev

# Commit to Git
git add .
git commit -m "Retrieve latest metadata from deandev"
git push origin feature/deandev-sync

# Validate deployment to QA
sfdeploy-deploycheck --checkonly

# Generate delta and retrieve in one flow
sf sgd source delta --from HEAD --to origin/prod --output-dir delta-prod-diff
sf project retrieve start --manifest delta-prod-diff/package/package.xml --target-org prod

```

---
