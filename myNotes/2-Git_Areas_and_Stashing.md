## Git Areas and Stashing
 ### Working Area, Staging Area, Repository
 These are the three areas where code lives:
 1. Working Area (aka Working Tree)
 2. Staging Area (aka Cache or Index)
 3. Repository (aka Repo)

#### The Working Area
- The files in your working area that are _also not_ in the staging area are not handled by git
- Also called **untracked files**. 
- working area is like your scratch space, where you can edit/modify/delete content

#### The Staging  Area (aka Index, Cache)
- What files are going to be part of the next commit
- The staging area is how git knows what will change between the current commit and the next commit

#### The Repository
- The files git knows about
- Contains all of your commits
- Contain a snapshot of what your working and staging area look like at the time of the commit
- It's in your `.git` directory

#### Closer Look: The Staging Area
:star: The staging area is how git knows what will change between the current commit and the next commit.
- Tip: a "clean" staging area isn't empty!
- Consider the baseline staging are as being an exact copy of the latest commit. 
    - It contains a list of files that were in your last commit as well as the SHA1 hash of those files as they were in their last commit
- The staging area (the index) is actually a binary file in the .git directory.
- When you add/remove/rename files to the staging area, Git knows because the SHAs are now different.

#### Moving Files In and Out of the Staging Area
- add a file to the next commit:
    - `git add < file >`    
- delete a file in the next commit:
    - `git rm < file >`
- rename a file in the next commit:
    - `git mv < file >`

#### Git add -p
- One of Nina's favorite tools
- Allows you to stage commits in hunks
- interactively! Let's you cherry-pick what to commit.
- It's especially useful if you've done too much work for one commit
- a great demonstration on the utility of git's staging area
    - use the `?` to print the key for what the commands are.
    - use `q` to exit out

#### "Unstage" Files from the Staging Area
- Not removing the files
- You're just replacing them with a copy that's currently in the repository.
![](https://user-images.githubusercontent.com/5563119/63553111-4deaba00-c4ee-11e9-96df-d50ac03b0d47.png)
- We add from Working to Staging area
- We commit from Staging to repo
- `git commit -a` does it in one go (not advised)
- We checkout from Staging to Working
- We checkout branch from Repo to Working

## Stashing
There is one more place that Git stores code, that's through git stash.

### Git Stash
- The git stash is a way to save uncommited work
- The stash is **safe** from most, destructive operations (like reset and checkout)

#### Git Stash - Basic Use
- stash changes
    - `git stash`
- list changes
    - `git stash list` 
- show the contents
    - `git stash show stash@{0}`
- apply the last stash
    - `git stash apply`
- apply a specific stash
    - `git stash apply stash@{0}`

#### Advanced Stashing - Keeping Files
- Keep untracked files
    - `git stash --include-untracked`
- Keep all files (even ignored ones!)
    - `git stash --all`

#### Advanced Stashing - Operations
- Name stashes for easy reference
    - `git stash save "WIP: making progress on foo"`
 
- Start a new branch from a stash
    - `git stash branch < optional branch name >`

- Grab a single file from a stash
    - `git checkout < stash name  > -- < filename >`
    - if you have this same file in working/staging it will overwrite, so use with caution

#### Advanced Stashing - Cleaning the Stash
- Remove the last stash and applying changes:
    - `git stash pop`
    - Tip: doesn't remove if there's a merge conflict
- Remove the last stash
    - `git stash drop`
- Remove the nth stash
    - `git stash drop stash@{n}`
- Remove all stashes
    - `git stash clear`

#### Examing Stash Contents - Git show
If we want to look into the contents of a stash we can do that in two ways:
- `git stash list`
- `git stash show stash@{2}`

#### Git Stash - What I use
- Keep untracked files
    - `git stash --include-untracked`
- Name stashes for easy reference
    - `git stash save "WIP: making progress on foo"`
- You can also you the -p flag on git stash to selectively add files to stash just like we did with commit -p