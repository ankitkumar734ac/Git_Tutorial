Git
====

Set your username global:->  git config --global user.name "FIRST_NAME LAST_NAME"

Set your email address global:->  git config --global user.email "MY_NAME@example.com"

Set your username:-> git config user.name "FIRST_NAME LAST_NAME"

Set your email address:-> git config user.email "MY_NAME@example.com"

Verify your configuration by displaying your configuration file:-> cat .git/config

You can view all of your settings and where they are coming from using:->  git config --list --show-origin

Disable use of the Git credential cache using:->  git config --global --unset credential.helper

To Add Origin:-> git remote add origin https://github.com/kumarankit00792/temp.git
To Remove Origin:- git remote remove origin


I Have two github account then how to use https for both:-
------------------------------------------------------------
    :-> git config --global credential.github.com.useHttpPath true
   You'll end up with a login for each repo in GitHub (not each username), but at least you won't have conflicts.
   If I use useHttpPath I'm being asked for a password each time.
The credential.useHttpPath is the "correct" way. Another option for GitHub and Bitbucket authorities is to prefix the URL with a username.

Example:
https://account1@github.com and https://account2@github.com should be seen as different accounts by the GCM. You will have to remember, however, to ensure that your repository remote's URL in the expected format: {protocol}://{username}@github.com/{repo}.

For example, when I use the "Clone with HTTPS" button on this repository, GitHub places https://github.com/Microsoft/Git-Credential-Manager-for-Windows.git on my clip board. If I want to use an alternate account, I would need to modify that to include my user alias ala https://gitstofj@github.com/Microsoft/Git-Credential-Manager-for-Windows.git.
      username@github.com/repo :-doesn't seem to work
      git config credential.github.com.username username :-doesn't seem to work
      git config credential.useHttpPath true :-does work, but it uses the entire repository as key, so it's annoying if you have multiple repositories under one account.

First time Push in Github:-> git push --set-upstream origin master
                         :-> git push -u origin master
               Note --set-upstream  == -u