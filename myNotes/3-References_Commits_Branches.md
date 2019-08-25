# References, Commits, Branches

## References
References are pointers to commits. We already learned that there are 3 types of git references

### Three Type of Git References
- Tags & Annotated Tags
- Branches
- HEAD

### What's a Branch?
- A **branch** is just a pointer to a particular commit
- The pointer of the current branch changes as new commits are made

### What is HEAD?
- **HEAD** is how git knows what branch you're currently on, and what the next parent will be.
- It's a pointer
    - It usually points at the _name_ of the current branch.
    - But, it can point to a commit too (detached HEAD).
- It moves when:
    - You make a commit in the currently active branch
    - When you checkout a new branch

## Tags & Annotated Tags
### Lightweight Tags
- **Lightweight tags** are just a simple pointer to a commit.
- They get created when you create a tag with no arguments, it captures the value in HEAD
- continuing with our previous example, if we were to checkout master: `git checkout master`
- `git tag my-first-commit` will now just point to the value in HEAD.

### Annotated Tags: git tag -t
- Point to a commit, but store additional information
    - author, message, date
- Created using the `-a` flag
- You can pass in `-m`, just like a commit, to specify a message:
`git tag -a v1.0 -m "Version 1.0 of my blog"`

    `> git tag`  <---- Is How you list your tags; below is output --v  
        `my-first-commit`  <--- The first tag we had previously created  
        `v1.0`  <--- The annotated tag we just created 
 
To get all the useful info out of the annotated tag we use: `git show + tag name`  
    `git show v1.0`

In practice lightweight tags not used too often in practice, more useful for yourself.
- Annotated tags are much more useful

### Working with Tags
- List all the tags in a repo
    - `git tag` 
- :star: List all tags, and what they're point to (pretty useful command)
    - `git show-ref --tags`
- List all the tags pointing to a commit
    - `git tag --points-at < commit >`
- Looking at the tag, or tagged contents:
    -  `git show < tag-name >`

### Tags & Branches
- **Branch**
    - Thew current branch pointer moves with every commit to the repository
- **Tag**
    - The commit that a tag points doesn't change.
    - It's a snapshot!

Two important pieces of info that separate what a tag is and what a branch is:
- A branch, when you're on a branch, the current pointer, the branch pointer it moves with every new commit to the repository. You use branches when your branch will change, when new commits will be added. Tags are a pointer to a commit, a snapshot, tags aren't meant to change. You tag v1 of your release. You don't move you tag to another commit.

### Detached Head & Dangling Commits
- Sometimes you need to checkout a specific commit (or tag) instead of a branch
- git moves the HEAD pointer to that commit
- as soon as you checkout a different branch or commit, the value of HEAD will point to the new SHA
- There is no reference pointing to the commits you made in a detached state.
![](https://user-images.githubusercontent.com/5563119/63643548-9093ca00-c687-11e9-8583-3ad33724aad9.png)

### HEAD-LESS / Detached HEAD
Save your work:
- Create a new branch that points to the last commit you made in a detached state.
    - `git branch < new-branch-name > < commit >`
- Why the last commit?
    - Because the other commits point to their parents. So we don't have to save all commits individually. 

### Dangling Commits
Discard your work:
- If you don't point to a new branch at those commits, they will no longer be referenced in git (**dangling commits**).
- Eventually, they will be garbage collected
- Git does it's own garbage collection (runs every few weeks, can be run manually)
- It's possible to recover these after GC (with ref logs, will talk about later)

#### References Exercise 