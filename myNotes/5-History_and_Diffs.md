# History and Diffs

## Useful Commit Messages
### Bad Commit Messages
- A few extra minutes writing solid Commit messages could save you and others hours in the future.
- Effect of bad commit messages compounds over the life of the project

### Good Commits are Important
- Good commits help perserve the history of a code base
- They help with:
    - debugging & troubleshooting
    - creating release notes
    - code reviews
    - rolling back
    - associating the code with an issue or ticket

### Anatomy of a Good Commit Message 
- Complex fixes/features shouldn't be relegated to a single line `commit -m`, what you should do is add a description. Add descriptive message to your commit after a newline. Message truncates after 69 characters, 

- Commit message is in future tense. 'Fix' vs 'Fixed'
- Short subject, followed by a blank line.
- A description of the current behavior, a short summary of **why** the fix is needed. Mention side effects. Commit messages are for adding context for why and how you did something as a opposed to what you did (which will be evident, or not, by the code). Describe the current behavior, a short summary of why 
![](https://user-images.githubusercontent.com/5563119/63657009-88539180-c750-11e9-993a-7545a4a6e17a.png)
- Keep each line to 72 characters per line

### Anatomy of a Good Commit
- Good commit message
- Encapsulates one logical idea
- Doesn't introduce breaking changes
    - i.e. tests passKv

## Git Log
### Git Log
- `git log` - the baic command that shows you the history of your repository
- not super useful by itself, but it has some super helpful and cool flags...

### git log --since
- The site is slow. What changed since yesterday?
    - `git log --since="yesterday"`
    - `git log --since="2 weeks ago"`

### git log --follow
- Log files that have been moved or renamed
    - `git log --name-status --follow -- < file >`

### git log --grep
- Search for commit messages that match a regular expression:
    - `git log -grep < regexp >`
    - Can be mixed & matched with other git flags.
- Example
    - `git log --grep=mail -- author=nina --since=2.weeks`

### git log diff-filter
- Selectively include or exclude files that have been:
- (A)dded, (D)eleted, (M)odified & More...

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
A really quick way to take a peet at another commit from the command line. It's a reference, and a super neat way to look at the contents of any commit. It can also show the contents of any commit that has been orphaned, a commit after a rebase or files in a detached head-state, so long as it's in our history we can take a look at it with `git show < commit >`. 

-show commit and contents
    - `git show < commit >`
- show files changed in commit:
    -`git  show < commit >  --stat`
- look at a file from another commit:
    - `git show < commit >: < file >`

### Diff 
Diff is a common tool we use as developers
- Diff shows you changes:
    - between commits
    - between the staging area and the respository
    - what's in the working area

- unstaged changes (what could be in the next commit)
    - `git diff`
- staged changes (what will be in the next commit)
    - `git diff --staged`

You can also pass in file arguments to narrow down which file you wanna look at the diff of.

### Diff Commits and Branches
![](https://user-images.githubusercontent.com/5563119/63693862-fc7e4b80-c7c9-11e9-841f-ab6f66f88da7.png)
- Note that the default syntax of diff is the same as the two dot notation, `..`, so...  
- `git diff A B` === `git diff A..B`
- The diff between these branches will show you difference between the branches, so only the blue changes. 

### "Diff" Branches
It's also possible to so call, "diff" branches...
- Which branches are merged with mastewr, and can be cleaned up?
    - `git branch --merged master`

We can also find out ...  
- Which branches aren't merged with master yet?a
    - `git branch --no-merged master`

## History and Diffs Solution
 - the `-f` flag will force something
 - if we run something like `git log --name-status --follow --oneline hello.template` we can see the tracked changes and name changes of a file. Notice the very first intial commit has the letter A next to it. A in this context is when the file was added. (Taking a closer look, it looks like commit with the renamed file starts with R and the rest of the files that just modifying start with M). 

> git log --since="yesterday"  
> git log --name-status --follow --oneline hello.template  
> git log --grep="i18n" --author=kelasol --since=2.weeks  
> git log --diff-filter=R --find-renames  
> git log --diff-filter=M --oneline
> git show 09ca68
> git branch --merged master
> git branch --no-merged mastwer
