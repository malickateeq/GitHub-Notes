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

## Committing Changes
    ```php

        // GIT files/code life cyle
        Modified -> Staging -> Committed

        // Add files for git staging for commit
        git add .           // means add all
        git add file.txt    // add file.txt

        // To remove file from staging
        git rm --cache file.text    // remove file.txt
        git rm --cache . -r    // remove all, -r to avoid recursive loop

        // Move files from staging to committed
        git commit -m "My custom message here"
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

## GitHub Branches

    - Master branch is the stable version of the code.
    - Feature branch for testing adding new things if satisfied merge with master.

### master branch:
    - Is the stable version of the code.

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

### Push local repository to remote(live) repo:
    ```php
        // make sure everything is comitted, nothing in staging.

        git push https://github.com/malickateeq/GitHub-Notes.git master     //(url you get after creating reppo) -> branch_name
        
        // We can set alias to above url to avoid repeatition
        git remote add origin https://github.com/malickateeq/GitHub-Notes.git        // origin is default used by many       
        // Then
        git push origin master  // with branch name
        
    ```
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
