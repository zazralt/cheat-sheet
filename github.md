# GitHub Cheat-Sheet

## **Basic Git Configuration**

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "code --wait"
```

## **Repository Management**

| Task                    | Command                                      |
| ----------------------- | -------------------------------------------- |
| Clone a repo            | `git clone https://github.com/user/repo.git` |
| Create new repo (local) | `git init`                                   |
| Add remote              | `git remote add origin <url>`                |
| Check remotes           | `git remote -v`                              |

## **Staging & Committing**

```bash
git status                  # Check changes
git add <file>             # Stage file
git add .                  # Stage all
git commit -m "Message"    # Commit
git commit -am "Message"   # Add & commit tracked files
```

## **Branching**

```bash
git branch                 # List branches
git branch <name>         # Create branch
git checkout <name>       # Switch to branch
git checkout -b <name>    # Create and switch
git merge <branch>        # Merge branch into current
```

## **Pulling & Pushing**

```bash
git pull                   # Fetch & merge
git push                   # Push to default remote/branch
git push -u origin <branch>  # Push new branch
```

## **Tagging**

```bash
git tag <tagname>                   # Lightweight tag
git tag -a <tagname> -m "message"  # Annotated tag
git push origin <tagname>          # Push tag
```

## **Undoing Changes**

```bash
git restore <file>           # Discard uncommitted changes
git reset --hard HEAD        # Reset to last commit
git revert <commit>          # Create new commit that undoes
```

## **Git Log & Diff**

```bash
git log                      # Show commit history
git log --oneline --graph    # Compact view
git diff                     # Show unstaged changes
git diff --staged            # Staged changes
```

## **GitHub Specific**

| Task                     | How-To                                                           |
| ------------------------ | ---------------------------------------------------------------- |
| Fork a repo              | Use GitHub UI (button on repo page)                              |
| Create Pull Request (PR) | Push branch, then click "Compare & pull request"                 |
| Assign reviewers, labels | Available in PR interface on GitHub                              |
| GitHub Actions           | Automate workflows using `.github/workflows/*.yml`               |
| Issues                   | Use Issues tab to report/track bugs, assign labels and assignees |

## **.gitignore File**

Add files or patterns to ignore:

```
node_modules/
*.log
.env
.DS_Store
```

## **Common Shortcuts (GitHub UI)**

| Feature           | Location                |
| ----------------- | ----------------------- |
| Repo Insights     | "Insights" tab          |
| CI/CD Logs        | "Actions" tab           |
| Branch Protection | Settings > Branches     |
| Wiki              | "Wiki" tab (if enabled) |

## **GitHub CLI (Optional)**

```bash
gh auth login               # Authenticate
gh repo clone owner/repo    # Clone repo
gh pr create                # Create a pull request
gh issue list               # List issues
```
