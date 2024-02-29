+++
title = "Introduction to git"
chapter = true
+++

# Git 

### What is Git?

Git is a version management tool used to make collaborative efforts a lot easier.

### Creating a new repository:

To create a new repository using git you should cd to the folder you want to be a repository and type into your terminal:

```
git init
```

This will create a .git directory known as the working tree. 

### Checking the status of your repository

Using the 'git status' command will show you what branch you are using, changed files not staged for commit and files that are not currently tracked by git.

```
git status
```

### Adding files to your repository to be tracked

To add files to be tracked you will need to use 'git add' an example of this would be:

```
git add .
```

Using the command above will add all files inside the folder to be tracked. 

### Commiting changes to the repository

```
git commit
```

This command will commit the changes that have been added to the repository, it will bring up your default text editor and ask for a commit message, this is what will be seen when you look at repository history.

I prefer to use the '-m' switch on my commit and then type the message inside the command meaning it skips the extra step of using a text editor.

```
git commit -m "MESSAGE GOES HERE"
```

### Showing the history of the repository

```
git log
```

This command will show you the commits to the project you are looking at, each commit has a unique name called the git hash these are not randomly generated they are generated using SHA-1. The output also shows you the author, commit message and date and time of the commit.

It is useful to see what the project looked like at each stage of the commits so if needed you can restore to a previous state.
