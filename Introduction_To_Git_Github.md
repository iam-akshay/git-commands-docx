# Introduction to Git and Github
---
### Goal of VCS
- A **version control system** allows us to keep track of when and who did what changes to our files. Those can be code, configuration, images, or whatever else we need to track.
### diff
- The **diff** tool shows all the differences between any type of file. By highlighting what’s changed, it helps us understand the changes and see how the files have been modified.
- **Command:**
    - `diff file_1.py file_2.py`
    - `diff -u file_1.py file_2.py` show the diff in another format (unified format)
    - `diff -u old_file.py new_file.py > change.diff` Create the diff file 

### Apply changes (patch)
- While diff is the command that generates the difference between two files, **patch** is the command that applies those differences to the original file.
- **Command:**
    - `patch  file_1.py < file_1_changes.diff` To automatically apply changes to a file, we need to run the patch command on the file that we want to modify with the diff file as input.

### Basic configuration
- `git config --global user.email "email@example.com"` Setting commit email address
- `git config --global user.name "My Name"` Setting commit username
- ***Note: `--global` used for global configuartion***

### Init, add, status, commit
- `git init` Initialize the empty git repo. (.git): The **git directory** acts as a database for all the changes tracked in Git and the **working tree** acts as a sandbox where we can edit the current versions of the files.
- `git add filename, ...` or `git add .` add the file in staging area: The staging area which is also known as the index is a file maintained by Git that contains all of the information about what files and changes are going to go into your next command.
- `git add -p` it will show the file changed and ask for staging confirmation
- `git status` is used to show that the file is staged or not, it shows the tracked and untracked file
- `git commit -m "commit message"` It create the new snapshot in the git repo.
- `git commit -a -m "commit message"` It will stage and commit the changes and it will not work for new files.
- `git commit --amend` Override the last commit

### Log, show
- `git log` is use to see the commit history
- `git log --oneline --graph`
- `git log -p` It will display commit logs with content changed
- `git show <commit_id>` It will display the detail about particular commit
- `git log --stat` display basic stat about commit

### git diff
- `git diff` It will show the changes made in file which is modified **(unstaged)**
- `git diff --staged` show the changes of staged file
### git rm, mv
- `git rm <file_name>` it will remove file and staged the file
- `git mv <old_name> <new_name>` it will rename the file and staged the file
### .gitignore
- The **gitignore** file is a text file that tells Git which files or folders to ignore in a project.

### Undoing changes before commit
- `git checkout <file_name>` revert the changes made before commit
- `git reset` or `git reset HEAD <file_name>` revert the file back to unstaged if staged

### Rollback (revert)
- `git revert HEAD` **git revert**, a new commit is created with inverse changes. This cancels previous changes instead of making it as though the original commit never happened.

### Branch
- By creating a new branch, we can experiment without breaking what already works.
- `git branch` List all branch
- `git branch <branch_name>` Create new branch
- `git checkout <branch_name>` Move to branch
- `git checkout -b <branch_name>` Creates a new branch and switches to it
- `git branch -d` Delete the branch
- `git branch -D` Forcefully delete the branch
- `git branch -r` Lists the remote branches
### Merge branch
- **Merging** combines branched data and history together.
- Git throwing a **merge conflict error** in cases of overlap on same line 
- Git uses two different **algorithms** to perform a merge, **fast-forward** and **three-way** merge.
- `git merge <feature_branch>` If we want to **merge feature branch** in **master branch** then move to master branch and use the command
- `git merge --abort` it will escape the merge and revert that

### Clone
- `git clone <git-web-url>` is use to create the local copy of the remote repo
### Push
- `git push` command gathers all the snapshot and sends them to the remote repo.
- `git push -u origin <new_branch_name>` -u flag is similar to --set--upstream, is use to create branch upstream
- `git push --delete origin <branch_name>` Delete the remote branch

### Pull
- `git pull` is used to fetch the newest updates from a remote repo.

### Fetch
- `git fetch` is use to sync the repo, it downloads the remote changes to local
- **NOTE: `git fetch fetches remote updates but doesn't merge; git pull fetches remote updates and merges.`**
### Avoid entering credentials
- As we push or clone we need to enter username and password both. So we can avoid this things with: 
    -  **SSH Key**
    -  **Credential helper**: `git config --global credential.helper cache` used to enable, after that, they'll be **cached for 15 minutes**.

### Git remote
- `git remote -v` to see the remote configuration. With this we can see the url associated with the origin remote.
- `git remote show origin` display more details about remote (**origin is the default name of remote**)

### Git Stash
- `git stash` to store uncommit changes for future use.
- `git stash list` to see the list of uncommit changes.
- `git stash save "message"` to save stash with a message.
- `git stash pop stash@{stash index number}` to remove the stash from stash list.
- `git stash show` to show the difference.
- `git stash apply stash@{stash index number}` to apply the stash.

### Rebase
- `git rebase <branch_name>` Move the current branch on top of the <specified_branch_name> branch
- Rebasing instead of merging rewrites history and maintains linearity, making for cleaner code.

### Squash
- `git rebase -i <branch_name>`
- **Squashing a commit** means, from an idiomatic point of view, to move the changes introduced in said commit into its parent so that you end up with one commit instead of two (or more). If you repeat this process multiple times, you can reduce n commit to a single one.

---
