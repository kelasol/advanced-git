# Rebase and Amend

## Git Amend
### Amend a Commit
- Amend is a quick and easy shortcut that lets you make changes to the previous commit.
![](https://user-images.githubusercontent.com/5563119/63740220-fb3e3480-c844-11e9-87e3-9f458fd510f0.png)
The reason you have different SHAS, is because commits can't be edited...
- An amend is king of like a mini rebase

### Commits Can't be Edited!
- Remember, commits can't be edited!
- A commit is referenced by the SHA of all its data.
- Even if the tree the commit points to is the same, and the author is the same, the date is still different!
- A new commit is created
 ![](https://user-images.githubusercontent.com/5563119/63740453-f4fc8800-c845-11e9-9bad-4a6fa39dd58e.png)

## Rebase
### What is Rebase Anyway?
- Imagine our tech_posts and master branch have diverged
- We don't want a messy merge commit in our history
- We can pull in all the latest changes from mastewr, and apply our commits on top of them by changing the parent commit of our commits.
- **Rebase = Give a commit a new parent** (ie. a new base commit)

### Rebase: Rewinding Ahead
- The first thing that `rebase` does is it rewinds HEAD
- if I want to rebase from master and master has one new commit since I've made my tech_posts branch.
- first git is going to rewind HEAD back to master, it's going to end up replaying my commits on top of HEAD.
- Now original commit on our branch is gone and we've created a new commit, a copy of that commit on the tech_posts branch and that new tech_posts branch is up to date on the latest from master.

### Merge vs Rebase
- So in our example below, it would be a merge commit and it's okay to have in your history, but if you're contributing to open source, that's not really ideal. We mostly want to keep our history neat and clean. It's somewhat like a fast-forward.
![](https://user-images.githubusercontent.com/5563119/63740922-c384bc00-c847-11e9-96b3-cdea413fab2d.png)

### Power of Rebasing - Replay Commits
- Commits can be:
    - edited
    - removed
    - combined
    - re-ordered
    - inserted
- Before they're _"replayed"_ on top of the new HEAD.

### Interactive Rebase (rebase -i or rebase --interactive)
- Interactive rebase opens an editor with a list of "todos"
    - in the format of < command > < commit > < commit msg >
    - git will pick the commits in the specified order, or stop to take an action when editing or a conflict occurs.

- Interactive rebase with a shortcut:
    - `git rebase -i < commit_to_fix >^
    - (the ^ specifies the parent commit)

### Rebase Options
- `pick`
    - keep this commit
-`reword`
    - keep the commit, just change the message
- `edit`
    - keep the commit, but stop to edit more than the message.
- `squash`
    - combine this commit with the previous one. stop to edit the message
- `fixup`
    - combine this commit with the previous one. keep the previous commit message
- `exec`
    - run the command on this line after picking the previous commit
- `drop`
    - remove the commit (tip: if you remove this line, the commit will be dropped too!)

### Tip: Use Rebase to Split Commits
Editing a commit can also split it up into multiple commits!
You want to make sure your commit is only one logical idea/feature.

## Fixup and Autosquash
### Tip: "Amend" Any Commit with Fixup & Autosquash
What if we want to amend an arbitrary commit?

1. `git add new files`
2. `git commit --fixup < SHA >`
    1. this creates a new commit, the message starts with 'fixup!'
3. `git rebase -i --autosquash < SHA >^`
4. git will generate the right todos for you! just save and quit.

Note on (3)Make sure you specify the parent of the SHA chosen, otherwise it won't work.

### Fixup & Autosquash Example
You don't have to interactive rebase, if you just want to modify one commit:
![](https://user-images.githubusercontent.com/5563119/63741309-6db11380-c849-11e9-9853-f0df3418bb1a.png)

### Rebase --exec (execute a command)
- A way for git to run a command after every rebase action, e.g. run this test.

## Abort 
### Pull the Rip Cord!
Remember, there is a safety option, if you are doing a rebase and before it's done things are really going wrong with you you can just abort...
- At any time before rebase is done, if things are giong wrong:
    - `git rebase --abort`

### Rebase Pro Tip
- Before you rebase / fixup / squash / reorder:  
- Make a copy of your current branch:
    - `git branch my_branch_backup`
- `git branch` will make a new branch, without switching to it

- if rebase "succeeds" but you messed up...
- `git reset my_branch_backup --hard`

- you're back in business!
- rebase doesn't have to be scary, this is a really great way of playing around with it without making your changes final or permanent. 

### Rebase Advantages
- Rebase is incredibly powerful!
- You can slice and dice your git history.
- It's easy to fix previous mistakes in code.
- You can keep your git history neat and clean.
- consistent with the mantra of committing early and often: and locally rebase to your heart's content, once you're ready to share your changes with your co-workers, they don't need to know you made 5 commits in an hour. You can just present them with a pretty, neat history.

### Commit Early & Often vs. Good Commits
- Git Best Practice:
    - "commit often, perfect later, publish one"

- When working locally:  
    - Commit whenever you make changes!  
    - It'll help you be a more productive developer.  
- Before pushing work to a shared repo:  
    - rebase to clean up the commit history.  

- Don't just use rebase to squash all your commits into one commit; it makes it harder to debug. 

### Warning! Never Rewrite Public History!
- Rebase commits are copes
- If other people are working on the same repository they would be working on different commits
- You could cause massive merge conflicts
- Even worse, you can cause people to lose their work!

## Git Rebase and Amend Solution

In CMDER, if youre echoing things into a file:
`echo "Hello, World!" > hello.txt`
You actually don't need the quotes. You can just write: `Hello, World!` as is.
- `>` will write to the file given as an argument
- `>>` will append to the file given as an argument 

- when rebasing interactively these all list in top-down order so different from `git log`,
- Interactively rebasing is 

- Rebase is not a dirty word, Nina uses it almost everyday. Commit early and often on your local branch. Make updates, always back up your work, and when you need to share it with coworkers then you rebase it.

