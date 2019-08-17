## Self-Assessment & Review of Git Foundations
---

<details>
    <summary> <b>How does Git Store Information? </b> </summary>
    In what are essentially key-value pairs: <br>
    <ul> 
        <li> The Value = data  
        <li> The Key = Hash of the Data
    </ul>
</details>

<details>
    <summary> <b> What is one of the most critical design features of Git?</b></summary>
    One of the most critcal features of Git, how Git saves as ton of space. So if we commit a blob or the tree, if it hasn't changed, we're just gonna point to the same copy. Which is why checking out branches in git is super fast.
</details>

<details>
    <summary> <b> What is the difference between the blob and the SHA that refers to it?</b></summary>
    The difference between the blob and the SHA. Is that the blob is the content and the SHA is essentially the key for that piece of content. However, the key is stored within that blob that tells it what content to associate itself with.
</details>
