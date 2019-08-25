# Self-Assessment & Review of References, Commits, and Branches
---
<details>
    <summary><b>What is the command to find the current value of HEAD?</b></summary> 
    <code>cat .git/HEAD</code>  
</details>

<br>
<details>
    <summary><b>After running cat on .git/HEAD, what's the command to verify this in the context of our other branches?</b></summary> 
    <code>git branch</code><br>
    This will show you a list output of all your existing branches, and then demark with an asterisk * (and maybe highlight color) where your head is. I personally like the: <code>gl</code> command from CMDER which is an alias for <code>git log --oneline --all --graph --decorate</code>
</details>

<br>
<details>
    <summary><b>How do we figure out whta our references are pointing to?</b></summary> 
    <code>git show-ref --heads</code><br>
    You can also use the | + grep + < branchname > to take a look at a specific branch... <br>
    <code> git show-ref --heads | grep exercise3 </code> <br>
    And if we wanted to, we could <code>git cat-file -p </code> to verify this by grabbing the hash of the branch we want and running the command above on that hash which should show us what commit is referenced.
</details>

<br>
<details>
    <summary><b>How do you create a lightweight tag? Then how do you show the tags you have?</b></summary> 
    To create a new lightweight(non-annotated tag, which isn't used particularly often as you'll usually want to annotate your tags)
    <code>git tag < tagname ></code><br>
    To show the tags you have you can use... <br>
    <code> git tag </code>
</details>

<br>
<details>
    <summary><b>How do we find out which commit on which branch our tag is pointing to?</b></summary> 
    <code>git show-refs --tags</code><br>. This can also be verfied in reverse with...
    <code> git tag --points-at < hash id > </code>
</details>

<br>
<details>
    <summary><b>How are lightweight tags different from annotated tags? How do we create an annotated tag? And how do we view that tag we just created?</b></summary> 
    They contain additional metadata: like the author, the date, and an optional message.
    <code> git tag -a < tagname > -m 'this is an annotated tag, cool!' </code><br>
    You can take a look at the newly created tag with...<br>
    <code> git show < tagname > </code>
</details>

<br>
<details>
    <summary><b>How do we figure out the latest commit directly?</b></summary> 
    By looking at the log. We can use something like...
    <code> git --no-pager log --oneline</code> <br>
    We use the <code>--no-pager</code> flag so that it prints in terminal without opening in a new screen. Do note that the no-pager flag should proceed the log command.
</details>

<br>
<details>
    <summary><b>If we've created a dangling commit and don't want to keep it, what do we do?</b></summary> 
    We can just checkout a branch. Git will give us a warning that we are leaving a(or #) commit behind and instructions on if we want to keep it (by creating a new branch) otherwise it will be garbage-collected.
</details>
