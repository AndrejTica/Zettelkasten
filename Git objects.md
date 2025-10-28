---
date: 2025-09-30
tags:
  - "#git"
---
Git is a content-addressable filesystem. What does that mean? It means that git at its core is a key-value database. This means we can insert any kind of content into the git database and it will return as a unique key with with later we can reference this content. 

With the ``git hash-object`` command, we can give it some data, it will store this data into the .git/objects directory and return a unique key that refers to this object now. 

```
echo 'test content' | git hash-object -w --stdin
```
return:
```
d670460b4b4aece5915caf5c68d12f560a9fe3e4
```

the -w flag says to not only give a key but also store the content. --stdin reads from stdin as input.

The output is a 40 character checksum hash using [[SHA-1]] hash and also contains a part which is the header (d6)

Now we have a directory and file in the objects directory:

```
.git/objects/d6/70460b4b4aece5915caf5c68d12f560a9fe3e4
```

We can examine the content of this file with the 
```
git cat-file
```
With the -p flag we can tell the command to figure out type of content and display it appropriately. 
```
$ git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
 test content
```

If we would create a new file and add it to the database, and then write some content into that file and again use git hash-object -w command, we would get two entries in our objects database. Now we can delete the file, and use git to restore a version of this file. 

```
$ git cat-file -p 83baae61804e65cc73a7201a7252750c76066a30 > test.txt $ cat test.txt version 1
```

However its not practical to remember the hash for each time we want to restore the file, plus the file name itself is not stored. This type of objects is called "blob" in git.

### Tree objects 
This type of git objects solve the problem of storing file names and also allows to store a group of files. 
A tree object is gits way of representing a directory.  If we have a structure like this:
```
project/
 ├── main.c
 └── lib/
      └── util.c
```

Then git will create: 
1. One blob for main.c.
2. One blob for util.c.
3. A tree for lib/ that points to the blob of util.c.
4. A tree for the root project/ that points to the blob of main.c and the tree for lib/.
A commit object then points to the root of the tree

### References


