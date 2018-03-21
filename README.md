# git-tips
A collection of my most used git commands

```
# Before pushing changes, it's good to know what changes you've made.
git log     # Use this to find the last commit made before you (e.g. fa275b54574d768d3628948658d00feae11a1df5)
git diff --name-only fa275b54574d768d3628948658d00feae11a1df5..           # Shows files that have changed
git diff fa275b54574d768d3628948658d00feae11a1df5.. MyApp/MyClass.swift   # Show what has changed in a specific file 


# Overwrite master with latest version of beta branch
git checkout master
git merge -X theirs beta

# Compare two branches
git diff --name-status master..beta

# Keep their version of a conflicted file
git checkout --ours index.html          

# Keep my version of a conflicted file
git checkout --theirs index.html                

# View conflicted files
git diff --name-only --diff-filter=U                
                     
# When in a branch, merge with local master
git rebase master  
           
# When in a branch, merge with remote master (use with caution, don't remember why)
git pull --rebase origin master

# Retrieve a list of the most recently active branches.
git for-each-ref --sort=-committerdate refs/heads/

# Compare a file between two branches.
git diff beta master -- myfile.html

# Find the common commit between two branches.
git merge-base master mybranch

# Revert all view controllers modified by mybranch (ignoring those modified by master) to their state before mybranch separated from master.
git diff --name-only master...mybranch *ViewController.swift | xargs git checkout 76d1e5ba4153c263134ac221eb37ebaa5552358f

# List all the json files that have been modified by mybranch since it parted ways from master.
git diff --name-only master...mybranch -- '*.json'

# List all the files changed between the last and current commit (HEAD is current commit, HEAD~ is its parent commit).
git diff --name-only HEAD~

# *Untested* Revert all the json files that have been modified by mybranch since it parted ways from master.
git diff --name-only master...mybranch -- '*.json' | xargs git checkout `git merge-base master mybranch`

# Diff between current branch commit (HEAD) and a certain commit, excluding certain directories.
git diff --name-only 401f58f6675bfc8b25f4cd04e352f7208abc7cebb -- . ':!imgs/logos' ':!assets/user'

# Retrieve a remote branch.
git checkout -t origin/some-branch

# List commits showing visually the amount of changs in each commit
git log --stat

# In the middle of a merge with conflicts, if you want to re-try to manually resolve a particular file
git checkout -m path/to/a_file


```
