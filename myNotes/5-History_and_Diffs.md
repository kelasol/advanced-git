# History and Diffs

## Useful Commit Messages
### Bad Commit Messages
- A few extra minutes writing solid Commit messages could save you and others hours in the future.
- Effect of bad commit messages compounds over the life of the project

### Good Commits are Important
- Good commits help perserve the history of a code base
- They help with:
    - debuggin & troubleshooting
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
    - n: number of commits back, following only 1st parent]

note: ^ and ~ can be combined


## Git Show and Diffs

## History and Diffs Exercise

## History and Diffs Solution