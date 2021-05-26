# Git
Git is a distributed version control system. It makes working on projects in collabration with team members speedy and efficient. It allows you to create your own working copy of project on your local machine and allows you to make it remote so other team member can read and update it.

### Git Commands
| command |  Description|
|----------|-----------|
|git config --global user.email <"email_address">| configure user email --global(to all repositary) if not given then setting will be for current repository| 
|git config --global user.name <"user_name">|configure user name.|
| git init . | turn current directory into empty repository.|
|git add \<file_name/Dir_name> | add a file/dir to staging area/be tracked.|
|git add . | add all files that are not staged.|
|git commit -m \<message_for_commit> | record changes of file to local repository|
|git commit -a -m \<message_for_commit> | commit all the staged changes.| 
|git status | return current state of working tree.|
|git push \<remote_name> \<branch_name> | send local commits to remote repository.|
|git log | commit history of repository.|
|git remote add \<remote_name> \<remote_repo_URL> | add remote repositories.|
|git clone \<remote_repo_URL> | to create local working copy of existing remote repository.|
|git pull \<remote_name> \<branch_name> | to get latest version of remote repository of specified branch. If many people make changes the our push may get rejected the use this command|
|git branch <branch_name> | create new branch|
|git branch -D <branch_name> | delete a branch|
|git checkout <branch_name> | switch to specified branch.|
|git checkout -b <new_branch_name> | checkout to and create specified branch.|
|git switch <branch_name> | switch to specified branch.|
|git merge <branch_name> | merge changes from specified branch into current branch.|
|git show [commit_SHA] | metadata and content changes of specified commit.|
|git stash | to save work without commit|
|git stash pop | to pop the save work that was not committed|
|git reset <commit_id> --soft | git reset is used to move current head to commit specified,this command takes head back to stagging area |
|git reset <commit_id> --mix | takes head back to working area|
|git reset <commit_id> --hard |permanent remove from working area, changes made after this commit will be gon from working area |


**Good To**: use git reset commands only if you have not push the changes. Otherwise make new commit.