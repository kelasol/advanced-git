# Self-Assessment & Review of Merging and Rebasing
---
<details>
    <summary><b>Merge commits are just...</b></summary> 
    ...commits, they just happen to have more than one parent. <br>
    &bull; In most modern Git workflows, most merge commits probably have two parents (possible to have 3,4+) <br>
    &bull; The Merge commit is just a marker of when a new feature merged into master 
</details>

<br>
<details>
    <summary><b>When do fast-forwards happen?</b></summary> 
    Fast-forward happens when there are no commits on the base branch that occured after the feature branch was created.
</details>

<br>
<details>
    <summary><b>What's happening under the hood when we ff?</b></summary> 
    During a fast-forward commit, we add the new commits on top of the master branch and then we just move the master pointer. In this case we didn't have a merge commit, git knew how to just move the pointer to the end of the feature branch. <br>
</details>

<br>
<details>
    <summary><b>What is the problem with ff?</b></summary> 
    The problem is that during these FF commits: we can possibly lose track of a feature that was merged back into master, because when you are working on a feature and you merge it back into master, you really want to have a clear delineator of work that was done in that specific branch. We won't be able to identify which bugs emerged from which feature if there's no merge commit. In order to avoid this...
</details>

<br>
<details>
    <summary><b>How do we work around the drawback of fast-forwards?</b></summary> 
    By using <code>git merge --no-ff</code> (No Fast Forward) <br>
    &bull; This way we retain the history of a merge commit, even if there are no change to the base branch <br>
    &bull; This will _force_ a merge commit, even when one isn't necessary.
</details>

<br>
<details>
    <summary><b>What is a merge conflict? What does git do with a merge conflict?</b></summary> 
    This happens when we try to merge but our files have diverged and changes are not comapatible. <br>
    &bull; Attempt to merge, but files have diverged.
    &bull; Git stops until the conflicts are resolved.
</details>

<br>
<details>
    <summary><b>What is git rerere and what is it useful for?</b></summary> 
    Stands for REuse REcorded REsolution. A way for git to save how you resolved a conflict and reapply the resolution when the same conflict arises. <br>  
    &bull; It's useful in long lived feature branches (like a refactor) as well as when rebasing.
</details>

<br>
<details>
    <summary><b>How do you use git rerere?</b></summary> 
    You first need to turn it on with <code>git config rerere.enabled true</code>. To use it globally in all projects use the <code>--global</code> flag to enable for projects, although not advised to use globally. <br>
    &bull; Once enabled, you can just resolve a conflict that you'd want cached, and git handles the rest. 
</details>

<br>
<details>
    <summary><b>What happens when you use git rerere?</b></summary> 
&bull; When you commit the conflict resolution, it's recorded, and says so in terminal: <code> Recorded resolution for < feature name ></code> <br>
&bull; The next time we have the same conflict, git will automatically apply the last resolution, but it won't be automatically staged so you can review it.
&bull; The next time we have the same conflict, git will automatically apply the last resolution, but it won't be automatically staged so you can review it.
</details>