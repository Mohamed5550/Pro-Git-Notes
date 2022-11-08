# Chapter 3: Gt Branches

- ## Branching in a Nutshell

  - Each branch points to a commit (by default the last one), each commit points to its previous commit, and contains pointers to last snapshot of each file
  
  - Creating a branch
    - *git branch {name}*: creates a new branch
    - There is a specials pointer HEAD points to the current branch
    - *git log*: to see current branch
  
  - Switching branch
    - *git checkout {name}*: switches to an existing branch
    - It moves HEAD to the selected branch
    - It changes the directory to the commit which that branch points to
    - *git checkout -b {name}*: creates the branch and switches to it
    - *git switch*: is alias for git checkout
    - *git switch -c*: is alias for git checkout -b
    - *git switch -*: return to your previous checked out branch

- ## Basic branching and merging

  - *git merge {name}*: merges the {name} branch into the current branch
  - fast-forward: means that the other branch differs from the current branch in some additional commits, so Git just moves the pointer forward
  - *git branch -d {name}*: for deleting a branch

- ## Basic merging

  - When the merged branch last commit is not a child of the current branch, the fast-forward doesn't apply, so Git creates a new merge branch that has more than one parent
  - This is called three-way merge

- ## Basic merge conflicts

  - conflicts happens when you edit the same part of the file in two branches then you tries to merge them
  - fix the conflicts manually
  - run git add . then git commit

- ## Branch management
  
  - *git branch*: lists all branches
  - *git branch -v*: lists with the last commit
  - *--merged*, *--no-merged*: filters the list according to the state of merging the branches with the current branch
  - *git branch -D*: force delete when the branch is not merged
  - you can specify a branch in the list to use it instead the currnt one

  - Changing a branch name
    - Don't rename a branch that is still in use by other collaborator
    - *git branch --move old-name new-name*: renames a branch locally
    - *git push --set-upstream origin new-name*: to let others see the corrected branch
    - *git push origin --delete old-name*: to delete the branch on the remote

- ## Branching workflow

  - common workflows to follow when working with brances
  - Long Running Branches: like develop branch
  - Topic Branches: short branches for features ans issues

- ## Remote Branches

  - remote-tracking branches
    - *git clone -o {hello}*: clones and makes the main remote "hello"
    - *git fetch {remote}*: to syncronize the remote branch with the local branch
  
  - Pushing:
    - *git push {remote} {branch}*
    - *git push {remote} {localBranch}:{remoteBranch}*
    - *git config --global credential.helper cache*: to cache the login data for some minutes in memory
    - *git merge {remote}/{remoteBranch}*: to merge the fetched branch into a local branch
    - *git checkout -b {localBranch} {remote}/{remoteBranch}*: same as above

  - Pulling:
    - *git pull* = *git fetch* + *git merge*
    - It's better to use them explicitly
  
- ## Tracking Branches

  - Tracking branch: the local branch that tracks a remote branch
  - Upstrea branch: the remote branch that is being tracked
  - *git pull* inside a branch: the server knows automatically where server to go and where branch to pull
  - *git checkout --track {remote}/{branch}*: creates a branch and makes it track the remote branch
  - *git checkout {branch}*: creates a tracking branch if
    - the name deosn't exist
    - it matches a branch in only one remote
  - *git branch -u {remote}/{branchc}*: to change the upstream branch of the current branch
  - *@{u}* or *@{upstream}*: reference to the upstream branch like "origin/master" ex: *git merge @{u}*
  - *git branch -vv*: to show tracking branches
  - *git fetch --all*: fetches from all remotes

- ## Rebasing
  
  - Exactly like merging but with a linear history
  - it rebases the current branch into the target branch to add all the updates to it in its history
  - then you can switch to that branch and merge
  - *git rebase test main*
  - *git switch main*
  - *git merge test*
  - *git branch {baseBranch} {topicBranch}*
  - *git branch --onto {baseBranch} {subBaseBranch} {topicBranch}*: this rebases {topicBranch} into the {baseBranch} since it diverged from {subBaseBranch}
  - don't repase when you have work ouside your repo that people may base work on
  - *git pull --rebase*: to fix such a situation
  - advise: use rebase to clean your work before pushing, but don't use it on something you pushed
