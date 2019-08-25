## Self-Assessment & Review of Git Areas and Stashing
---
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
 
