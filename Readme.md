# GitHub Notes

## Setting up the environment:
    ```php
        // Configure user //

        git config --global user.name malickateeq
        git config --global user.email malickateeq@gmail.com
        // to check
        git config user.name or git config user.email
    
        // Initialize git in a project // move to project's roote folder
        git init
        // list tracked and untracked commits etc.
        git status
    ```
    
## Git States:
    // GIT files/code life cyle
    Modified -> Staging -> Committed
    1. Modified: You have a file you’ve made changes to but you have not yet committed (saved) to your local database.

    2. Staged: You have a modified file that you’ve “marked” as one you are planning to include in your next commit “snapshot”.

    3. Committed: You “officially” saved all your changes/files to your local database in git.
    
## GitHub Basics:

### Initializing Git:
    ```php
        // Initialize Git in newly created project by
        // Also will create a default master branch
        git init
    ```
### Staging Files
    - To stage a file to be included in your next commit snapshot, use "git add" command
    ```php
        // Add files for git staging for commit
        
        // Add all untracked files
        git add .
        
        // Add a specific file
        git add file.txt    // add file.txt

        // To remove file from staging
        git rm --cache file.text    // remove file.txt
        git rm --cache . -r    // remove all, -r to avoid recursive loop
    ```

### Saving A File
    - To save a file (and all changes) to your local git database, you will use the "git commit" command.
    ```php
        // Commit changes in local version
        git commit -m "I make xyz change in abc.."
    ```
### Pushing Up Your Local Repository To GitHub: Code Hosting Site
    ```php
        1. Link local repository with a live remotely hosted repository
            - "git remote add", then short name for reppo usually "origin", then URL to remote repository
            
            // We can set alias to git reppo url to avoid repeatition
            // origin is default used by many
            
            git remote add origin https://github.com/malickateeq/MyProject.git
        
        2. Push, publish or upload local repository to live
            - Arg1: shortname, Arg2: branch name, -u means set-upstream: set default branch only 1st time
            git push -u origin master
    ```

## Working With Branches:

### Creating a New Branch:
```php
    git branch <branch_name>

    // List all branches
    git branch
    
    // Switch to other branch
    git checkout <branch_name>
    
    // Create new branch and switch to it
    git branch -b <branch_name>

    // A Classification to Branches
    1.Feature Branch (new stuff your adding to your project)
    2. Bug Fix Branch (you introduced a change that broke some existing functionality and needs to get fixed)
    3. Hotfix Branch (a critical fix that needs to go in ASAP to get some functionality up and running again)
```

### Reverting (Undoing) Changes:
```php
    1. Finding Commit(Hash, ID) to Revert
        git log --oneline
    
    2. Use this ID or Hash to Revert
        git revert <ID,Hash>
    
    x. Revert HEAD or last commit
        git revert HEAD
```

### Merging Changes:
- Git offers the ability to “join” two or more branch histories together 
```php
    1. Checkout (switch over) to the master branch
        git checkout master
        
    2. Merge your feature branch into your master branch
        git merge <branch_name>
```

### Branch Conflicts:
- Simply put, there are changes in both branches that touch the same piece of code (file, etc.) and git doesn't know which change should be accepted over the other.
```php

```

### Reverting Changes:
```php

```

## Collaborating
- the ability for others to collaborate with you on your project.
```php

```

## Git General Commands:
    ```php
    - git status:
        Current status of the branch.
        
    - git log:
        When I want to see what I have in my local database and what git has recorded up this point
        
    - git remote -v
        Git setup for remotely repository fetch and push.
    - git branch 
        List all branches, shows current branch with an asteric *
    ```

## GitHub Undoing things
    ```php
        // To view Git Commit history/log (Commit_ID, Author, Date, Message)
        git log
        // To view in condensed form
        git log --oneline
    ```

### Checkout Commit (go back in time to view code)
    ```php
        // 1. First get ID of committ to modify etc.
        git log --oneline

        // 2. Get back in time by
        git checkout Commit_ID

        // 3. Now to get original/previous state just
        git checkout master

    ```
### Revert Commit (almost delete, but not we can get back)
    ```php
        // 1. First get ID of committ to modify etc.
        git log --oneline

        // 2. Get back in time by
        git revert Commit_ID

        // 3. You'll see a warning then press shift+: then enter wq to exit,

        // 4. It'll revert changes BUT add a new commit to git log

        // 3. Now to get original/previous state just
        git checkout master
    ```
### Reset Commit (permenantly go back in time)
    ```php
        // 1. First get ID of committ to modify etc.
        git log --oneline

        // 2. Get back in time by; The existing file changes will not effect
        git revert Commit_ID 

        // 2. Get back in time by; Hard revert
        git revert Commit_ID --hard

        // 3. Now to get original/previous state just
        It's too late to get back now.
    ```

### Creating & merging a branch:
    ```php
        // Creating a new branch 
        git branch branch_name

        // Show all branches
        git branch -a       // current branch will be highlighted green

        // Switch to new branch
        git checkout branch_name

        <-- Coding/changes in new branch, while stying in that branch --> 
        // make commits etc..

        // To delete a branch not merged yet just
        git branch -D branch_name

        // Merge branch with master
        git checkout master
        git merge branch_name
    ```
### Branch Conflicts:
    - when you change same things in master as well as in the branch, on merging them arises conflicts.
    ```php
        1. Remove committs, 
        2. git add.
        3. git commit       // with no message
        4. shift + :    type wq enter to exit now conflict branches merged.
    ```

## GitHub Remote Repositories:

### Create live reppo and clone in to local:
    ```php
        1. Initialize with Readme.md
        2. Click "Clone or Download" button and copy url
        3. Now to clone:
            git clone https://github.com/malickateeq/GitHub-Notes.git
        
        4. Add alias for future pushes:
            git add remote -v   // It has already setup push/fetch aliases on cloning
        
        5. Then
        git push origin master  // with branch name
        
    ```

## Collaborating on Github:

    ```php
        1. Clone project from live reppo as described above.
        2. Pull any new changes from master if any. GET UPDATES
            git pull origin master  (get from live and merge it to local master(current branch))

        3. Create a new branch locally & make some changes therein
            DON'T: merge changes with the master branch locally, can mess up things on live reppo
            Better: PUSH the branch to live reppo for review to others.

            git push origin newly_created_branch_name
        
        4. We can review "Compare & Pull" on live reppo website: To merge and > delete the branch
        
    ```
## Working on other's accounts code
    ```php
        1. Git to GitHub and open the public url to theire code
        2. click "Fork" to make a copy to your account
        3. Clone tha copy.
        4. Do some work and push changes to your copy ~~~~

        5. Bow contribute.. by;
            click "Create Pull Request" to your copy and your request is submittd to original author.
        6. The original branch reppo will login and review pull request and approve/disapprove changes. :)   
    ```
## CRLF and LF Issue:
```php
    Windows: Carriage Return (CR) and a Line Feed (LF) thus (CRLF)
    UNIX: Line Feed (LF)
    
    1. For single developer on windows, turn off the warning:
        git config core.autocrlf true
    2. For multiple developers > One on Windows platform
        git config --global core.autocrlf true
    3. For multiple developers > One on UNIX platform
        git config --global core.autocrlf input
        
    4. For Windows Only > Turn off this functionality
        git config --global core.autocrlf false
        
     For more details: https://stackoverflow.com/questions/5834014/lf-will-be-replaced-by-crlf-in-git-what-is-that-and-is-it-important
```
