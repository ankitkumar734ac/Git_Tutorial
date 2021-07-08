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
The git log command displays a record of the commits in a Git repository. By default, the git log command displays a commit hash, the commit message, and other commit metadata. You can filter the output of git log using various options
![Screenshot (608)](https://user-images.githubusercontent.com/71343747/124383344-9f1e8400-dce9-11eb-950d-99e4c9c16d47.png)
### Navigating The Log
If you're not used to a pager on the command line, navigating in Less can be a bit odd. Here are some helpful keys:
```sh
to scroll <b>down</b>, press
<b>j</b> or <b>↓</b> to move down one line at a time
<b>d</b> to move by half the page screen
<b>f</b> to move by a whole page screen
```
```sh
to scroll <b>up</b>, press
<b>k</b> or <b>↑</b> to move _up_ one line at a time
<b>u</b> to move by half the page screen
<b>b</b> to move by a whole page screen
```
```sh
press <b>q</b> to quit out of the log (returns to the regular command prompt)
```
### Filter the log command output
+ This command returns a list of the three most recent commits made to a repository.
```sh
git log -n 3
```
+ You can also filter the commits returned by git log by the person who wrote or committed the changes. Suppose we want to see a list of commits pushed by “John Smith.” We can do so using these commands, The author flag limits the results to commits whose changes were made by John Smith. The committer flag limits the results to the commits that were actually committed by that individual.
```sh
git log --author="John Smith"
git log --committer="John smith"
```
+ you can filter the results of git log by date. To do so, you can use the—before and—after flags. These flags both accept a wide range of date formats, but the two most commonly used are relative references and full dates.
```sh
git log --after="2019-3-2"
git log --before="yesterday"
```
+ you may only want to see a list of commits that have affected a particular file. To do so, you can specify the file whose changes you want to see.
```sh
git log -- main.py
```
+ You can also search for commits that have removed or added a particular line of code.
```sh
git log -S"# Introduction"
```
+ This command returns a list of all commits between the b72beb5 and b53b22d commits.
```sh
git log b72beb5..b53b22d
```
+This command returns a list of all commits whose messages start with “feat:”.
```sh
git log --grep="feat:"
```
+ By default, the git log statement returns a full log entry for each commit made to a repository. You can retrieve a list of commit IDs and their associated commit messages using the –oneline flag.
```sh
git log --oneline
```
+ The –decorate flag allows you to see all the references (i.e. branches and tags) that point to a particular commit.
```sh
git log --decorate
```
+ The –stat flag allows you to display the number of lines of code added to and deleted from a repository in each commit.The plus signs (+) indicate insertions, and, if there were any, the minus signs (-) would indicate deletions.
```sh
git log --stat
```
+ If you want to see the exact changes made to a repository, you can use the -p flag.  The flag is --patch which can be shortened to just -p:
```sh
git log -p
```
+ The git shortlog command provides a summary of a git log
```sh
git shortlog
```
+  find the commit that has a SHA that starts with f9720a.
```sh
git log f9720a
```
+ find the commit that has the message <b>Set article timestamp color</b>. Which commit belongs to that SHA? Provide the first 7 characters of the SHA.
```sh
git log --oneline --grep='Set article timestamp color'
```
# git show
shows a specific commit is git show:
```sh
 git show fdf5493
 ```
 he git show command will show only one commit. So don't get alarmed when you can't find any other commits - it only shows one. The output of the git show command is exactly the same as the git log -p command. So by default, git show displays:
+ the commit
+ the author
+ the date
+ the commit message
+ the patch information
However, git show can be combined with most of the other flags we've looked at:
+ --stat - to show the how many files were changed and the number of lines that were added/removed
+ -p or --patch - this the default, but if --stat is used, the patch won't display, so pass -p to add it again
+ -w - to ignore changes to whitespace


# Git Add Command
The git add command is used to move files from the Working Directory to the Staging Index.
The git add command adds a file or folder to the staging area. Files in the staging area are those that you want to add to your next commit. Git add does not modify or otherwise affect your repository or files.
```sh
$ git add <file1> <file2> … <fileN>
```
This command:
+ takes a space-separated list of file names
+ alternatively, the period . can be used in place of a list of files to tell Git to add the current directory (and all nested files)
```sh
 git add css/app.css js/app.js
 ```
 ```sh
 git add .
```
# Git Commit Command
The git commit command takes files from the Staging Index and saves them in the repository.
The commit command will commit the changes and generate a commit-id. The commit command without any argument will open the default text editor and ask for the commit message. We can specify our commit message in this text editor.
```sh
$ git commit 
```
![git-commit2 (1)](https://user-images.githubusercontent.com/71343747/124842300-dff9ef80-dfac-11eb-90f2-89f2f6e32fac.png)
Press the Esc key and after that 'I' for insert mode. Type a commit message whatever you want. Press Esc after that ':wq' to save and exit from the editor. Hence, we have successfully made a commit.
<b>Note</b> lines that start with a # are comments and will not be recorded
![Screenshot (609)](https://user-images.githubusercontent.com/71343747/124842433-251e2180-dfad-11eb-99a3-724e2d1aff5e.png)
We can see in the above output that log option is displaying commit-id, author detail, date and time, and the commit message.
### Bypass The Editor With The -m Flag
```sh
git commit -m "Initial commit"
```
# git diff
the git diff command is used to see changes that have been made but haven't been committed, yet:
```sh
git diff
```
This command displays:
+ the files that have been modified
+ the location of the lines that have been added/removed
+ the actual changes that have been made
<b>Note</b>
It's the same output that we say with<b> git log -p </b>! Wanna know a secret? <b>git log -p</b> uses <b>git diff</b> under the hood. 
# Git Ignore
If you want to keep a file in your project's directory structure but make sure it isn't accidentally committed to the project, you can use the specially named file, .gitignore (note the dot at the front, it's important!). Add this file to your project in the same directory that the hidden .git directory is located. All you have to do is list the names of files that you want Git to ignore (not track) and it will ignore them.
.gitignore file is used to tell Git about the files that Git should not track. This file should be placed in the same directory that the .git directory is in.
Globbing lets you use special characters to match patterns/characters. In the .gitignore file, you can use the following:
+ blank lines can be used for spacing
+ # - marks line as a comment
+ * - matches 0 or more characters
+ ? - matches 1 character
+ [abc] - matches a, b, _or_ c
+ ** - matches nested directories - a/** /z matches
++ a/z
++ a/b/z
++ a/b/c/z
![Screenshot (610)](https://user-images.githubusercontent.com/71343747/124844311-9233b600-dfb1-11eb-9cab-c0161a78aa76.png)
we can create multiple .gitignore files for a project. But Git also allows us to create a universal .gitignore file that can be used for the whole project. This file is known as a global .gitignore file. To create a global .gitignore, run the below command on terminal:
```sh
git config --global core.excludesfile ~/.gitignore_global  
```




















