## Self-Assessment & Review of Git Foundations
---
<br>
<details>
    <summary><b>How does Git Store Information? </b> </summary>
    In what are essentially key-value pairs: <br>
    <ul> 
        <li> The Value = data  
        <li> The Key = Hash of the Data
    </ul>
    Git stores things as <i>Git Objects</i>: blobs, trees, and commits are all instances of git objects.
</details>

<br>
<details>
    <summary><b>Why can a system like Git be referred to as a <i>content addressable</i> system?</b> </summary>
    This value should always be the same if the given input is the same.
Sometimes system like this is called a content addressable system and that's because you can also use the content to generate the key.
</details>

<br>
<details>
    <summary><b>What is a blob? What does it hold?</b> </summary>
    A blob is a type of <i>Git Object</i>. It contains at least 3 other pieces of metadata in addition to the contents of the data itself. <br>
    <ol> 
        <li> the indentifier blob
        <li> the size of the content
        <li> the \0 delimiter (string terminator in C)
        <li> the compressed data or content
    </ol>
</details>

<br>
<details>
    <summary><b>Where Does Git Store its Data?</b> </summary>
    In the .git directory when we init. 
    This in turn contains all of the data about our repository
</details>

<br>
<details>
    <summary><b>Where, more specifically, are blobs stored?</b> </summary>
    If you tree, your .git directory you will see a dir called objects that will contain the first two values of the hash, the file is the rest of the hash.
</details>

<br>
<details>
    <summary><b>What information from blobs is missing that requires git to have something else? Where is this information managed?</b></summary>
        <span>&#8226;</span> Filenames <br>
        <span>&#8226;</span> Directory structures
        This additional information is held by trees
</details>

<br>
<details>
    <summary><b>What does a tree hold? Used for?</b></summary>
    A tree contains <i>pointers</i>. To blobs and also to other trees.
    It holds pointers to other trees because subdirectories can be nested.
</details>

<br>
<details>
    <summary><b>What else do trees contain?</b></summary>
    A tree also contains metadata:<br>
    <span>&#8226;</span> type of pointer (blob or tree)<br>
    <span>&#8226;</span> File name or directory name<br>   
    <span>&#8226;</span> mode (executable file, symbolic link)...<br>
</details>

<br>
<details>
    <summary><b>What is one of the most critical design features of Git?</b></summary>
    One of the most critcal features of Git, how Git saves as ton of space. So if we commit a blob or the tree, if it hasn't changed, we're just gonna point to the same copy. Which is why checking out branches in git is super fast.
</details>

<br>
<details>
    <summary><b>What is the difference between the blob and the SHA that refers to it?</b></summary>
    The difference between the blob and the SHA. Is that the blob is the content and the SHA is essentially the key for that piece of content. The blob is essentially a pointer to this number (the SHA).
</details>

<br>
<details>
    <summary><b>How would you say the design of Git compliments the iterative development process of code writing? What is a Packfile?</b></summary>
     As files change, their contents remain mostly similar as you tend to add to them and modify them (more than not) in gradual increments. This allows git to optimize files by compressing them together into what is referred to as a Packfile.
</details>

<br>
<details>
    <summary><b>If the Packfile is the thing that stores the object, what are deltas for?</b></summary>
    Deltas are just what we call the differences between one version of the file and the next. Delta = difference between old and new versions; the diff of what has changed.
</details>

<br>
<details>
    <summary><b>When are Packfiles generated?</b></summary>
     When you have too many objects, during garbage collection, or during a push to a remote.
</details>

<br>
<details>
    <summary><b>What is a commit? What does it contain?</b></summary>
    A commit is just a pointer to a tree. It like most other git objects, contains metadata. Things like : and contains metadata: author and committer, date, message, parent commit (one or more). The SHA1 of the commit is the hash of all this information.
</details>

<br>
<details>
    <summary><b>What's a more useful or precise way to think of commits?</b></summary>
    Commits point to a parent commit or a tree, and the tree is just a snapshot of what the repository staging area looked like at the time of the commit. A commit then is a snapshot of code, a combination of the changes (deltas) from the staging area on the previous commit.
</details>
 
<br>
<details>
    <summary><b>If we are wanting to look at some of the other git objects and their contents we can use what command and corresponding flags?</b></summary>
    If we are wanting to look at some of the other git objects and their contents we can use  <i>git cat-file</i> and the -t and -p flags on the hash identifier. <br> An example would be: "git catf-file t 980a0" <br>
    You could do the same with trees which would print out: the mode (a reference number for its type), the blob stored, and the file that it points to. 
</details>

<br>
<details>
    <summary><b>Why can't we change commits?</b></summary> <br>
- If you can change any data about the commit, the commit will have a new SHA1 hash.<br>
- Even if the files don't change, the created date will.<br>
- A great incidental security feature, because tampering with commit history would be very <br> obvious. It's also helpful for us as devs because we can expect exactly the same data as when it was commited.
</details>

<br>
<details>
    <summary><b>What are references? Why is changing a branch so fast in git?</b></summary> <br>
<b>References are just pointers to commits</b>. Three types of references are... <br>
- Tags<br>
- Branches<br>
- HEAD - a (special type of) pointer; it points to the current commit<br>
The reason changing branches is so fast in Git is, it's not pulling down new data, all it's doing is <i>changing a pointer.</i>
</details>

<br>
<details>
    <summary><b>Where in our git directory do all our branches live? What is a handy tool to get a quick-glance summary of our git history?</b></summary> <br>
refs/heads is where all your branches live.<br>
The handy tool to show a quick view of git history is : <i>git log --oneline</i>
</details>

<br>
<details>
    <summary><b>How many HEADs are there in git?</b></summary> 
    Git only has one HEAD at a given time, if you are wondering what it is you can run `cat .git/HEAD`to find out. HEAD is a pointer to the current branch, in some cases it could also be the current commit.
</details>

<br>
<details>
    <summary><b>Where are the three areas that code live in git?</b></summary> 
     These are the three areas where code lives:<br>
     <ol>
         <li>Working Area (aka Working Tree)
         <li>Staging Area (aka Cache or Index)
        <li>Repository (aka Repo)
    </ol>
</details>

<br>
<details>
    <summary><b>What is the working area?</b></summary> 
     - The files in your working area that are _also not_ in the staging area are not handled by git <br>
- Also called **untracked files**. <br>
- working area is like your scratch space, where you can edit/modify/delete content
</details>

<br>
<details>
    <summary><b>What is the staging area (index, cache)?</b></summary> 
     - What files are going to be part of the next commit<br>
- The staging area is how git knows what will change between the current commit and the next commit. <br>
** The staging area is how git knows what will change between the current commit and the next commit. <br>
- Tip: a "clean" staging area isn't empty! <br>
- Consider the baseline staging are as being an exact copy of the latest commit. <br>
    - It contains a list of files that were in your last commit as well as the SHA1 hash of those files as they were in their last commit<br>
- The staging area (the index) is actually a binary file in the .git directory. <br>
- When you add/remove/rename files to the staging area, Git knows because the SHAs are now different.
</details>

<br>
<details>
    <summary><b>What is the repository?</b></summary> 
   - The files git knows about <br>
- Contains all of your commits<br>
- Contain a snapshot of what your working and staging area look like at the time of the commit<br>
- It's in your `.git` directory
</details>
 
<br>
<details>
    <summary><b>What is git add -p?</b></summary> 
   - One of Nina's favorite tools <br>
    - Allows you to stage commits in hunks<br>
    - interactively! Let's you cherry-pick what to commit.<br>
    - It's especially useful if you've done too much work for one commit<br>
    - a great demonstration on the utility of git's staging area<br>
    - use the `?` to print the key for what the commands are.<br>
    - use `q` to exit out<br>

</details>
  
<br>
<details>
    <summary><b>What happens when you unstage files?</b></summary> 
- Not removing the files <br>
- You're just replacing them with a copy that's currently in the repository. <br>
- We add from Working to Staging area<br>
- We commit from Staging to repo<br>
- `git commit -a` does it in one go (not advised)<br>
- We checkout from Staging to Working<br>
- We checkout branch from Repo to Working<br>
</details>
 
<br>
<details>
    <summary><b>Talk a bit about git stash</b></summary> 
There is one more place that Git stores code, that's through git stash. <br>
- The git stash is a way to save uncommited work <br>
- The stash is **safe** from most, destructive operations (like reset and checkout) <br><br>
- stash changes: git stash <br>
- list changes: git stash list <br>
- show the contents: git stash show stash@{0} <br>
- apply the last stash: git stash apply <br>
- apply a specific stash: git stash apply stash@{0} <br>
- Keep untracked files: git stash --include-untracked <br>
- Name stashes for easy reference: git stash save "WIP: making progress on foo<br>
- You can also you the -p flag on git stash to selectively add files to stash just like we did with commit -p
</details>
 
