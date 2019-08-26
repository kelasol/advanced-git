# Merging and Rebasing
## Merging and Fast Forward
### Under the Hood - Merge Commits are Just Commits
- Merge commits are just commits, they just happen to have more than oen parent
- I think in most modern Git workflows, most merge commits probably have two parents (possible to have 3,4+)
- The Merge commit is just a marker of when a new feature merged into master
![](https://user-images.githubusercontent.com/5563119/63645157-bda6a380-c6ac-11e9-8898-7de974c5ca20.png)

### Fast Forward
Fast-forward happens when there are no commits on the base branch that occured after the feature branch was created.
Occasionally, you check out master, and merge in a feature branch, and if there haven't been any additional changes to master. Git will show you this message saying that is has fast-forwarded. This happens when there is a clear path, from the tip of the current branch to the tip of the target branch.
- After say we branched off to our feature branch and there were no other commits to master. 
- During a fast-forward commit, we add the new commits on top of the master branch and then we just move the master pointer. In this case we didn't have a merge commit, git knew how to just move the pointer to the end of the feature branch.
    - The problem is that during these FF commits: we can possibly lose track of a feature that was merged back into master, because when you are working on a feature and you merge it back into master, you really want to have a clear delineator of work that was done in that specific branch. We won't be able to identify which bugs emerged from which feature if there's no merge commit. In order to avoid this...

### Git merge --no-ff (No Fast Forward)
- To retain the history of a merge commit, even if there are no change to the base branch:
    - use `git merge --no-ff`
- This will _force_ a merge commit, even when one isn't necessary.
![](https://user-images.githubusercontent.com/5563119/63645222-440fb500-c6ae-11e9-9df5-52d1722af55a.png)

## Merge Conflicts
### Merge Conflicts
This happens when we try to merge but our files have diverged and changes are not comapatible.
- Attempt to merge, but files have diverged.
- Git stops until the conflicts are resolved.

### Git RERERE - REuse REcorded REsolution
- a really helpful tool  
- git saves how you resolved a conflict
- next conflict: reuse the same resolution

- useful for:
    - long lived feature breanc (like a refactor)
    - resbasing
#### How do we use it? 
Turn it on:
- `git config rerere.enabled true`
- use `--global` flag to enable for _all_ projects

- When you commit the conflict resolution, it's recorded, and says so in terminal:  
`Recorded resolution for < feature name >`

- The next time we have the same conflict, git will automatically apply the last resolution, but 
![](https://user-images.githubusercontent.com/5563119/63650738-e6f21e80-c702-11e9-95f3-52689e3ec1ed.png)

## Merging and ReReRe Exercise
- Nina like having ReReRe on on a project by project basis. Doesn't like having it on automatically (globally). If something does go wrong, Git does allow you to delete those saved resolutions.

## Merging and ReReRe Solution
Note: If using CMDER for terminal. Instead of `git reset --hard HEAD^`you can use: `git reset --hard HEAD~1`. On Mac, `HEAD^` should work as expected.
- Another neat trick is if you checkout between branches frequently.  
`git checkout -`  
This will checkout the last branch you were on, the previous branch using the -.