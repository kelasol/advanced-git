# Forks & Remote Repos
## Github vs. Git
### Distributed Version Control
- We've been talking about the tool, git, but let's talk about what it can do now in the context of distributed repositories. Things used to be held in a central repository

### Github vs Git - The Key is Collaboration
- Git:
    - Open source version control software
- Github: (the following are all Github features, not Git)...  
    - Repository hosting
    - Browse Code
    - Issues
    - Pull Requests
    - Forks

Github real key driver to open source accessibilty.
- Launched in 2008! (Baffling!)
- Github changed the game

## Remotes
### Remotes
- A **remote** is a git repository stored elsewhere - on the web, in github, etc.
- **origin** is the default name git gives to the server you cloned from.

- Cloning a remote repository from a URL will fetch the whole repository, and make a local copy in your .git folder

- You may have different privileges for a remote.
    - Read/Write for some, Read Only for other

### Clone Repository git clone
- We make a copy called a clone on the local machine.
- origin is the default name given  
- all git command , push ,pull all work on _origin_

### Viewing Remotes
`git remote -v`
`> origin git@github.com:lisa/projA.git (fetch)`
`> origin git@github.com:lisa/projA.git (push)`
Will help you view what your remotes are,.

### Cloned Someone Else's Repository
- `git clone git@github.com:dan/projB.git`
- Pull permissions but not push permissions

## Forks, Pull Requests, & Upstreams
### Fork
- A **fork** is a copy of a repository that's stoerd in your Github account
- You can clone your fork to your local computer
- Once cloned to your account, there aren't restrictions
    - push changes
    - edit code
    - can edit your own copy 

### Mergint Changes to ORiginal Project From A Fork
Say you've forked something and made changes, now you want to apply those changes to the origin project, you do so with a **pull request**. A pull request is saying, *knock, knock*, hello mainter of this project. I've made these really cool changes, you should apply them because they improve upon the original.

### Staying up to Date
- While you work on your fork, other changes are getting merged into the source repository.
- In order to stay up to date, set up an **upstream**

### Upsteam 
- The upstream repository is the base repository you created a fork from.
- This isn't set up by default, you need to set it up manually.
- By adding an upstream remote, you can pull down changes that have been added to the original repository after you forked it.
`git remote add upstream https://github.com/ORIG_OWNER/REPO.git`

## Github Workflow
### Triangular Worfklow
- The most common workflow when you are contributing to open source projects.
1. You fetch from upstream to keep your local up to to date
2. You push changes to your fork, aka the origin, and
3. then you propose changes to the upstream repository via _pull request_

![](https://user-images.githubusercontent.com/5563119/63777691-62390900-c898-11e9-836e-471d3c239612.png)

### Tracking Branches
- Track a branch to tie it to an upstream branch.
    - Bonus: Use git push / pull with no arguments

- To checkout a remote branch, with tracking:
    - `git checkout -t origin/feature`
- Tell Git which branch to track the first time you push:
    - `git push -u origin feature`
    - This is going to set up tracking and push that branch back up to remote 

### Tracking Branches Continued
`$ git branch`
`>> *master`
By default, git doesn't really show you any interesting information about what upstream branches are tracking, so a useful command that is useful:

`git branch -vv`
`>> *mastwer bbeb1c32 [ origin/master: behind 124 ] Merge branch 'master' of... `
The `-vv` flag will show you which remote branch you're tracking on your local branch. Very useful information.
- It will also show you how many commits you are ahead or behind.
- In the example above: `origin/master` = which upstream branch is being tracked  
- In the example above: `behind 124` = how many commits you're ahead or behind  

### Fetch
- **Fetching** (`git fetch`): pulls down all the changes that happened on the server
If I want to get information from the the server without merging or pulling, I can use `git fetch`
- Git fetch is important for keeping your local repository up to date with a remote.
- It pulls down all the changes that happened on the server
- But, it doesn't change your local repository

### Pull
- **Pulling** (`git pull`) will pull down the changes from the remote repository to your local repository, and merging them with a local branch.

- Under the hood:
    -`git pull` = `git fetch && git merge`

- If changes happened upstream, git will create a merge commit.
- Otherwise, it will fast-forward.

### Push
- **Pushing** (`git push`): sends your changes to the remote respository
- git only allows you to push if your changes won't cause a conflict

- Tip:
    - To see commits which haven't been pushed upstream yet, use:
        - `git cherry -v`

### Git pull --rebase
:star: Super helpful. It's a `git pull` with a rebase built in...
- `git pull --rebase` will fetch, update your local branch to copy the upstream branch, then replay any commits you made via rebase.

- Bonus: When you open a PR, there will be no unsightly merge commits!

### Git Pull vs Git Pull --rebse

- Warning: Don't use `git pull --rebase` on a branch that has local merge commits, it doesn't work very well. Works best when you are just kind of branching off master or working on a feature. 

![](https://user-images.githubusercontent.com/5563119/63779357-43884180-c89b-11e9-9836-fd06a372b590.png)

### Note: tags
- Git doesn't automatically push local tags to a remote repository.
- To push tags:
    -`git push < tagname >`
    -`git push --tags`

### Contributing to Open Source Projecrts - Pull Requests
- Before opening a PR:
    - Keep commit history clean and neat. Rebase if needed.
    - Run projects tests on your code
    - Pull in Upstream changes (preferably via rebase to avoid merge commits)
    - check for a CONTRIBUTING (.md/.txt) in the project root

- After opening a PR:
    - Explain yuor changes throughly in the pull request
    - Link to any open issues that your pull request might fix
    - Check back for comments from the maintainers

### Advice
- Encourage developers to work on their own forks of a repository
- Mistakes are less likley to happen if no one is pushing directly to the "source of truth" for your codebase!
- You can rebase and force push freely to _your own origin_, as long as no one else is cloning your branch

### Pushing/Merging Your Changes Back to a Remote
- Rule of thumb:
    - Rebase commits on your local feature branch
    - Merge feature branches back to origin (or upstream)

- When accepting a pull request:
    - Squash and merge or rebase with care.
    - You'll lose context about the work on the feature branch!
    - It'll make it harder to debug when issues arise in the future

## Forks and Remote Repos Exercise
Takes 5 minutes to setup.
