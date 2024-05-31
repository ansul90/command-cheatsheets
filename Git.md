Configurations
1. To set a git alias globally
git config --global alias.staash 'stash --all'

It executes git stash --all when you use git staash

2. Execute shell script on a command
git config --global alias.bb !better-branch.sh

It executes the better-branch.sh file when you use git bb 

3. Current user email which is used for commiting
git config user.email

4. To set user email at local level
git config --local user.email "<email>"

5. Resolve merge conflicts 1 time and next time Git will automatically do it for you
git config --global rerere.enabled true

6. Displays git branch in column format
git config --global column.ui auto

7. Sort the branches by last committed date
git config --global branch.sort -committerdate
-----------------------------------

1. View modification of each line in the file
git blame <filename>

To view modification for certain line range
git blame -L 10,15 <filename>

git blame -w -C -C -C
w: whitespace ignore
C: detect lines moved/copied in the same commit
C: or any commit that created the file
C: or any commit at all

Basically you get the origin/author of the code.

2. To see the history of certain line range
git log -L 10,15 <filename>

git log -S<string> -p
Performs a regex for the string whenever that's removed/updated

3. Log of your references
git reflog

4. Git diff
git diff --word-diff
Word based difference

5. When making a change to the last commit instead of doing a git push --force you should do
git push --force-with-lease
If you do a force push then you rewrite the history of remote with your local history. If somebody might have made changes it will be lost.
Usually force push is done to amend a commit
Doing force-with-lease will make sure you have the latest reference 

Making Git fast
1. Runs a couple of things in the background to make repo faster
git maintenance start
It does Prefetching (it won't fetch but will keep references to data), commit-graph (it builds for you indexes of commit)

2. If you want to the time taken to execute any git command append the command with time
time git status


Big repo
1. Filesystem monitor
If you run git status for big repo
    git config core.fsmonitor true - fsmonitor launches daemon that looks at file system and watches for inode events & updates cache in memory
    git config core.untrackedcache true

2. Sparse checkout
git sparse-checkout
Gets only the files required for you to work 


