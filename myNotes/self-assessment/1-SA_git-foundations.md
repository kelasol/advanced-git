## Self-Assessment & Review of Git Foundations
---
<h4 style="color:blue;"> Question 1</h4>
<details>
    <summary><b>How does Git Store Information? </b> </summary>
    In what are essentially key-value pairs: <br>
    <ul> 
        <li> The Value = data  
        <li> The Key = Hash of the Data
    </ul>
    <br>
     Git stores things as <i>Git Objects</i>: blobs, trees, and commits are all instances of git objects.
</details>

<h4 style="color:blue;"> Question 2</h4> 
<details>
    <summary><b>Why can a system like Git be referred to as a <i>content addressable</i> system?</b> </summary>
    This value should always be the same if the given input is the same.
Sometimes system like this is called a content addressable system and that's because you can also use the content to generate the key.
</details>

<h4 style="color:blue;"> Question 3</h4>
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

<h4 style="color:blue;"> Question 4</h4>
<details>
    <summary><b>Where Does Git Store its Data?</b> </summary>
    In the .git directory when we init. 
    This in turn contains all of the data about our repository
</details>

<h4 style="color:blue;"> Question 5</h4>
<details>
    <summary><b>Where, more specifically, are blobs stored?</b> </summary>
    If you tree, your .git directory you will see a dir called objects that will contain the first two values of the hash, the file is the rest of the hash.
</details>

<h4 style="color:blue;"> Question 6</h4>
<details>
    <summary><b>What information from blobs is missing that requires git to have something else? Where is this information managed?</b></summary>
        <span>&#8226;</span> Filenames <br>
        <span>&#8226;</span> Directory structures
        This additional information is held by trees
</details>

<h4 style="color:blue;"> Question 7</h4>
<details>
    <summary><b>What does a tree hold? Used for?</b></summary>
    A tree contains <i>pointers</i>. To blobs and also to other trees.
    It holds pointers to other trees because subdirectories can be nested.
</details>

<h4 style="color:blue;"> Question 8</h4>
<details>
    <summary><b>What else do trees contain?</b></summary>
    A tree also contains metadata:
    <span>&#8226;</span> type of pointer (blob or tree)<br>
    <span>&#8226;</span> File name or directory name<br>   
    <span>&#8226;</span> mode (executable file, symbolic link,...<br>
</details>

<h4 style="color:blue;"> Question 9 </h4>
<details>
    <summary><b>What is one of the most critical design features of Git?</b></summary>
    One of the most critcal features of Git, how Git saves as ton of space. So if we commit a blob or the tree, if it hasn't changed, we're just gonna point to the same copy. Which is why checking out branches in git is super fast.
</details>

<h4 style="color:blue;"> Question 10 </h4>
<details>
    <summary><b>What is the difference between the blob and the SHA that refers to it?</b></summary>
    The difference between the blob and the SHA. Is that the blob is the content and the SHA is essentially the key for that piece of content. However, the key is stored within that blob that tells it what content to associate itself with.
</details>

<h4 style="color:blue;"> Question 11 </h4>
<details>
    <summary><b>How would you say the design of Git compliments the iterative development process of code writing? What is a Packfile?</b></summary>
     As files change, their contents remain mostly similar as you tend to add to them and modify them (more than not) in gradual increments. This allows git to optimize files by compressing them together into what is referred to as a Packfile.
</details>

<h4 style="color:blue;"> Question 12 </h4>
<details>
    <summary><b>If the Packfile is the thing that stores the object, what are deltas for?</b></summary>
    Deltas are just what we call the differences between one version of the file and the next. Delta = difference between old and new versions; the diff of what has changed.
</details>

<h4 style="color:blue;"> Question 13 </h4>
<details>
    <summary><b>When are Packfiles generated?</b></summary>
     When you have too many objects, during garbage collection, or during a push to a remote.
</details>

<h4 style="color:blue;"> Question 14 </h4>
<details>
    <summary><b>What does a commit point to and what does it contain?</b></summary>
    A commit points to a tree and it contains metadata like: author, committer, date, message, parent commit (one or more)
    The SHA1 of the commit is the hash of all this information.
</details>