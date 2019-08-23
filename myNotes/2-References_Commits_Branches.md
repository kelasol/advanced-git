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