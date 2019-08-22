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
            - file is the rest of the hash

### We Need Something Else
The blob is missing information
- Filenames
- directory stuctures

Git stores this information in a **tree**.

### Tree
A **tree** contains pointers (using SHA1) 
- to blobs
- also to other trees
    - So why to other trees? It's because subdirectories can be nested.

#### Trees also contain metadata
- **type** of pointer (blob or tree)
- **filename** or directory name
- mode (executable file, symbolic link,...)
- git doesn't store empty directories; it's a limitation in the staging area which only keeps track of files

Trees and Blobs are a _directed graph_.

### Identical Content is Only Stored Once
Remember how content informs the SHA. Well running that hash on the same content will always return the same SHA. 
> In Git identitcal content is only stored once. Pointers will point to any repeated content.
> One of the most critcal features of Git, how Git saves as ton of space. So if we commit a blob or the tree, if it hasn't changed, we're just gonna point to the same copy. Which is why checking out branches in git is super fast.

![git pointers](https://user-images.githubusercontent.com/5563119/63214169-a3c3fa00-c0c9-11e9-9d93-660929d6b0db.png)
What is the difference between the blob and the SHA that refers to it?

>  The difference between the blob and the SHA. Is that the blob is the content and the SHA is essentially the key for that piece of content. However, the key is stored within that blob that tells it what content to associate itself with. (I may be misunderstanding this)

### Other Optimizations - Packfiles, Deltas
Optimzations are also build on how we work/develop, e.g. contents remain mostly similar
- Git objects are compressed
- As files change, their contents remain mostly similar.
- Git optimizes for this by compressing these files togethwer, into a **Packfile**
- The **Packfile** stores the object, and **"deltas"**, or the differences between one version of the file and the next.

- Packfiles are generated when:
    - You have too many objects, during garbage collection, or during a push to a remote.
