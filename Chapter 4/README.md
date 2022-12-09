# Chapter 4: Git on the server

git repositoriy is the collaboration point for all collaborators

## The protocols

- ### Local
  
  - the remote repository is on a desk accessed by all collaborators, they are all in the same filesystem
  - git clone /path/to/repo.git => *better*
  - or git clone file:///path/to/repo.git
  - git remote add local_repo /path/to/repo.git

- ### HTTP

  - git clone https://github/username/repo.git
  - Smart HTTP
  - Dump HTTP

- ### SSH
  
  - git clone ssh:://[user@]server/repo.git
  - or git clone [user@]server:repo.git
  - user@ is optional
  - it is secure and fast
  - it doesn't support read-only without access

- ### Git
  
  - it listens to port: 9418
  - you must create git-deamon-export-ok file
  - it dosnt' have authentication
  - it is the fastest for read-only
  - you will need ssh or https for pushers

## Getting Git on a Server

- git clone --bare my_project my_project.git
- putting the bare repo on a server
  - scp -r my_project.git user@git.example.com:/srv/git
  - git clone user@git.example.com:/srv/git/my_project.git
  - git init --bare --shared: to add group permissions properly
- Small Setups
- SSH Access
