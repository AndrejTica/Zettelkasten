---
date: 2025-10-01
tags:
  - "#git"
---
``git log --graph --decorate --oneline --all ``
shows a compact, colored commit history graph of all branches, with branch/tag names, one commit per line.

--graph draws ASCII branch/merge lines (*, |, \, /) in the left margin.

--decorate shows refs (branch names, tags) next to the commit ((HEAD -> main, origin/main, v1.4.0)).

--oneline prints each commit as short-hash subject (one line).

--all includes commits from every ref (all local branches, remote-tracking branches, etc.).


![[Pasted image 20251001181906.png]]


Handy add-ons:

Limit output: … --max-count=30 or … main (only that branch).

Since date: … --since="2025-09-01".

Show remotes too: … --all --remotes.


### References

