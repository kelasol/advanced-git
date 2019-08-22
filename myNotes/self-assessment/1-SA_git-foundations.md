## Self-Assessment & Review of Git Foundations
---
<details>
    <summary> <b>How does Git Store Information? </b> </summary>
    In what are essentially key-value pairs: <br>
    <ul> 
        <li> The Value = data  
        <li> The Key = Hash of the Data
    </ul>
    <br>
     Git stores things as <i>Git Objects</i>: blobs, trees, and commits are all instances of git objects.
</details>

<details>
    <summary> <b>What is a blob? What does it hold?</b> </summary>
    A blob is a type of <i>Git Object</i>. It contains at least 3 other pieces of metadata in addition to the contents of the data itself. <br>
    <ol> 
        <li> the indentifier blob
        <li> the size of the content
        <li> the \0 delimiter (string terminator in C)
        <li> the compressed data or content
    </ol>
</details>

<details>
    <summary> <b>Why can a system like Git be referred to as a <i>content addressable</i> system?</b> </summary>
    This value should always be the same if the given input is the same.
Sometimes system like this is called a content addressable system and that's because you can also use the content to generate the key.
</details>

<details>
    <summary> <b> What is one of the most critical design features of Git?</b></summary>
    One of the most critcal features of Git, how Git saves as ton of space. So if we commit a blob or the tree, if it hasn't changed, we're just gonna point to the same copy. Which is why checking out branches in git is super fast.
</details>

<details>
    <summary> <b> What is the difference between the blob and the SHA that refers to it?</b></summary>
    The difference between the blob and the SHA. Is that the blob is the content and the SHA is essentially the key for that piece of content. However, the key is stored within that blob that tells it what content to associate itself with.
</details>

<details>
    <summary> <b> When are Packfiles generated?</b></summary>
     You have too many objects, during garbage collection, or during a push to a remote.
</details>

 