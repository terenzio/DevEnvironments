Git Commands
==================

***

HEAD is not the latest revision, it's the current revision. Usually, it's the latest revision of the current branch, but it doesn't have to be.
master is a name commonly given to the main branch, but it could be called anything else (or there could be no main branch).
origin is a name commonly given to the main remote. remote is another repository that you can pull from and push to. Usually  it's on some server, like github.

***

Commit Messages:
------------
* Empty commit messages:  git commit --allow-empty

* One line per item since script will neither be able to pick up messages consequent lines nor break up multiple items within the same line when generating release notes

* FORMAT: Note:[TAG] <your message> (Note: and TAG are case-sensitive) where the options for TAG are:
    > [feature]: if you are adding a new feature

    > [bugfix]: if you are fixing a bug, should include the JIRA/HICHUB ticket number

    > [config]: if you are adding/modifying variables in docker-compose.yml so we should notify QA/OPS to get the latest copy.

* Be concise on release note items since they are not for payment developers. They should only know the changes with respect to functionalities but not implementation details

* Try not to number release note items since they will be collaborated with items from other commits so the numbering will be off.

* DONT: Note:[feature] 1. add a new feature (remove 1. since there will be multiple 1., 2., ... from multiple commits)

* Merge Assignees:
@Yuan-Chen @Ivan_Lo @Kang_Kuo @Kbear_Lin @Terence_Liu @joseph_chuang



***

Git Alias
------------
*  git status = git s
*  git log --pretty=format:"%h %s" --graph = git l
*  git checkout master = git ckm
*  git show-branch = git br
*  To Configure: git config --global alias.s 'status'
*  http://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html

***

PUSH
------------
*  git status
*  git add * //or you specify the file name here
*  git commit -m "Commit message"
*  git push origin branch name

***

NEW BRANCH
------------

* Show remote local and tracking branches:
   > git branch -avv

* Show currrent local branch:
   > git show-branch

* Create New Branch:
   > git branch NewBranch

   > git checkout NewBranch (lets you navigate between the branches created by git branch)

   > git branch (should show all the local branches of your repo. The starred branch is your current branch)

   > git checkout master

***


 BRANCH
------------

Delete Local Branch:
>  git branch -d branchName

Delete Local remote-tracking Branch
> git branch -rd origin/branchName

Delete actual remote Branch
> git push origin --delete branchName

> http://stackoverflow.com/questions/2003505/how-to-delete-a-git-branch-both-locally-and-remotely

***

DELETE STASHES
------------


* git stash
> stores changes temporarily

* git stash apply
> reapply stored changes

*  git stash clear
 > Remove all the stashed states. Note that those states will then be subject to pruning, and may be impossible to recover (see Examples below for a possible strategy).

* drop [-q|--quiet] [<stash>]
> Remove a single stashed state from the stash list. When no <stash> is given, it removes the latest one. i.e. stash@{0}, otherwise <stash> must be a valid stash log reference of the form stash@{<revision>}.



MERGE
------------
*  git branchr
*  git merge NewBranch  //Merge the specified branch into the current branch.
*  git show-branch

***

GIT FETCH and PULL
------------
On the master branch:
*  git pull origin
then checkout to own branch to merge master

***

GIT REBASE
------------
*  To link back to the newest branch or split when the master has evolved after receiving newer pushes.

* 0) Git PULL Origin FIRST!

* 1) first make sure your HEAD is at the newest commit
> git reset --hard {latest commit ID of the new feature branch that you want to rebase - the commit that you were just on}

* 2) then rebase
>  git rebase --onto {target branch ID - the latest MASTER CommitID} {current commit ROOT ID / the origin branching off point /  not the latest commit like the previous step}

* 3) then delete the old feature branch
> git branch -D {branch name}

* 4) then rename the rebased master branch to the old deleted feature name
> git branch -m {feature branch name}
* Rename Tips:
> git branch -m <oldname> <newname>
* If you want to rename the current branch, you can do:
 > git branch -m <newname>

* 5) then push the new feature branch
> git push origin {NOTICE!! feature branch name not master}

***

GIT SQUASH
------------
FORMAT:
* git rebase -i {insert your target branch}~{number of previous commits that you desire}

EXAMPLE:
* git rebase -i origin/master~6

This will bring up your text editor (-i is for "interactive") with a file that looks like this:
* pick 16b5fcc Code in, tests not passing
* pick c964dea Getting closer
* pick 06cf8ee Something changed
* pick 396b4a3 Tests pass
* pick 9be7fdb Better comments
* pick 7dba9cb All done

Change all the pick to squash except the first one:
* pick 16b5fcc Code in, tests not passing
* squash c964dea Getting closer
* squash 06cf8ee Something changed
* squash 396b4a3 Tests pass
* squash 9be7fdb Better comments
* squash 7dba9cb All done

AFTER SQUASH USE THIS TO PUSH:
* git push origin [branch-name] -f

***

DELETE GIT COMMAND
------------
https://stackoverflow.com/questions/1338728/delete-commits-from-a-branch-in-git

CLONE EXISITING REPO
------------
*  git clone ssh:XXXX

***

GIT TAGGING
------------

In Master Branch:
> git tag -a {tag name = build number} {commit id}
>
> git push origin {tag name}

***
VIEW COMMITS
------------
Version 1: All Network:
        >git log --all --graph --color --decorate --oneline
Version 2: Specific File
        >git log --all --graph --color --decorate --oneline <path/filename>
Others:
        >git log --pretty=format:"%h %s" --graph
        >git log --graph

***
