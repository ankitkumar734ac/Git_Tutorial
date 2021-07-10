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
# Git Tag Command
The command we'll be using to interact with the repository's tags is the git tag command:
```sh
$ git tag -a v1.0
```
This will open your code editor and wait for you to supply a message for the tag. How about the message "Ready for content"?
`CAREFUL: In the command above (git tag -a v1.0) the -a flag is used. This flag tells Git to create an annotated flag. If you don't provide the flag (i.e. git tag v1.0) then it'll create what's called a lightweight tag.`
Annotated tags are recommended because they include a lot of extra information such as:
+ the person who made the tag
+ the date the tag was made
+ a message for the tag
Because of this, you should always use annotated tags.
<b>Note</b> to close git editor After writing commit message, just press Esc Button and then write<b> :wq or :wq! </b>and then Enter to close the unix file.
# Verify Tag
 it will display all tags that are in the repository.
```sh
git tag
```
# Git Log's --decorate Flag
The --decorate flag will show us some details that are hidden from the default view.
```sh
git log --decorate
```
The Terminal application showing the output of the git log --decorate command. The log output now displays the newly created tag.
The tag information is at the very end of the first line:
`commit 6fa5f34790808d9f4dccd0fa8fdbc40760102d6e (HEAD -> master, tag: v1.0)`
Did you notice that, in addition to the tag information being displayed in the log, the --decorate also revealed HEAD -> master? That's information about a branch! We'll be looking at branches in Git, next.
# Deleting A Tag
What if you accidentally misspelled something in the tag's message, or mistyped the actual tag name (v0.1 instead of v1.0). How could you fix this? The easiest way is just to delete the tag and make a new one.

A Git tag can be deleted with the -d flag (for delete!) and the name of the tag:
```sh
 git tag -d v1.0
```
```sh
fit tag -delete v1.0
```
# Adding A Tag To A Past Commit
Running git tag -a v1.0 will tag the most recent commit. But what if you wanted to tag a commit that occurred farther back in the repo's history?

All you have to do is provide the SHA of the commit you want to tag!
```sh
git tag -a v1.0 a87984
```
(after popping open a code editor to let you supply the tag's message) this command will tag the commit with the SHA a87084 with the tag v1.0. Using this technique, you can tag any commit in the entire git repository! Pretty neat, right?...and it's just a simple addition to add the SHA of a commit to the Git tagging command you already know.
# The git branch command
The git branch command is used to interact with Git's branches:
```sh
git branch
```
It can be used to:
+ list all branch names in the repository
+ create new branches
+ delete branches
If we type out just git branch it will list out the branches in a repository:
# Create A Branch
To create a branch, all you have to do is use git branch and provide it the name of the branch you want it to create. So if you want a branch called "sidebar", you'd run this command:
```sh
git branch sidebar
```
# The git checkout Command
Remember that when a commit is made that it will be added to the current branch. So even though we created the new sidebar, no new commits will be added to it since we haven't switched to it, yet. If we made a commit right now, that commit would be added to the master branch, not the sidebar branch. We've already seen this in the demo, but to switch between branches, we need to use Git's checkout command.
```sh
 git checkout sidebar
 ```
 It's important to understand how this command works. Running this command will:
+ remove all files and directories from the Working Directory that Git is tracking
++ (files that Git tracks are stored in the repository, so nothing is lost)
+ go into the repository and pull out all of the files and directories of the commit that the branch points to
So this will remove all of the files that are referenced by commits in the master branch. It will replace them with the files that are referenced by the commits in the sidebar branch.
Let's use this new feature of the git checkout command to create our new footer branch and have this footer branch start at the same location as the master branch:
```sh
git checkout -b footer master
```
# Branches In The Log
The branch information in the command prompt is helpful, but the clearest way to see it is by looking at the output of git log. But just like we had to use the --decorate flag to display Git tags, we need it to display branches.
```sh
git log --oneline --decorate
```
## Note
```sh
git branch alt-sidebar-loc 42a69f
```
It creates a new branch called alt-sidebar-loc and has it pointing at the commit with the SHA 42a69f
# Delete A Branch
A branch is used to do development or make a fix to the project that won't affect the project (since the changes are made on a branch). Once you make the change on the branch, you can combine that branch into the master branch (this "combining of branches" is called "merging" and we'll look at it shortly).

Now after a branch's changes have been merged, you probably won't need the branch anymore. If you want to delete the branch, you'd use the -d flag. The command below includes the -d flag which tells Git to delete the provided branch (in this case, the "sidebar" branch).
```sh
git branch -d sidebar
```
One thing to note is that you can't delete a branch that you're currently on. So to delete the sidebar branch, you'd have to switch to either the master branch or create and switch to a new branch.
Deleting something can be quite nerve-wracking. Don't worry, though. Git won't let you delete a branch if it has commits on it that aren't on any other branch (meaning the commits are unique to the branch that's about to be deleted). If you created the sidebar branch, added commits to it, and then tried to delete it with the git branch -d sidebar, Git wouldn't let you delete the branch because you can't delete a branch that you're currently on. If you switched to the master branch and tried to delete the sidebar branch, Git also wouldn't let you do that because those new commits on the sidebar branch would be lost! To force deletion, you need to use a capital D flag - git branch -D sidebar.
# See All Branches At Once
We've made it to the end of all the changes we needed to make! Awesome job!
Now we have multiple sets of changes on three different branches. We can't see other branches in the git log output unless we switch to a branch. Wouldn't it be nice if we could see all branches at once in the git log output.
As you've hopefully learned by now, the git log command is pretty powerful and can show us this information. We'll use the new --graph and --all flags:
```sh
git log --oneline --decorate --graph --all
```
The --graph flag adds the bullets and lines to the leftmost part of the output. This shows the actual branching that's happening. The --all flag is what displays all of the branches in the repository.
Running this command will show all branches and commits in the repository: This shows all branches and therefore all commits in the repository.
# Merging.
Combining branches together is called merging.
Git can automatically merge the changes on different branches together. This branching and merging ability is what makes Git incredibly powerful! You can make small or extensive changes on branches, and then just use Git to combine those changes together.
the two main types of merges in Git, a <b>Regular merge and a Fast-forward merge</b>.
It's very important to know which branch you're on when you're about to merge branches together. Remember that making a merge makes a commit.
As of right now, we do not know how to undo changes. We'll go over it in the next lesson, but if you make a merge on the wrong branch, use this command to undo the merge:
```sh
git reset --hard HEAD^
```
(Make sure to include the ^ character! It's a known as a "Relative Commit Reference" and indicates "the parent commit". We'll look at Relative Commit References in the next lesson.)
## The Merge Command
The git merge command is used to combine Git branches:
```sh
git merge <name-of-branch-to-merge-in>
```
When a merge happens, Git will:
+ look at the branches that it's going to merge
+ look back along the branch's history to find a single commit that both branches have in their commit history
+ combine the lines of code that were changed on the separate branches together
+ makes a commit to record the merge
### Fast-forward Merge
When we merge, we're merging some other branch into the current (checked-out) branch. We're not merging two branches into a new branch. We're not merging the current branch into the other branch.
Now, since footer is directly ahead of master, this merge is one of the easiest merges to do. Merging footer into master will cause a Fast-forward merge. A Fast-forward merge will just move the currently checked out branch forward until it points to the same commit that the other branch (in this case, footer) is pointing to.
To merge in the footer branch, run:
```sh
git merge footer
```
now that you've merged the two branches together. the master branch and the footer branch point to the same commit
to show:
```sh
git log --oneline --graph  --decorate --all
```
### Perform A Regular Merge
So let's do the more common kind of merge where two divergent branches are combined. You'll be surprised that to merge in a divergent branch like sidebar is actually no different!
To merge in the sidebar branch, make sure you're on the master branch and run:
```sh
git merge sidebar
```
Because this combines two divergent branches, a commit is going to be made. And when a commit is made, a commit message needs to be supplied. Since this is a merge commit a default message is already supplied. You can change the message if you want, but it's common practice to use the default merge commit message. So when your code editor opens with the message, just close it again and accept that commit message.
<b>Question</b>
Let's say a repository has 4 branches in it:
+ master
+ allisons-mobile-footer-fix
+ nav-updates
+ jonathans-seo-changes
The changes on master and allisons-mobile-footer-fix need to be merged together. If HEAD points to allisons-mobile-footer-fix, which branch will move when the merge is performed?
<b>Ans:</b> allisons-mobile-footer-fix branch HEAD pointer is pointing at, that's the branch that will have the merge commit.
# What If A Merge Fails?
The merges we just did were able to merge successfully. Git is able to intelligently combine lots of work on different branches. However, there are times when it can't combine branches together. When a merge is performed and fails, that is called a merge conflict. We'll look at merge conflicts.
If a merge conflict does occur, Git will try to combine as much as it can, but then it will leave special markers (e.g. >>> and <<<) that tell you where you (yep, you the programmer!) needs to manually fix.
## What Causes A Merge Conflict
As you've learned, Git tracks lines in files. A merge conflict will happen when the exact same line(s) are changed in separate branches. For example, if you're on a alternate-sidebar-style branch and change the sidebar's heading to "About Me" but then on a different branch and change the sidebar's heading to "Information About Me", which heading should Git choose? You've changed the heading on both branches, so there's no way Git will know which one you actually want to keep. And it sure isn't going to just randomly pick for you!

Let's force a merge conflict so we can learn to resolve it. Trust me, it's simple once you get the hang of it! Remember that a merge conflict occurs when Git isn't sure which line(s) you want to use from the branches that are being merged. So we need to edit the same line on two different branches...and then try to merge them.
# Merge Conflict Output Explained
```sh
 git merge heading-update 
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```
Notice that right after the git merge heading-update command, it tries merging the file that was changed on both branches (index.html), but that there was a conflict. Also, notice that it tells you what happened - "Automatic merge failed; fix conflicts and then commit the result".

Merge Conflict Indicators Explanation
The editor has the following merge conflict indicators:
+ <<<<<<< HEAD everything below this line (until the next indicator) shows you what's on the current branch
+ ||||||| merged common ancestors everything below this line (until the next indicator) shows you what the original lines were
+ ======= is the end of the original lines, everything that follows (until the next indicator) is what's on the branch that's being merged in
+ >>>>>>> heading-update is the ending indicator of what's on the branch that's being merged in (in this case, the heading-update branch)

# Resolving A Merge Conflict
Git is using the merge conflict indicators to show you what lines caused the merge conflict on the two different branches as well as what the original line used to have. So to resolve a merge conflict, you need to:
+ choose which line(s) to keep
+ remove all lines with indicators
# Commit Merge Conflict
Once you've removed all lines with merge conflict indicators and have selected what heading you want to use, just save the file, add it to the staging index, and commit it! Just like with a regular merge, this will pop open your code editor for you to supply a commit message. Just like before, it's common to use the provided merge commit message, so after the editor opens, just close it to use the provided commit message.

And that's it! Merge conflicts really aren't all that challenging once you understand what the merge conflict indicators are showing you

# Undoing Changes
<hr/>
# Modifying the last commit
<br/>
## Changing The Last Commit
You've already made plenty of commits with the git commit command. Now with the --amend flag, you can alter the most-recent commit.
```sh
 git commit --amend
```
If your Working Directory is clean (meaning there aren't any uncommitted changes in the repository), then running git commit --amend will let you provide a new commit message. Your code editor will open up and display the original commit message. Just fix a misspelling or completely reword it! Then save it and close the editor to lock in the new commit message.
## Add Forgotten Files To Commit
Alternatively, git commit --amend will let you include files (or changes to files) you might've forgotten to include. Let's say you've updated the color of all navigation links across your entire website. You committed that change and thought you were done. But then you discovered that a special nav link buried deep on a page doesn't have the new color. You could just make a new commit that updates the color for that one link, but that would have two back-to-back commits that do practically the exact same thing (change link colors).

Instead, you can amend the last commit (the one that updated the color of all of the other links) to include this forgotten one. To do get the forgotten link included, just:
+ edit the file(s)
+ save the file(s)
+ stage the file(s)
+ and run git commit --amend
So you'd make changes to the necessary CSS and/or HTML files to get the forgotten link styled correctly, then you'd save all of the files that were modified, then you'd use git add to stage all of the modified files (just as if you were going to make a new commit!), but then you'd run git commit --amend to update the most-recent commit instead of creating a new one.
# Reverting A Commit
When you tell Git to revert a specific commit, Git takes the changes that were made in commit and does the exact opposite of them. Let's break that down a bit. If a character is added in commit A, if Git reverts commit A, then Git will make a new commit where that character is deleted. It also works the other way where if a character/line is removed, then reverting that commit will add that content back!
## The git revert Command
Now that I've made a commit with some changes, I can revert it with the git revert command
```sh
git revert <SHA-of-commit-to-revert>
```
Since the SHA of the most-recent commit is db7e87a, to revert it: I'll just run git revert db7e87a (this will pop open my code editor to edit/accept the provided commit message)
# Resetting Commits
<b>Reset vs Revert</b>
At first glance, resetting might seem coincidentally close to reverting, but they are actually quite different. Reverting creates a new commit that reverts or undos a previous commit. Resetting, on the other hand, erases commits!
##  Resetting Is Dangerous ⚠️
You've got to be careful with Git's resetting capabilities. This is one of the few commands that lets you erase commits from the repository. If a commit is no longer in the repository, then its content is gone.

To alleviate the stress a bit, Git does keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the git reflog command. Check out these links for more info:
Relative Commit References
You already know that you can reference commits by their SHA, by tags, branches, and the special HEAD pointer. Sometimes that's not enough, though. There will be times when you'll want to reference a commit relative to another commit. For example, there will be times where you'll want to tell Git about the commit that's one before the current commit...or two before the current commit. There are special characters called "Ancestry References" that we can use to tell Git about these relative references. Those characters are:

+ ^ – indicates the parent commit
+ ~ – indicates the first parent commit
Here's how we can refer to previous commits:

+ the parent commit – the following indicate the parent commit of the current commit
++ HEAD^
++ HEAD~
++ HEAD~1
+ the grandparent commit – the following indicate the grandparent commit of the current commit
++ HEAD^^
++ HEAD~2
+ the great-grandparent commit – the following indicate the great-grandparent commit of the current commit
++ HEAD^^^
++ HEAD~3
The main difference between the ^ and the ~ is when a commit is created from a merge. A merge commit has two parents. With a merge commit, the ^ reference is used to indicate the first parent of the commit while ^2 indicates the second parent. The first parent is the branch you were on when you ran git merge while the second parent is the branch that was merged in.
# The git reset Command
The git reset command is used to reset (erase) commits:
```sh
git reset <reference-to-commit>
```
It can be used to:
+ move the HEAD and current branch pointer to the referenced commit
+ erase commits
+ move committed changes to the staging index
+ unstage committed changes
# Git Reset's Flags
The way that Git determines if it erases, stages previously committed changes, or unstages previously committed changes is by the flag that's used. The flags are:
--mixed
--soft
--hard
It's easier to understand how they work with a little animation.
<b>💡 Backup Branch 💡</b>
Remember that using the git reset command will erase commits from the current branch. So if you want to follow along with all the resetting stuff that's coming up, you'll need to create a branch on the current commit that you can use as a backup.

Before I do any resetting, I usually create a backup branch on the most-recent commit so that I can get back to the commits if I make a mistake:
```sh
git branch backup
```
Reset's --mixed Flag
Let's look at each one of these flags.
```sh
* 9ec05ca (HEAD -> master) Revert "Set page heading to "Quests & Crusades""
* db7e87a Set page heading to "Quests & Crusades"
* 796ddb0 Merge branch 'heading-update'
```
Using the sample repo above with HEAD pointing to master on commit 9ec05ca, running git reset --mixed HEAD^ will take the changes made in commit 9ec05ca and move them to the working directory.
![ud123-l6-git-revert-mixed](https://user-images.githubusercontent.com/71343747/125152301-652a0380-e169-11eb-92b0-62f1b9d83ee8.png)
💡 Back To Normal 💡
If you created the backup branch prior to resetting anything, then you can easily get back to having the master branch point to the same commit as the backup branch. You'll just need to:

remove the uncommitted changes from the working directory
merge backup into master (which will cause a Fast-forward merge and move master up to the same point as backup)
```sh
 git checkout -- index.html
 git merge backup
```
# Reset's --soft Flag
Let's use the same few commits and look at how the --soft flag works:
```sh
* 9ec05ca (HEAD -> master) Revert "Set page heading to "Quests & Crusades""
* db7e87a Set page heading to "Quests & Crusades"
* 796ddb0 Merge branch 'heading-update'
```
Running git reset --soft HEAD^ will take the changes made in commit 9ec05ca and move them directly to the Staging Index.
![ud123-l6-git-revert-soft](https://user-images.githubusercontent.com/71343747/125152361-b33f0700-e169-11eb-8c60-d76fa15270b8.png)

# Reset's --hard Flag
Last but not least, let's look at the --hard flag:
```sh
* 9ec05ca (HEAD -> master) Revert "Set page heading to "Quests & Crusades""
* db7e87a Set page heading to "Quests & Crusades"
* 796ddb0 Merge branch 'heading-update'
```
Running git reset --hard HEAD^ will take the changes made in commit 9ec05ca and erases them.
![ud123-l6-git-revert-hard](https://user-images.githubusercontent.com/71343747/125152387-dbc70100-e169-11eb-9be4-39f02fbb730a.png)
# Reset Recap
To recap, the git reset command is used erase commits:
```sh
git reset <reference-to-commit>
```
It can be used to:
+ move the HEAD and current branch pointer to the referenced commit
+ erase commits with the --hard flag
+ moves committed changes to the staging index with the --soft flag
+ unstages committed changes --mixed flag
Typically, ancestry references are used to indicate previous commits. The ancestry references are:
+ ^ – indicates the parent commit
+ ~ – indicates the first parent commit



--------------------------END------------------------------------





