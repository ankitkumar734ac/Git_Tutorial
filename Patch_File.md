# What is a patch file
● You should know by now that git is a way for developers to manage code in a project especially if there’s other developers collaborating in that project too.
● A git patch file is just a file that you can apply to a repository to get the changes / modifications / additions another developer
did on his / her machine onto your local machine. This isn’t the only way to do that ofcourse but this is a viable method for a head/lead developer
to check your code first before merging it into the repository’s main/master branch
# How to make a patch file
● Fire up a terminal, enter the repository via the terminal you opened (via the cd <repo_name_here> aka change directory command) and do the following commands
(one line, one command )
```sh
git add -A
git config user.email "<your_email_address>"
git config user.name "<your_name>"
git commit -m 'Create Patch File'
git format-patch -1 HEAD
```
# How to make a patch file
The final command, i.e. git format-patch -1 HEAD, should produce the .patch file you’d want to submit to complete this module. It will be located in the directory where you executed the commannd

![Screenshot (793)](https://user-images.githubusercontent.com/71343747/126617250-f69b25c6-c9fb-416c-8888-cbc198045870.png)

That’s how it would look like if you executed the commands properly.
