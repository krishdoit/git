# Configure git
SYSTEM: Git Installation directory, system level

$ git config --sytem user.name "balakrishna_s"

$ git config --system --list

GLOBAL: User home dir [.gitconfig] at user level

$ git config --global user.name "balakrishna_g" 

$ git config --global user.email balakrishna@xxx.com

$ git config --global --list

LOCAL: .git/config under local repository

$ git config  user.name "balakrishna_l"

$ git config --list  

Priority: local -> global -> system

# Commit ID

Git uses hash alg to create checksum/commitID to maintain the data integrity

# Initialize, Add Files to Stage and Commit

$ git init          // Initialize the local repository, creates .git in the current directory

$ git add <file(s)>      // Add files to Stage/Index, excluding .git. 

$ git add .         // Stage all the files

$ git commit -m "<commit_message>"    // commit the staged changes, creates branch master, HEAD points at master

$ git status        // Display the status of commits

$ gitk           // Visualize the commits


# Git log

$ git log           // Displays the commit history

$ git log --oneline             // Displays the commit history in simple format in the current branch

$ git log -n <number of commits history to display>     //  1/2/3..

$ git log --since=<YYYY-MM-DD>   // Displays commit history since and until the dates specified

$ git log --until=<YYYY-MM-DD> 

$ git log HEAD      // Display commits from the current HEAD - Tip of the current branch

$ git show          // Reports the changes by the recent commit(s)

$ git show HEAD~

$ git show HEAD~2

$ cat .git/HEAD         // Reference to where the HEAD points 


# Remote Repositories

$ git clone <repository_url>         // Clone remote repository onto local machine

$ git remote -v         // List remove repo connections

$ git remote add <alias> <url>       // Create new connection/link to a remote repository locally

$ git remote rm <alias>

$ git remote rename <old-name> <new-name>

$ git push -u <remote_alias> <branch>

# Branching and Merging

$ git branch        // List all the local branches

$ git branch -a        // List all the branches including local and remote

$ git branch <branch_name> // Create new branch

$ git checkout -b <branch>     // Switch to the branch specified

$ git diff <branch>      // Diff between branch specified and the CURRENT branch [ file differences]

$ git merge <branch>        // Merge <branch> into the CURRENT branch

$ git branch -D <branch>        // Delete a branch

$ git checkout <commit> <file>      // Check out to a previous version of a file

$ git checkout <commit>         // All files are updated to the specified commit

# Git workflow 
working directory -> staging area -> repository 
               git add ->     git commit ->

# Git Clean, Revert, Reset and Rebase

$ git clean <options>       // Remove untracked files from working tree

$ git clean -n      // Perform dry run of git clean

$ git clean -f <file_name>     // Remove untracked file_name from the current dir [before commit]

$ git clean -df         // Remove untracked files and dir from the current dir

$ git revert <commit_id>       // Create new commit that undoes all of the changes made in <commit_id>. The safe method

$ git diff <new_commit_id_after_revert> <previous_commit_before_commit_id>  // Should have no changes

$ git checkout <commit_id>      // to get the contents back, specific to the commit_id

$ git cherry-pick <commit_id>   //  Pick the changes specific to commit_id from different branch to the current branch 
                                // and merge in the current branch

$ git stash         // Stash/Save the current branch changes temporarily 

$ git stash list    // List stash list

$ git checkout <new_branch>     // Perform work on different branch and come back when the work is over there

$ git checkout <previous_branch>

$ git stash apply stash@{0}  // Previously stashed changes will be applied in the current branch

$ git reset <file_name> // Remove <file_name> from staging area but leave the working directory unchanged 
                        // [i.e, Move file from staging area to the working directory] 

$ git reset <file>        // Three types: soft, mixed, hard

$ git reset --soft <commit>     // Moves the HEAD

$ git reset --mixed <commit>     // Changes HEAD and Staging Index

$ git reset --hard <commit>        // Revert completely back to commit

$ git rebase -i <base>          // Rewrites commits as if they started in a different place, commits are lost

$ git rebase master <base>      // Changes in <base> but not in master are rewritten as changes to the new master

# Push, Clone, Fetch and Pull

$ git push -u <alias> <branch>      // User1 push changes from branch 1

$ git clone <url>             // User2 clone the repo from branch 2, Clone will create the local alias but pull doesn't

$ touch file1.txt; git add .; git commit -m "commit message"  // User2 have some changes

$ git remote add <alias> <branch>   // User2

$ git pull <alias> <branch>       // User2 will get the User1 changes

$ git fetch <alias> <branch> //  Download objects and refs from another repository, Fetch before work, before push and
                             // and often

$ git branch -a; git checkout remotes/origin/master // the contents would be available in remote branch but not local

$ git merge remotes/origin/master // Merge the changes using fetch + merge

$ git pull  //   git fetch + git merge 
            //   Means, get the latest updates by others to local copy of the repository from remote repository and 
            //   merge it


# Renaming and Deleting

$ git mv <filename>

$ git rm <file(s)>

# Git Ignore
Ignore the files that you would not want to commit

Create .gitignore under repository

Include the files/directory that you would like git to ignore.

