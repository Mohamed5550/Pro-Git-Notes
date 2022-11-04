# Chapter 2: Gt Basics

- ## Getting a Git repository
  
  - Two ways to get a git repo:
    - Initializing a new one: *git init*
    - Cloning an existing one: *git clone $repo $local_folder_name*

- ## Recording changes to the repo
  
  - Two types of files:
    - Tracked: files Git know about
    - Untracked: files added or modified but not stagged yet

  - *git status*: to see the state of each file
  - *git add*: to stage a file
  - *git status -s or git status --short*: short status
    - ??: Untracked
    - M: Modified
    - A: Added
    - There are two columns, the left for stagging area, and the right for work tree
  - ignoring files
    - empty lines and lines starting with # are ignored
    - use glob patterns to write the ruels
    - append / to stop recursivity
    - prepent / to specify a folder
    - you can negate with !
    - glob is a simplifed regex for shell
    - you can use multiple .gitignore files in different folders

  - Viewing staged and unstaged changes
    - *git diff*: shows the files to be stagedcompares them
    - *git diff [--staged or --cached]*: shows the staged files but not committed and compares them
    - *git difftool to see the differences in a graphical tool that is installed in the system*
  
  - Committing changes
    - *git commit*: commit all staged files
    - -v adds the diff to the commit message
    - -m to write the commit message inline
    - *git commit -a -m 'messae'* skipps stagging area

  - Removing files
    - *git rm file*: removes is from the staging area and from working tree
    - *git rm file --cached*: removes it from the stagging area only
    - You can use glob in the file name
  - Moving files
    - git mv

  - Viewing the commit history
    - *git log*: to see this history of all commits
    - -p or --patch: shows the diff in the commits
    - -[number]: shows the last [number] commits
    - --stat: to show states of the commits
    - --pretty or with[=short, =full, =fuller]: small formated log, you can use custom format also.
    - -- graph shows an ascii graph describing the commit

  - Limiting Log Output:
    - --since
    - --author
    - --grep: for searching in the commit message
    - -S: the commits that changed the numbef of occurences of a word
    - *git log -- [path]*: prints the commits that changed the files in [path]
    - --no-merges

- Undoing Things:
  - *git commit --amend*: redo last commit with new changes

  - Unstaging a staged file:
    - *git reset HEAD*: removes he file from stagging area
  
  - Unmodifying a modified file
    - *git checkout -- file*: discards the changes in the working tree
    - It's a dangerous command
  
  - git restore

    - *git restore --staged [file]*: unstages a file
    - *git restore*: resets the working tree  // dangerous

  - Working with remotes
    - Remotes are versions of your project hosted in the internet somewher
    - *git remote*: shows the remote for your repo
    - *git remote -v*: shows the link of the remote with the name
    - *git remote add {name} {url}*: to add a new remote
    - *git fetch {remoteName}*: gets the data that the remote have but you don't have yet
    - *git pull {remoteName}*: fetch + merge
    - *git push {remote} {branch}*: pushes the changes to the remote
    - before you can push you should pull the last changes
    - *git remote rename {oldName} {newName}*: rename
    - *git remote remove (or rm) {remoteName}*: remove
  
  - Tagging
    - *git tag*: lists all the tag
    - *git tag -l "v1.5.\*"*: lists tags with a pattern
    - *git show {tagName}*: to show tag
    - types:
      - annotated tags: "git tag -a {tagName} -m '' "
      - ligtweight tags: "git tag {tagName}"
    - *git tag -a {tagName} {commitHash}*: to tag a past commit
    - git push doesn't share the tags
    - *git push origin {tagName}*: to push a tag
    - or *git push --tags*
    - --follow-tags: will push only annonated tags
    - *git tag -d {tagName}*: delete a tag
    - *git push origin :refs/tags/{tagName}*: delete a tag
    - *git push origin --delete {tagName}*: delete a tag (simpler)
  
  - Git Aliasing
    - *git config --global alias.{short} {long}*
    - *git config --global alias.{short} '!{long}'*: for running externals commands (note the !)
