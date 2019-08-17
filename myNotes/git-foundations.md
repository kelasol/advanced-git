# Git Foundations

## Course Agenda
### Class Overview - Part 1
- What is Git? 
- Working Area, Staging Area, Repository
- Staging Area Deep Dive
- Reference, Commits, Branches
- Stashing

### Part 2
- Merging + Rebasing
- History + Diffs
- Fixing Mistakes
- Rebase
- Forks, Remote Repositories

### Part 3
- The Danger Zone
- Advanced Tools
- Customization - Config, Ignore, Hooks, Templates
- Social Git: Integrating HitHub with CI Tools
- Advanced GitHub: Working with the GitHub API

### Why Use the Command Line?
- CLI much better for learning what is happening under the hood, use tools as they were designed not GUIs

## Data Storage

### How does Git Store Information?
- At its core, Git is like a key value store.
    - The **Value** = **data**
    - The **Key** = **Hash of the Data**
- You can use the key to retrieve the content.

### The Key - SHA1
- It is a cryptographic hash function
- Given a piece of data, it produces a 40-digit hexadecimal number
- This value should always be the same if the given input is the same.
- Sometimes system like this is called a _content addressable system_ and that's because you can also use the content to generate the key.

## Git Blobs and Trees
The way that Git stores things is as _Git Objects_ and a very basic one is called a Blob...

### The Value - Blob
- Git stores the _compressed_ data in a blob, along with metadata in a header:
    - the identifier blob
    - the size of the content
    - the \0 delimiter (string terminator in C)
    - content

### Under the Hood - Git Hash - Object
Asking Git for the SHA1 of contents:
- The way that Git does this under the hood is with a plumbing command:
    ``` [...] git hash-object ---stdin```
- If you run the hash method on the same object twice you will always get the same result.
    - blobs usually unique in Git
    - Likelyhood of collision very small

### Where Does Git Store its Data?
- In the .git directory when we init
    - This in turn contains all of the data about our repository

### Where are the Blobs Stored?
    - If you tree command in the .git dir. You can see 
        - Objects
            - (Starts with 8a) (Directory is first two characters of hash)
                - file is the rest of the has

@@