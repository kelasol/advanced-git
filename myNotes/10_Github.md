# GitHub

## GitHub Shortcuts
### Navigate Like a Pro
- Press the '?' on any github.com page for a list of shortcuts.
- Then, hit 'Show All'
***Repositories*** 
g c - Go to code
g i - Go to issues
g p - Go to pull requests
g b - Go to projects
g w - Go to Wiki

***Source Code Browsing***
t - activates the file finder
l - jump to line
w - switch branch / tag
y - expand URL to its canonical form
i - Show/hide all inline notes

## Continuous Integration
### Continuous Integration
- Merging smaller commits frequently, instead of waiting until a project is "done" and doing one big merge.
- This means that features can be released quicker!
- CI only works well when there are tests that ensure that new commits didn't "break the build"
- It's even possible to perform a deployment at the end of a CI build!

Commit ---> Test ---> Merge ---> (optional) --> Deploy

### Travis CI - Integrates with Github
- Travis CI is free for open source projects! As well as personal projects that are public.
- It's easy to specify what command you need to run to run tests
- It's also easy to test against multiple versions of a language (python2 vs python3) and even multiple versions of libraries
- tests run automatically on branches and pull requests
- Getting set up is easy
