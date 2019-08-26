# Fixing Mistakes
A few tools that we use to fix mistakes are:
- `checkout`
- `reset`
- `revert`
- `clean`

Fundamentally in order to understand how to fix mistakes, means having a very clear idea of how those three areas of where code lives work: The Working Area, The Staging Area, and The Repository, and how we can move data between them. The first way people learn to fix mistakes is usually with...

## Git Checkout
### Git Checkout
![](https://user-images.githubusercontent.com/5563119/63697140-25560f00-c7d1-11e9-9575-2054155dbfd6.png)
- Restore working tree files _or_ switch branches
- The action that is taken depends on the parameters
- `checkout` can move the head pointer and update the staging area and the working directory.
- If you're checking out a file, it can perform the same actions without moving the pointer.
- A key thing to remember here is how earlier in the course, we said the staging are isn't empty? It's a copy ofhe current commit, it has all the files that are in our current commit and thier SHA, this is an important concept to remember when using `git checkout` ...

### What Happens When you git checkout a branch?
1. Change HEAD to point to the new branch
2. Copy the commit snapshot to the staging area (or index)
3. Update the working area with the branch contents
![](https://user-images.githubusercontent.com/5563119/63697497-e4122f00-c7d1-11e9-9a94-95683ce5e50f.png)
- Remember when we tried to checkout a branch and git warned us that our files will be overwriten? 
- Changes in the staging area are also capped unless they conflict with any changes in the branch you're abotu to checkout. 
- Checking out a branch is generally a pretty safe operation; git is going to warn you if you're going to lose data.

### What Happens When you git checkout --file?
![](https://user-images.githubusercontent.com/5563119/63697880-9518c980-c7d2-11e9-941d-dd2eb2d821e0.png)
Replace the working area copy with the version from the current staging area.
- git recommends this command to be run when you want to remove a file: replace the files in your working area with clean files from the staging area
- **This operation overwrites files in the working directory without a warning and no way of recovering them!**
- It's a destructive operation with no warning. 

### Git checkout: Overwrite Files with Staing Area Copy
**This operation overwrites files in the working directory without warning!**
![](https://placehold.it/400x40/ff6600/000?text=WARNING!)  
- Overwrite the working area file with the staging area version from the last commit.  
    - `git checkout -- < file-path >`  
        - A lot of people get confused about the `--` the two dashes and what they mean. `--` signifies the end of a command operation and the start of positional parameters. So if we had a branch and a file of the same name, `git checkout` can possibly be ambiguous. So with the `--` we're specifying that the next argument is a file in this case and not a branch.

### What Happens When you git checkout < commit > --file?
![](https://placehold.it/400x40/ff6600/000?text=WARNING!)  
**This operation overwrites files in the working directory and the staging area without warning!**
1. Update the staging area to match the commit
2. Update the working area to match the staging area.

- When you're running git checkout and you have unsaved changes, it's time to stop, pause, stash, commit them, do whatever you need to do to get your code in a safe place because that command is very destructive.

### Git checkout: From a specific commit
![](https://placehold.it/400x40/ff6600/000?text=WARNING!)  
**This operation overwrites files in the working directory and the staging area without warning!**
- checkout a file from a specific commit
    - _copies to both working area & staging area_
    - `git checkout < commit >  -- < file path >`

- Restore a delete file
    - `git checkout < deleting_commit >^ -- < file_path >`

## Git Clean & Reset
### Git Clean
- Git clean will clear your working area by **deleting** untracked files.
- WARNING: This operation cannot be undone 

- Use the `--dry-run` flag to see what would be deleted
    - the `-f` flag to do the deletion
    - The `-d` flag will clean directories 

![](https://user-images.githubusercontent.com/5563119/63699287-5d5f5100-c7d5-11e9-9263-4812b3806c6e.png) 

## Git Revert

## Fixing Git Mistakes Solution