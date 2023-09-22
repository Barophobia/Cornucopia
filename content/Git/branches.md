+++
title = "Git Branches"
chapter = true
+++

# Git Branches

### Creating new branches

If you have multiple people who contribute to a project then it may be useful to create a new branch so that the master branch is always working and correct.

To create a new branch you can use this command.

```
git branch X
```

X = name of the new branch 

now a new branch has been made but you are not on the branch yet, to switch to a new branch use:

```
git switch X
```

X = name of the branch to switch to 

You are now on the new branch.

you could also use:

```
git switch -c X
```

X = new branch name 

this will create and switch you to the new branch that you have created.

### Listing branches


To see local branches, run this command:

```
git branch
```

To see remote branches, run this command:

```
git branch -r
```

To see all local and remote branches, run this 
command:

```
git branch -a
```

The current branch will be marked with an asterix.
