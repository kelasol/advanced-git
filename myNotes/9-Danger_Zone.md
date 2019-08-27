# Danger Zone
## Local and Remote Destructive Operations
### Local Destructive Operations
-`git checkout -- < file >`
    - If the is present in the staging area, it'll be overwritten.
-`git reset --hard`
    - Will overwrite changes that are staged and in the working area.

- Unless changes are stashed, there's _no way_ of getting them back!
- Tip: use `git stash --include-untracked` to include working area changes in your stash.

- Remember the mantra: commit early and often and remember you can clean up your history at any point in time.

### Remote Destructive Operations - Rewriting History
- There are many operations taht can rewrite history:
    - `rebase`
    - `amend`
    - `reset`

- If your code is hosted or shared:
    - **Never run `git push -f`**
 
## Recover Lost Work
### Recover Lost Work
- Use `ORIG_HEAD`
    - The commit `HEAD` was pointing to before a:
        - `reset`
        - `merge`
    - Check for repository copies:
        - github
        - coworker

### How to use ORIG_HEAD to Undo a Merge?
- Use `ORIG_HEAD` to undo merges
- `git reset --merge ORIG_HEAD`
- use `--merge` flag to preserve any uncommited changes

### Using Git Reflog and '@'Syntax
- By default, git keeps commits for about 2 weeks.
- If you need to go back in time, and find a commit that's no longer 
referenced, you can look in the reflog.
- Detached HEAD? Dangling commits? Reflog is how you are going to get them back.
- The syntax of reflog is different.
    - `HEAD@{2} means "the value of HEAD 2 moves ago"
