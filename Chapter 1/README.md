# Chapter 1: Getting Started

## About Version Control

- VCS stands for version control systems
- It means to track all the states of a file
- You can know when a particular part was modified, reset a file to a previous state, or reset the whole project to a previous state

## Local Version Control Systems

- There is an old approach of VCS which works by keeping the differences between files in a local database. This alows us to know how the file looked in any point of time, this system is called RCS.

## Centrailized Version Control Systems

- This means to save all the tracked files in a central database for all developers, for many years, this has been the standard for version control.

- This has a downside as, if the server goes down for an hour, nobody will be able to save any work.

- Examples: CVS, Subversion, Preforce

## Distributed Version Control Systems

- It has a full history of the repo, not only the last snapshot

- If the server dies, you can copy any clone to resore it. Every clone is really a full backup of all the data

- Examples: Git, Mercurial, Bazaar, Darcs

## A short hitory of Git

- It was developed by the community who developed Linux after their problem with BitKeeper

- They focused on:
  - Speed
  - Simple Design
  - support for non-linear development
  - fully distributes
  - Able to handle large projects

- Git was released in 2005

## What is Git?

- ### Snapshot not differences
  
  - Other CVS systems like Subversion and Preforce use delta-based version control: which means to store the files and the changes made to them over the time
  - Git takes a picture to the last changed file and saves a reference to that picture

- ### Nearly every operation is local
  
  - You can still work with nearly full features while you are offline

- ### Git Has Integrity

  - Git tracks everything ans uses SHA-1 hashing for this

- ### Git generally only adds data

  - You can undo enything

- ### The three states

  - The working directory: the current snapshot of the repo
  - The stagging area: the index file to show what is marked to be committed in the next commit
  - The .git directory: is the most important part of git

## The command line

- The only place to run all git commands is the command line, the GUIs implements only a selected area

## Installing Git

- For windows
- For MacOs
- For Linux
- Git the source code

## Firs-Time Get Setup

- git config --global user.name "John Doe"
- git config --global user.email johndoe@example.com
- If you want to save it globally, pass the --globla option, if you want to run it to the current project only, don't pass it
- git config --global core.editor emacs: this make the defualt editor emacs
- git config --global init.defaultBranch main: for default branch name
- git config --list: to check your config
- you can pass --show-origin to show tha path of the config file for that value

## Getting Help

- git help $verb
- git $verb -- help
- man git-$verb
- git $ver -h: for more concise help
