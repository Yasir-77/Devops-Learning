## Chapter 1: Introduction to Git

### What is git?
Git is a distributed version control system that enables users to collaborate on projects, tracking changes in files and directories while providing a history of snapshots and the ability to manage different branches and merge code changes efficiently

### What is version control?
Git allows developers to track changes made to files over time, keeping a history of all modifications. This makes it easy to revert to previous versions if something goes wrong or to see how the code evolved.

### Centralised (SVN) vs Distributed VCS (Git)

| Centalised (SVN)  | Distributed (Git)  
|-------|------
| Single source of truth  | Full history on every machine |
| Requires network to commit | Work offline |
| Conflicts are common | Fast branching and merging |
| Server Outage = devs stuck | Resilient to outages | 
| Locks files during edits | Everyone cancommit locally | 

---

## Chapter 2: Git internals and Core Concepts

### Git Terminology & Key Concepts

- **Repository**: A Git project (tracked folder with a git directory)
- **Commit**: A snapshot of your files and metadata (author, timestamp, message, parent commit, etc.)
- **Branch**: A movable pointer to a specific commit (e.g., main, dev, feature/login)
- **Remote**: A reference to an external Git host (like GitHub, GitLab) usually named origin
- **Staging Area**: Also called the Index; a buffer between your working directory and the repo what you plan to commit
- **Blobs**: "binary large object" - stores the actual content of files (just the data, no filename/path)
- **Trees** : stores filenames, file paths, and pointers to blobs (files) and other trees (directories). Represents a directory snapshot
- **Refs (Reference)** : pointer to a commit: branches (refs/heads), tags (refs/tags), and special ones like HEAD
- **HEAD** : pointer to the current branch or commit you're working on
- **Index**: the actual file git/index, a binary file that holds the staging area info
- **Object Store**: git/objects/ — where Git stores all blobs, trees, and commits by SHA hash
- **Tag**: a ref to a specific commit, often used for marking releases

### The .git directory

The .git directory is the heart of every Git repository. It contains all the metadata and objects Git needs to manage the version history, branches, remotes, and more. When you run `git init`, Git creates this hidden .git folder inside your project directory.

#### What is inside the .git directory?

- .git/HEAD - Points to the current branch (e.g., refs/heads/main).
- .git/config - Project-specific Git configuration (user, remotes, etc.).
- .git/objects/	- Stores all the content (commits, trees, blobs) as SHA-1 hashes.
- .git/refs/ - Contains pointers to branches (heads/) and tags (tags/).
- .git/index - The staging area. Tracks what will be included in the next commit.

### Git common commands

| Commands  | Use 
|-------|------
| git init | initialises a new Git repo with git directory|
| git add | stage changes|
| git commit | Snapshot changes|
| git status | show staged/unstaged work|
| git log | show commit history|
| git diff | show what changed|
| git config | set user/email|
| git help <command> | built-in docs|
| git clone | copy a remote repo|
| git rm | remove files|
| git my | rename files|
| git restore | undo file changes|

### The Areas of Git

![image](https://github.com/user-attachments/assets/b7bfeb0a-6b00-4cef-91ec-aef7a72569ce)

- **1. Working Directory** - Where you actively edit files. It shows the current state of your project. - `git status` 
- **2. Staging Area (Index)** - Holds changes you intend to include in the next commit. - `git add` to stage, `git status` to view 
- **3. Git Repository (.git)** | The permanent, versioned history of your project. - `git commit` adds to this

---

## Chapter 3: History, Branching & Merging

### Viewing history

Commands Used for viewing history:

- `git log`: See commit history
- `git log --oneline--graph`:Visual summary
- `git show <commit>`: view a specific commit
- `git diff`: Compare unstaged vx last commit
- `git diff --staged`: comapare staged vs last commmit

Bonus:

- `git blame <file>`: show who last changed each line
- `git reflog`: View local HEAD history (even deleted branches)

### Git vs GitHub:

| Feature                | **Git**                                      | **GitHub**                                       |
| ---------------------- | -------------------------------------------- | ------------------------------------------------ |
| **Type**               | Version control system (VCS)                 | Online hosting service for Git repositories      |
| **What it does**       | Tracks changes in your local code            | Hosts repositories for collaboration and sharing |
| **Where it runs**      | On your **local computer** (CLI or GUI)      | On the **web(cloud)** (`github.com`)              |
| **Use case**           | Save versions, switch branches, undo changes | Collaborate, review code, manage pull requests   |
| **Requires Internet?** | ❌ No (works offline)                         | ✅ Yes (web-based)                                |
| **Interface**          | Command line / GUI apps (e.g., GitKraken)    | Web UI, GitHub Desktop, GitHub CLI               |
| **Created by**         | Linus Torvalds (2005)                        | Microsoft (owns GitHub since 2018)               |


### Branching

- `git branch`: List/create branches
- `git checkout -b<branch>`: Create & switch (older syntax)
- `git switch -c<branch>`: modern version to do same as above
- `git switch <branch>`: Sweitch branches safely
- `git branch -d<branch>`: delete branch

Note:

Git switch is newer and more beginner friendly. Works only with newer git versions.

Git branch only creates or lists, doesnt switch.

checkout still works but is multi-purpose and confusing.

### Merging in Git

When you’ve been working on a separate branch (feature-x) and you want to add your changes to the main project (main), you merge the feature branch into main.

![image](https://github.com/user-attachments/assets/8ba557ef-1c76-4009-ae63-d242c7c6383a)

### Visulaise Branches & Logs:

- `git log --oneline` - Compact commit view
- `git log --graph` - visual tree structure
- `git log --oneline --graph -all` - Comapct, visual and full view

These are great for debugging merges and tracking branches. Helps yosee whats really happening under the hood.

### Rebase vs Merge

| **Merge**                                | **Rebase**                                          |
| ---------------------------------------- | --------------------------------------------------- |
| Combine changes and preserve all history | Combine changes and rewrite history                 |
| Creates a new commit                     | No merge commits                                    |
| Good for team workflows                  | Ideal for cleanup before PR                         |
| Use wqhen working collaboratively        | Use when cleaning up your local history             |

---

## Advanced Git Usage:

### Git stash and pop

git stash is like putting your work into a temporary drawer so you can switch tasks without committing your changes. Later, you can take it out with git stash pop.

Git stash and pop commands:

- `git stash` - temporarily save uncommitted changes
- `git stash list` - view all stashes
- `git stash apply` - reapply latest stash (keeps stash)
- `git stash pop` - reapply and delete the stash

These commands are used when switching branches mid-task. Great for "I'm not ready to commit, but I need to move"

### Git reset, Revert and cherry pick:

#### git revert 

- Creates a new commit that undoes another
- safe for shared history
- Used in production

#### git reset 

- move branch pointer backword
- Soft = keep changes
- Mixed = unstage
- Hard = nuke everything.

#### git cherry-pick

- Apply a single commit from another branch
- Useful for hotfixes or targeted changes


### Forks and Pull requests (PRs)

- Fork = your own copy of someone elses repo (on Github)
- Clone the forked repo to your local machine
- Make changes -> push to your fork
- Open a Pull request (PR) to propose to your changes
- Used in open source and cross-team, workflows
- original rep owner can review, comment and merge.

![image](https://github.com/user-attachments/assets/a85ce718-c9ff-4712-b135-887cb68a3470)

### Collaborating practises

- Use branches to isolate work
- Push to remote and open pull requests
- Assign reviewers, use GitHubs UI for comments
- Resolve conflicts before merge
- Use issues, projects, Discussions to track work
- Keep commits focused and clean

### Typical Git workflow

![image](https://github.com/user-attachments/assets/d48f4284-310d-48f3-ad75-c75cbc27bce6)

### Trunk-Based-Development 

Trunk-Based Development (TBD) is a collaborative Git workflow where all developers work in a single main branch, called the trunk (usually main or master), and keep changes small and frequent.

- All devs commit to main or short-lived branches
- Heavy CI/testing gates
- Used in fast-moving orgs (Google/Facebook)

---

## Chapter 4: Git best practises

### Commit Hygiene & Best Practises

Write good commit messages - A clear commit message makes it easy to understand what changed and why — even months later.

Use squashing before merging PRs - Squashing lets you combine multiple small or messy commits into one clean, meaningful commit before merging a pull request.

One logical change per commit - Each commit should do one thing only — not multiple unrelated changes.

Avoid noisy merges or fixfixfinalfinal2 - Commits like fix, finalfinal, reallyfinal2 clutter the history and give no useful context.

### Pre-commit & Automation

1- Run linters/tests before comitting 9pre-commit, Husky, tflint/sec etc.)
2- Prevent broken code from entering the repo
3- Hook into CI pipelines for formatting, testing and scanning

### Common Mistakes in the Real World

![image](https://github.com/user-attachments/assets/6171b0fc-9366-4244-b12a-d841efcd8031)

### Git at scale

Absolutely! When using Git at scale, such as in large teams, monorepos, or enterprise environments, additional tools and practices are needed to manage complexity, performance, and automation.

- Monorepo strategies - Single Git repo for multiple projects
- Sparse checkout - Loads only part of the repository into your working directory — useful in huge monorepos.
- Large file support (Git LFS) - Git is not good at handling large binaries (e.g. videos, datasets, design files). Use Git LFS (Large File Storage) to manage them.
- Clean up legacy history (filter-branch, filter-repo) - Used to reduce repo size or remove sensitive files like secrets/passwords.
- Submodules vs subtrees in microservice repos - Used when splitting projects into microservices with their own Git repos.
- Selective CI builds (e.g. Turborepo, Nx, Bazel) - Run CI only on changed projects in a monorepo, instead of running everything every time.
- Commit linting + bots to enforce rules - Ensure commits follow standards using tools/bots
- GitOps-style deployments (e.g. ArgoCD, Flux) - Manage infrastructure and deployments using Git as the single source of truth.
- Server-side Git hooks (e.g. pre-commit.ci, Lefthook) - Run checks on the Git server or CI to enforce rules before allowing pushes or merges.

### Git Security & Secrets Hygiene

- Preveting secret leaks in commits
- Using git-secrets, trufflehog
- Cleaning secrets from history
- Auditing rep contributors + logs.

---  

## Chapter 5: Hands-on Git & Github

### Connecting to Github

- 1- git remote add origin <url>-link local --> GitHub
- 2- git push -u origin main - send your work to the cloud
- 3- git pull - bring down changes from Github
- 4- SSH vs HTTPS: ssh = Secure no password, HTTPS = easy but asks for credentials

### GitHub signup

1- Sign up to Github

2- On your Linux machine type `sudo apt-get install git`.

3- Create a Git Repository & link it locally, to congirgure Git and link it to any terminal type:

```
git config --global user.name "username"
```
```
git config --global user.email "email"
```
4- Create a SSH Key and connect to Github

On the command line type:
```
ssh-keygen -t ed25519 -C "user email" -f ~/.ssh/coderco_demo
```
This will create:

~/.ssh/coderco_demo → your private key (keep this safe!)

~/.ssh/coderco_demo.pub → your public key (add this to GitHub)

5- Copy SSH key into your GitHub account.
```
cat ~/.ssh/coderco_demo.pub
```
then copy the content.

Next you will go to your GitHub profile -> Settings -> SSH and GPG keys -> New SSH Key. Name the new SSH Key and paste the content you have copied from the terminal.


### Git Verify login
```
eval "$(ssh-agent -s)"
```
This launches the SSH authentication agent in the background, which helps manage your SSH keys during the session. You should see output like: Agent pid 12345. This means the agent is running.

```
ssh-add ~/.ssh/coderco_demo
```
This command adds your private key (coderco_demo) to the agent. If successful, it will respond: Identity added: /home/yourname/.ssh/coderco (your-email@example.com)
```
ssh -T git@github.com
```
This checks that: Git can use your SSH key. You're authenticated with GitHub


### New Repository

1- Create a new directory and enter the directory in the terminal :
```
mkdir git-lab
cd git-lab
```
2- Create a new Repository on GitHub named git-lab

3- Connect the command Line to the Git Hub repository:

- `echo "# git-labs" >> README.md` - This creates a file named README.md (if it doesn't exist), and adds the line:

- `git init` - Initializes a new Git repository in the current folder. It creates a hidden .git/ directory where Git tracks all changes.

- `git add README.md` - Stages the README.md file so it’s ready to be committed. Think of this as “preparing” the file to be saved to version history.

- `git commit -m "first commit"` - Creates your first commit, saving the staged README.md with the message: `first commit`. Commits are like checkpoints or snapshots of your code at a point in time.

- `git branch -M main` - Renames the current branch to main. -M forces the rename (even if main already exists). main is the standard default branch (instead of older master)

- `git remote add origin git@github.com:username/git-labs.git` - Links your local repo to a remote GitHub repo named origin. origin is the default nickname for your GitHub repo’s address.

- `git push -u origin main` - Pushes your local main branch to GitHub for the first time. -u sets up a tracking relationship, so next time you can just run: `git push`.


Now your local Git project is: Set up and committed, Linked to GitHub, Synced (pushed) to the remote repository

### First Repoitory Push

1 - `touch .gitignore` - Creates an empty .gitignore file.

2- `vi .gitignore` - Opens the file in the Vi editor so you can edit it. Inside, you'd typically add lines like: node_modules/, .env, .DS_Store

3- `git add .gitignore` - Stages the .gitignore file so it’s ready to be committed.

4- `git status` - Shows the current Git state — at this point it will show in red:

Changes to be committed: new file:   .gitignore
  
5- `git commit -m "add gitignore"` - Commits the staged .gitignore file with a clear message. This becomes a permanent part of your repo’s history.

6 - `git push` - Pushes the commit to your remote repository (on GitHub), assuming you already did: `git push -u origin main`
If the upstream was already set earlier, git push knows where to send it.

### Branching & Merging

1- Initialise the main branch -  created app.txt and committed it on the main branch.
```
echo "Hello from main" > app.txt
```
```
git status
```
```
git add app.txt
```
```
git commit -m "Inintial commit on main"
```
2- Create a feature branch and make changes - switched to a new branch feature-1 - overwrote `app.txt` with different conent and committed the change.
```
git checkout -b feature-1
```
```
echo "Feature branch change" > app.txt
```
```
git status
```
```
git add app.txt
```
```
git commit -m "update from feature-1"
```
3- Go back to main and make a conflicting change -  modified app.txt in main this change conflicts with the one from feature-1
```
git checkout main
```
```
echo "Main branch change" > app.txt
```
```
git add app.txt
```
```
git commit -m "conflicting update from main"
```
4- Attempt to merge feature-1 into main
```
git merge feature-1
```
Git detects a merge conflict in app.txt because both branches made incompatible changes to the same line(s). Merge is paused until the conflict is resolved

5. Resolve the conflict
```
echo -e "Hello from main\nMain branch change\nFeature branch change" > app.txt
```
```
git add app.txt
```
```
git commit -m "resolve merge conflict between main and feature-1 branch"
```

Manually edited the file to include both sets of changes. Then staged and committed the resolution.

6. Push the final result - Uploads the resolved and merged code to your remote (e.g., GitHub)
```
git push
```

7. Cleanup: delete the merged feature branch - Lists branches and deletes the now-merged feature-1 branch locally
```
git branch
git branch -d feature-1
```

Git WorkFlow

1- Create a new feature branch
```
git checkout -b feature/ass-about-page
```
Never work directly on main. Always make changes in a feature branch.

   
2- Make your changes
```
echo "This is your about page." > about.md
```
```
git add about.md
```
```
git commit -m "Add about page"
```

3- Push your branch to GitHub
```
git push --set-updtream origin feature/add-about-page
```
Uploads your feature branch so others can see it.

4- Open a Pull Request (PR)

- Go to GitHub → Your repository
- GitHub will show: “Compare & pull request”
- Click it, write a clear title and description of your change
- Assign reviewers (if needed)

This is where code review, discussion, CI tests, and approvals happen.

5 - Merge the Pull Request

- Click “Merge Pull Request”
- Optionally delete the branch in GitHub

6-  Pull changes into local main
```
git checkout main
```
```
git pull origin main
```
This syncs your local main branch with the latest merged changes.

### Undoing in Git

#### git restore

`git restore` helps undo changes in working directory and unstage files from staging area

Example:

1- Create and commit a file
```
echo "Original line" > undo.txt
git add undo.txt
git commit -m "test commit"
```
Created undo.txt with content "Original line". Staged and committed it to the repo

2. Made a bad change
```
echo "bad change" > undo.txt
```
overwrites the file with new content: "bad change"


3. Reverted the file with `git restore`
```
git restore undo.txt
```
This command restores the version of undo.txt from the last commit (HEAD), effectively undoing the bad local change

Now:
```
cat undo.txt
```
Will show: Original line - Because the file is now back to the last committed version.

#### git restore --staged

1- Made a new change
```
echo "Another bad line" > undo.txt
```
Overwrote undo.txt again with a new line

2. Staged the change
```
git add undo.txt
```
Now the modified version is in the staging area, ready to be committed

3. Checked status
```
git status
```
Output: Changes to be committed: modified: undo.txt

Confirms it's staged and ready to commit

4. unstaged it using:
```
git restore --staged undo.txt
```
This removes the file from the staging area but keeps your changes in the working directory.

5. Status now shows:

Changes not staged for commit: modified: undo.txt. Your change still exists

It's not staged anymore

#### git reset - git reset commands are powerful tools to undo commits, but each has a different level of impact — from gentle to destructive.

1 - `git reset --soft HEAD~11`

What it does:

- Removes the last commit
- Leaves changes in the staging area

When to use:

When you  want to rewrite my last commit message or squash commits.

Example:
```
git reset --soft HEAD~1
git commit -m "Better commit message"
```


2- `git reset --mixed HEAD~1`

What it does:

- Removes the last commit
- Moves changes back to the working directory
- Unstages them

When to use:

When you want to edit files before re-staging them, but don’t want to lose my work.

Example:
```
git reset --mixed HEAD~1
# edit files
git add .
git commit -m "Improved changes"
```

3- `git reset --hard HEAD~1`

What it does:

- Removes the last commit
- Deletes both staged and unstaged changes
- Working directory is reset to the state of HEAD~1

WARNING: Destructive! You lose uncommitted work.

When to use:

When made a mess and just want to go back cleanly — no changes, no trace.”

Example:
```
git reset --hard HEAD~1
```

#### git revert HEAD

`git revert HEAD` creates a new commit that undoes the changes introduced by the last commit (HEAD) — without modifying Git history.

When to use:

Use git revert when you want to safely undo a commit, especially on shared branches (like main), without breaking history for others.

Let’s say your last commit added this line: `Hello, production!`

You realize it was a mistake, so you run:
```
git revert HEAD
```

This:

- Launches an editor (e.g., Nano or Vim) to confirm the commit message.
- After saving, Git creates a new commit that removes Hello, production!.

#### git log --oneline

Is a shortened version of git log that shows your commit history in a compact, easy-to-read format.

What it shows:

Each line represents a single commit, like this:

3f3a2b1 Revert "accidental prod commit"
d9e1234 accidental prod commit
a1b2c3d Initial commit

Each entry includes:
- A short hash of the commit (3f3a2b1)
- The commit message

#### git reflog

It displays the history of where HEAD and branch tips have pointed, even if you've moved or deleted commits.

Example: 
```
e3a1b23 HEAD@{0}: revert: Revert "accidental prod commit"
f2b1a8d HEAD@{1}: commit: accidental prod commit
c4d3f55 HEAD@{2}: commit (initial): initial commit
```

Each entry shows:

- The commit hash
- A HEAD@{n} reference (position in the reflog)
- A short description of the action (e.g., commit, reset, checkout)

### git stash

git stash temporarily saves your uncommitted changes (both staged and unstaged) and reverts your working directory to a clean state, so you can:
- Switch branches
- Pull changes
- Work on something else without losing your current work.

Example: 

 1. Start a feature
```
echo "Incomplete work" > feature.txt
```
```
git add feature.txt
```
```
echo "more changes not staged" > feature.txt
```
Whats been done:

- Created feature.txt with some content
- Staged it
- Made further changes that are not yet staged

2. Stash the work-in-progress
```
git stash push -m "WIP: feature.txt changes"
```
This stashes:
- Staged changes (first version of feature.txt)
- Unstaged changes (second line added)
- All with a clear message for future reference

Your working directory is now clean.

Apply a hotfix (Worked on an alternative task)
```
echo "hotfix applied" > hotfix.txt
git add hotfix.txt
git commit -m "apply hotfix on main"
git push origin main
```
Created and committed a hotfix, then pushed it to the remote. ✅

4. View and restore your stashed changes

```
git stash list
```
```
git stash apply
```
git stash list shows something like:

stash@{0}: On main: WIP: feature.txt changes

git stash apply reapplies the stash but keeps it in the list, in case something goes wrong

5. Finalize and clean up
```
git stash pop
```
Pops the stash: reapplies it and removes it from the stash list

`git status` - You now see the restored changes in your working directory.

6. Commit and push the feature
```
git commit -m "push feature changes"
git push
```
Your feature changes are now committed and pushed.

7. Cleanup
```
git stash clear
```
Since everything went smoothly and nothing is left in stash, this clears all stash entries (if any remain).

### git rebase & squash

`git rebase` lets you move or replay your branch commits onto another base commit. It gives a linear, cleaner history.

Example How to use rebase and squash

Type the following:
```
git log --oneline
```
```
d7e1f00 Final styling
e3f2d12 Add footer
b4a3a9d Initial layout
a1b2c3d main branch commit
```
You want to squash the 3 feature commits into one.

Step 1: Interactive rebase

```
git rebase -i HEAD~3
```

Step 2: Change from this:
```
pick b4a3a9d Initial layout
pick e3f2d12 Add footer
pick d7e1f00 Final styling
```
To this:
```
pick b4a3a9d Initial layout
squash e3f2d12 Add footer
squash d7e1f00 Final styling
```
Git will then open a new editor for you to combine commit messages. A message like feat: Add all 3 lines to changes.txt. At the top of the editor.

Final result:
```
git log --oneline
```
```
f8e3c5a Initial layout with footer and styling
a1b2c3d main branch commit
```

Now your history is clean and easier to review.

### git cherry-pick

`git cherry-pick` applies the changes from an existing commit (or commits) onto your current branch, without merging the full branch.

When to Use It:

- You want a specific fix or feature, but not the whole branch
- Applying a hotfix from a dev branch directly onto main
- Pulling in individual commits from teammates without merging everything

Example:

1. Create a feature branch
```
git checkout -b feature-cherry
```
Created a new branch feature-cherry from main.

2. Add a hotfix
```
echo "hotfix config for prod" > hotfix.txt
git add hotfix.txt
git commit -m "hotfix: add prod config fix"
```
Created a new file (hotfix.txt) and committed it with a meaningful message.

3. Push the feature branch
```
git push --set-upstream origin feature-cherry
```
This pushes the branch to GitHub and sets the upstream so future git push/pull works without extra flags.

4. List commits
```
git log --oneline
```
Retrieved the commit hash (6b65efa in this case) of the hotfix commit.

5. Switch back to main
```
git checkout main
```

6. Cherry-pick the hotfix
```
git cherry-pick 6b65efa
```
Applied just that hotfix commit onto the main branch.

It creates a new commit on main with the same changes as the one in feature-cherry.

7. Push to remote
```
git push origin main
```
Pushed the cherry-picked change to GitHub’s main branch.

### The .gitignore

What is .gitignore?

- gitignore is a plain text file in a Git repository that tells Git which files or folders to ignore — meaning they won’t be tracked or committed.


Why use it?

- Avoid committing sensitive info (e.g., .env, API keys)

- Skip OS or editor clutter (e.g., .DS_Store, Thumbs.db, *.swp)

- Prevent checking in build artifacts (e.g., dist/, node_modules/, *.class)

- Keep your repository clean and focused on the actual source code

### git amend

`git commit --amend` allows you to edit the most recent commit. You can:

- Change the commit message
- Add or remove files in the commit
- Correct mistakes without creating a new commit

Example 1: Fix a Commit Message
```
git commit --amend
```
You'll be taken to your default editor (like Nano or Vim) to change the message.

Or do it inline:
```
git commit --amend -m "Corrected commit message"
```
Example 2: Add a Missed File
```
echo "Forgotten stuff" > forgot.txt
git add forgot.txt
git commit --amend --no-edit
```
--no-edit keeps the original commit message.

Important Notes
Amending rewrites history: it creates a new commit that replaces the old one. Only use --amend for commits not yet pushed to shared branches.

If you already pushed, force-push may be needed: `git push --force`





















