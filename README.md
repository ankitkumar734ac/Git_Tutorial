# Git_Tutorial_By_ME
# What is Git
 Git is a version control system.
# First Time Git Configuration
Before you can start using Git, you need to configure it. Run each of the following lines on the command line to make sure everything is set up.
```sh
# sets up Git with your name
git config --global user.name "<Your-Full-Name>"

# sets up Git with your email
git config --global user.email "<your-email-address>"

# makes sure that Git output is colored
git config --global color.ui auto

# displays the original state in a conflict
git config --global merge.conflictstyle diff3

git config --list
```
# Required Commands
```sh
Heads up! We'll be using the following terminal commands in this lesson:
ls - used to list files and directories
mkdir - used to create a new directory
cd - used to change directories
rm - used to remove files and directories
If you're not sure how to use them, check out our course Shell Workshop!
We'll also be using the idea of the current working directory, the directory that your shell is "looking at" right now. Using cd changes your working directory, and using ls (by itself) lists the files in the working directory. If you lose track of what your shell's working directory is, you can print its name with the pwd command (which stands for "print working directory").
```
# Git Init Command
Before you can make commits or do anything else with a git repository, the repository needs to actually exist. To create a new repository with Git, we'll use the git init command.

The init subcommand is short for "initialize", which is helpful because it's the command that will do all of the initial setup of a repository.
 Running the git init command sets up all of the necessary files and directories that Git will use to keep track of everything. All of these files are stored in a directory called .git (notice the . at the beginning - that means it'll be a hidden directory on Mac/Linux). This .git directory is the "repo"! This is where git records all of the commits and keeps track of everything!
# .Git Directory Contents
We're about to take a look at the .git directory...it's not vital for this course, though, so don't worry about memorizing anything, it's here if you want to dig a little deeper into how Git works under the hood.
Here's a brief synopsis on each of the items in the .git directory:
<b>config file </b>- where all project specific configuration settings are stored.
From the Git Book:
Git looks for configuration values in the configuration file in the Git directory (.git/config) of whatever repository you’re currently using. These values are specific to that single repository.
For example, let's say you set that the global configuration for Git uses your personal email address. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.
<b>description file </b>- this file is only used by the GitWeb program, so we can ignore it
 <b>hooks directory</b> - this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events
 <b>info directory </b>- contains the global excludes file
 <b>objects directory</b> - this directory will store all of the commits we make
 <b>refs directory </b>- this directory holds pointers to commits (basically the "branches" and "tags")

# Git Clone Command
```sh
git clone https://github.com/udacity/course-git-blog-project
```
 The command should clone the blog project repo and store it in a directory named blog-project.
 ```sh
 git clone https://github.com/udacity/course-git-blog-project blog-project
 ```
 # git status command!
 ```sh
 git status
 ```
 The git status is our key to the mind of Git. It will tell us what Git is thinking and the state of our repository as Git sees it. When you're first starting out, you should be using the git status command all of the time! Seriously. You should get into the habit of running it after any other command. This will help you learn how Git works and it'll help you from making (possibly) incorrect assumptions about the state of your files/repository.

The output tells us two things:

+ On branch master – this tells us that Git is on the master branch. You've got a description of a branch on your terms sheet so this is the "master" branch (which is the default branch). We'll be looking more at branches in lesson 5
+ Your branch is up-to-date with 'origin/master'. – Because git clone was used to copy this repository from another computer, this is telling us if our project is in sync with the one we copied from. We won't be dealing with the project on the other computer, so this line can be ignored.
+ nothing to commit, working directory clean – this is saying that there are no pending changes.

# Git log command

