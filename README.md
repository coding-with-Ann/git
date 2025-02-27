# About-git

Git is a distributed version control system.
In Distributed version controlled system a copy of the repo is stored in the local machine and then it is stored in server.
In centralised version controlled system a local copy is not stored.

git config --global user.name "user name"
git config --global user.email "email Id"
    to set user name and email

git config --list
    we can use this to see what we set up for git config

So basically we have a credential helper in git
it stores these credentials like user name, email.

git clone <some link>
    clone -- to clone a remote repository to our local machine
    copy the https code link from github and use that link here

cd    == to change directory
cd .. == to come out of current working directory
pwd   == present working directory
mkdir == to create directory
ls    == list files
ls -a == shows the hidden files.

ctrl + c to stop a running command.

The folders in which we use git, there will always be a .git file in that folder
ls -a also shows .git file if its present in that folder.


git status == displays the status of code
    it shows if there are any commits left.

If we make changes to any file, we will see a "M" symbol next to that  
    modified file which means modified but not commited.

After modifying any file we have two steps to follow 
    one is add and the other is commit.

If we see any UNTRACKED FILE in git status, it means we have created
    a file which is not tracked by git (git doesnt know about it).
    we can see a "U" next to the untracked file


when we use git status we could see four types of status
1. untracked  == new files that are not tracked by git yet.
2. modified   == made some changes to file but not commited.
3. staged     == file is ready to be commited.
4. unmodified == nothing was changed in the file.


When we make changes to a file we have to ADD those changes
    when we ADD the changes, our file become STAGED.
    we can see "A" next to file name after staging. 

After ADD we COMMIT the changes, which means it is final
    At this point the file becomes unchanged.

So when we want to know the status of a file or repo 
    we can use "git status" command.


ADD and COMMIT
add -- adds the new or modified files in your working directory to the git staging area.
git add <file name>
we can see "A" next to the file after add

"git add ."  git add dot adds all the files we have in our working directory.

commit -- it is the record of change
git commit -m "some message"

Now if we check the status we will see nothing to commit.
Also we will see "Your branch is ahead of origin/main by 1 commit."
    it means we are 1 commit ahead in our local system as compared to github.

push -- to push local repo content to remote repo
git push origin main

By default the repos we have in git hub are called remote repos
the github default remote repository name is origin(we can change it if we want)
in that origin we are pushing on to a branch named main


CREATE REPO ON LOCAL MACHINE(init command)
If we want to create repo on local machine instead of creating it on github,
we can use "init" command.

init -- used to create a new git repo(makes a normal directory to local git repo).

git init == converts a normal directory to local git repo 
just navigate to the directory you want and use this command.

git remote add origin <link>
    we want to add a new remote repo with name origin then give the link of remote repo

git remote -v
    to see or verify the origin we can use this command

git branch 
    to see on which branch we are at.

git branch -M main
    to change the branch name to main

we can use "git push origin main" to push to remote repo

here we can aslo use a flag "-u" which is used to set upstream
    git push -u origin main
    -u is used to avoid writting origin main next time when we push changes to remote repo.
    if we work on same project for long time, when we push changes for first time use 
    "git push -u origin main", next time when we push changes to same repo we can use 
    "git push" to push to remote repo.
    This is just a short form to push when we work on same project for long time.


WorkFlow
    create github repo --> clone to local machine -->make changes --> add --> commit -->push






Git Branches

if we started a project, made two commits then if we want to add a new feature to this 
project and also continue the project then we can create a new brach and a team can work work on
that branch to make any no of commits to develop the feature. Parallely we can continue the project on 
main branch and make commits. Then we can make another commit to merge these two branches.

Here new brach team doesnt have to wait for main branch team until they finish the work, when they complte
the feature they can directly merge it with the main branch, this is the use of branches.

git branch                         ==     to see the branches 

git branch -M <new name>           ==     to change the branch name

git checkout <brach name>          ==     to navigate to another branch

git checkout -b <new branch name>  ==     new create a new branch

git branch -d <branch name>        ==     to delete a branch
to delete current branch, first we have to navigate to another branch,
then we we can delete it.

if we checkout to a branch with name feature 1 and then add some code to index.html or any file
and commit it then that change is present only in feature1 branch.
If we check out to branch main we cant see the change we made in index.html from the branch feature1.
We can see that code only if we navigate to feature1 branch.




Merge Branches(code)

Now we can merge branch with name feature1 and other branches(if there are any) with main branch.
we have 2 ways to merge code

1. using command line
    Before merging we can check the differences between two branches using the command

    git diff <branch name>      ==  to compare commits, branches, files and more
        lets say we are currently in feature1 branch, now to compare feature1 branch with main
        branch we can use the command "git diff main"

    git merge <branch name>     ==   to merge branches
        we are currently using feature1 branch, to merge feature1 branch with with main branch
        we can use the command "git merge main"


2. using PR (pull request)
    It lets you tell others about changes you've pushed to a branch in a repo on github.
    goto github and click on compare and pull request and complete process to merge.

    Now we have merged the branches in github but to see those changes in our local machine
    we have to use pull command

        git pull origin main  == used to fetch and download content from a remote repo and
         immediately update the local repo to match the content on remote repo.



Resolving Merge Conflicts

In branch main if a paragraph is written as 
<p>This is button</p>
In branch feature1 if we override the same para as
<p>This is dropdown</p>
Now if we merge these two branches we get error because these two represent the same paragraph
git doesn't understand which commit it should display after merge, this causes error.
To resolve this,  we can either click on accept current change or incoming change or accept both changes.
We can also do this manually by removing wierd lines, then keep the code we want.







Undo changes

case1: staged changes
    git reset <file name>
 If there are multiple staged files then use
    git reset

case2: commited changes(for one commit)
    git reset HEAD~1

    In git commits are stored in continuous fashion, the last commit default name HEAD,
    ~1 indicates that we want go to previous commit(one step back).
    commit1---- commit2---- commit3---- commit4(head)
    
    After reset head~1 commit3 becomes head

case3: commited changes(for many commits)
    If we want to go back to multiple commits we have to 
    use hash of the commit we want to go back to.
    git reset <commit hash value>

    After this we will see the "M" symbol next to file because we still have the
    changes in code that we made in last commit.

    Now to remove the changes from code we use
    git reset --hard <commit hash value>

To check the commits history use
    < git log >







Fork
Fork is a rough copy.
A fork is a new repo that has code and visibility settings exactly like original upstream repo.

We can use fork to take a copy of code and settings of a project on github, 
we can also make changes in it if allowed then we can make a pull request to
add the features that we created in the project.
Useful for opensource contribution.

Search for the open source project we want to copy then select fork to copy it.


