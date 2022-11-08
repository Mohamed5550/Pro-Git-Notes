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
