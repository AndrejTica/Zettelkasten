---
date: 2025-09-30
tags:
  - "#git"
---
Initializes a git repository and creates a master branch.
Also creates a hidden .git folder with following contents:

- Head: points to the current branch
- config: specific config for the repository 
- objects/: stores file contents (commits, trees, blobs). See [[Git objects]]
- refs/: references to commits (branches, tags)
- index: staging area file
- info/: keeps a global exclude file for ignored patterns that you dont want to track in a .gitignore file. 
- hooks/: Contains client side or server side [[Git hook scripts]]
- description: only used by the GitWeb program 
- 






### References

