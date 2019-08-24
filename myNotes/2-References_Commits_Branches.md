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
    - It's a snapshot.
    
Two important pieces of info that separate what a tag is and what a branch is:
- A branch, when you're on a branch, the current pointer, the branch pointer it moves with every new commit to the repository
