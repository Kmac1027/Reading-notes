# Revisions and the Cloud

## what is Git?

Git is a way for developers to all be able to work on the same 
project at the same time while still being able to look back and 
see all previous work that has been done
***
Git is a DVCS or Distributed Version Control, this means that all 
information can be copied or mirrored to a backup sever as a way to
protect the work being done from bugs or crashes.

coding is done in a text editor locally, i use VSCode, and then is pushed to github via the terminal

## GitHub repository cloning

cloning a reposotory from github to a local computer

```
git clone (pathway of repository)
```

### Git clone pathway - A.C.P.

- Add
- command
- push

```
1. Git add (name of file)
1. Git commit -m “add description”
1. Git push origin master
```

*Git add . (Adds everything)*

## tracking and staging

Single File

Track one file only by using the following format:

```
git add filename
```

Track all files in a repository by using the following command:

```
git add *
```

*After using these commands, files are tracked and staged for committing*

### pushing changes

```
git push origin master
```

### seeing your remotes
```
By running the git remote command, 
you can view the short names, such as “origin,” 
of all specified remote handles.

By using git remote -v, 
you can view all the remote URLs 
next to their corresponding short names.
```

[Back Home](README.md)