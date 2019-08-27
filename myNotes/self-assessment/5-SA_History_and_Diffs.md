# Self-Assessment & Review of History and Diffs
---
<details>
    <summary><b>Why are clear/descriptive commit messages a good idea?</b></summary> 
    &bull; A few extra minutes writing solid Commit messages could save you and others hours in the future.
    &bull; Effect of bad commit messages compounds over the life of the project.
</details>

<br>
<details>
    <summary><b>What are some more reasons to spend time writing solid commit messages?</b></summary> 
    Good commits help perserve the history of a code base.They help with things like:
    <ul>
        <li>debugging & troubleshooting
        <li>creating release notes
        <li>code reviews
        <li>rolling back
        <li>associating the code with an issue or ticket
    </ul>
</details>

<br>
<details>
    <summary><b>What are 4 things that make a good/descriptive commit mesage?</b></summary> 
        <ul>
            <li>Commit message is in future tense. 'Fix' vs 'Fixed'
            <li>Short subject, followed by a blank line.
            <li>A description of the current behavior, a short summary of <b>why</b> the fix is needed. Mention side effects. Commit messages are for adding context for why and how you did something as a opposed to what you did
            <li>In description, keep each line to 72 characters per line
        </ul>
</details>

<br>
<details>
    <summary><b>What are the two primary guiding principles behind solid commits?</b></summary> 
        <ul>
            <li>Encapsulates one logical idea
            <li>Doesn't introduce breaking changes ( i.e. tests pass )
        </ul>
</details>

<br>
<details>
    <summary><b>What does git log do?</b></summary> 
    <code> git log </code>
    The baic command that shows you the history of your repository
</details>
 
<br>
<details>
    <summary><b>Speak a bit to what the git log --since flag does</b></summary> 
    Find out what changed since yesterday, 2 weeks...<br>
        <code>git log --since="yesterday"</code><br>
        <code>git log --since="2 weeks ago"</code><br>
        Another way to write the above: <br>
        <code>git log --since=2.weeks</code><br>
</details>

<br>
<details>
    <summary><b>Speak a bit to what the git log --follow flag does</b></summary> 
    Log files that have been moved or renamed <br>
    <code>git log --name-status --follow -- < file ></code>
</details>

<br>
<details>
    <summary><b>Speak a bit to what the git log --grep flag does</b></summary> 
    Search for commit messages that match a regular expression: <br>
    <code>git log -grep < regexp ></code> <br>
    Can be mixed & matched with other git flags. <br>
    <b>Example:</b> <br>
    <code>git log --grep=mail -- author=nina --since=2.weeks</code>
</details>

<br>
<details>
    <summary><b>Speak a bit to what the git log --diff-filter flag does</b></summary> 
    Selectively include or exclude files that have been: <br>
    (A)dded, (D)eleted, (M)odified & More...<br>
    <b>Example:</b> <br>
    <code>git log --diff-filter=R</code>
</details>


 
### git log: referencing commits
- `^` or `^n`
    - no args:  `==^1`: the first parent commit
    - n: the nth parent commit

- `~` or `~n`
    - no args: `==~1`: the first commit back, following 1st parent
    - n: number of commits back, following only 1st parent 

note: ^ and ~ can be combined

### Referencing Commits
- Parent commits are ordered left to right
- Nina uses ~ more than ^, but they are both very useful. 
- This chart is worth studying, wanting to move 3-commits back you can use this reference methodology versus finding the commit # and then going back by that, you could just say like 
![](https://user-images.githubusercontent.com/5563119/63693243-65fd5a80-c7c8-11e9-8334-36e668760435.png)
- If you don't provide a number argument, it passes in 1 by default

## Git Show and Diffs
### Git Show: Look at a Commit
A really quick way to take a peet at another commit from the command line. It's a reference, and a super neat way to look at the contents of any commit. It can also show the contents of any commit that has been orphaned, a commit after a rebase or files in a detached head-state, so long as it's in our history we can take a look at it with <code>git show < commit >`.</code>

-show commit and contents
    - <code>git show < commit ></code>
- show files changed in commit:
    -<code>git  show < commit >  --stat</code>
- look at a file from another commit:
    - <code>git show < commit >: < file ></code>

### Diff 
Diff is a common tool we use as developers
- Diff shows you changes:
    - between commits
    - between the staging area and the respository
    - what's in the working area

- unstaged changes (what could be in the next commit)
    - <code>git diff</code>
- staged changes (what will be in the next commit)
    - <code>git diff --staged</code>

You can also pass in file arguments to narrow down which file you wanna look at the diff of.

### Diff Commits and Branches
![](https://user-images.githubusercontent.com/5563119/63693862-fc7e4b80-c7c9-11e9-841f-ab6f66f88da7.png)
- Note that the default syntax of diff is the same as the two dot notation, `..`, so...  
- <code>git diff A B` === <code>git diff A..B</code>
- The diff between these branches will show you difference between the branches, so only the blue changes. 

### "Diff" Branches
It's also possible to so call, "diff" branches...
- Which branches are merged with mastewr, and can be cleaned up?
    - <code>git branch --merged master</code>

We can also find out ...  
- Which branches aren't merged with master yet?a
    - <code>git branch --no-merged master</code>

## History and Diffs Solution
 - the `-f` flag will force something
 - if we run something like <code>git log --name-status --follow --oneline hello.template` we can see the</code>tracked changes and name changes of a file. Notice the very first intial commit has the letter A next to it. A in this context is when the file was added. (Taking a closer look, it looks like commit with the renamed file starts with R and the rest of the files that just modifying start with M). 

> git log --since="yesterday"  
> git log --name-status --follow --oneline hello.template  
> git log --grep="i18n" --author=kelasol --since=2.weeks  
> git log --diff-filter=R --find-renames  
> git log --diff-filter=M --oneline
> git show 09ca68
> git branch --merged master
> git branch --no-merged mastwer
