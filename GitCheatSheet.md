# Git — Cheat Sheet

## General Git Commands

```
> git config --global user.name "<user name>"              # Set Git user name.
> git config --global user.email "<user e-mail>"           # Set Git user e-mail.
> git config --global core.editor <editor>                 # Set Git editor.
> git config --global init.defaultBranch main              # Set "main" to be the default branch name.
> git config list                                          # List all globally defined variables.
> git init                                                 # Create new Git repository.
> git init --bare                                          # Create new server-side Git repository, without working directory.
> git clone <url>                                          # Clone remote Git repository at <url>.
> git clone --depth=<n> <url>                              # Clone remote Git repository at <url>, making only a shallow clone with the last <n> commits.
> git remote -v                                            # Show remote tracking-branches.
> git remote add <remote> <url>                            # Add a remote <remote> for Git local repository at <url>.
> git remote remove <remote> <url>                         # Remove remote <remote> for Git local repository.
> git fetch                                                # Fetch from remote Git repository.
> git fetch <remote>                                       # Fetch from specific <remote> Git repository.
> git pull                                                 # Pull from remote Git repository and apply to working directory.
> git push                                                 # Push staging to remote Git repository.
> git push -f                                              # Force push to remote Git repository (will upset local repositories of others).
> git log                                                  # Show commit log.
> git reflog                                               # Show reflogs (SHA-1 hashes).
> git status                                               # Show status of working directory and staging.
> git add <file>...                                        # Add changes in <file> or multiple <file> from working directory to staging.
> git add -u                                               # Add changes in already tracked files to staging.
> git commit -m "<msg>"                                    # Commit changes to staging, providing commit message <msg>.
> git commit --amend                                       # Amend last commit (preferably before force pushing).
> git commit --amend --author="Author <name>@domain.net"   # Amend author of last commit (preferably before force pushing).
> git diff                                                 # Show differences in working directory with HEAD.
> git diff --cached                                        # Show differences of staging with HEAD.
> git reset --soft HEAD~1                                  # Revert last commit, keeping changes in working directory.
> git reset --hard HEAD~1                                  # Revert last commit, removing changes in working directory.
> git reset HEAD <file>                                    # Remove single <file> from staging.
> git rebase -i HEAD~<n>                                   # Rebase last <n> commits interactively.
> git rebase -i --root                                     # Rebase everything from first commit interactively.
> git rebase --abort                                       # Abort rebasing.
> git pull --rebase                                        # Pull rebase from remote.
```

## Checkout

```
> git checkout -f                                          # Revert all changes in working directory.
> git checkout HEAD <file>...                              # Revert changes in <file> or multiple <file>.
> git checkout HEAD *                                      # Revert all file changes in current directory.
> git checkout <sha>                                       # Checkout specific commit with SHA-1 hash <sha>.
```

## Branches

```
> git branch <branch>                                      # Create new <branch>.
> git branch {-u|--set-upstream-to} <remote>/[<branch>]    # Set upstream <remote> for current branch or possibly specific <branch>.
> git merge <branch>                                       # Merge current branch with other <branch>.
> git branch {-d|-D} <branch>                              # Delete <branch>.
> git branch {-d|-D} -f <branch>                           # Delete <branch>, forced when branch has not been merged.
> git checkout <branch>                                    # Checkout <branch> locally.
> git checkout -b <branch>                                 # Checkout <branch> locally.
> git checkout --track <remote>/<branch>                   # Create and checkout local <branch>, tracking <remote> tracking <branch>.
> git push <remote> [<branch>]                             # Push staging to specific <remote> Git repository, possibly at specific <branch>.
> git push {-u|--set-upstream} <remote> [<branch>]         # Push staging to specific <remote> Git repository, possibly at specific <branch>;
                                                           # Setting up for future Git pull commands.
> git push <remote> :<branch>                              # Delete <branch> remotely on <remote> Git repository.
> git push <remote> --delete <branch>                      # Delete <branch> remotely on <remote> Git repository.
> git remote prune                                         # Clean up references to remote branches no longer existing on the remote Git repository.
```

## Tags

```
> git tag                                                  # List tags.
> git tag <tag>                                            # Tag current commit with <tag>.
> git tag <tag>                                            # Tag with <tag> specific commit with SHA-1 hash <sha>.
> git push --tags                                          # Push tags to remote Git repository.
```

[![FOSS Cheat Sheets — License](https://img.shields.io/badge/LICENSE-CC0--1.0-blue?style=for-the-badge&logo=creativecommons&logoColor=white)](LICENSE.md)
