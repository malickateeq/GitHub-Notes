# GitHub Notes

## Setting up the environment:
    ```git
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
    ```git

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
    ```git
        // To view Git Commit history/log (Commit_ID, Author, Date, Message)
        git log
        // To view in condensed form
        git log --oneline
    ```

### Checkout Commit (go back in time to view code)
    ```git
        // 1. First get ID of committ to modify etc.
        git log --oneline

        // 2. Get back in time by
        git checkout Commit_ID

        // 3. Now to get original/previous state just
        git checkout master

    ```
### Revert Commit (almost delete, but not we can get back)
    ```git
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
    ```git
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